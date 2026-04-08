# Service Lifecycle

Every service in the homelab follows a standardized onboarding and offboarding process. This keeps the environment consistent, documented, and auditable. No service runs without DNS, HTTPS, monitoring, and a documentation page.

---

## Onboarding

### 1. Provision

Create the container or VM on Proxmox. Record the VMID and IP immediately - these are referenced everywhere else.

```bash
# LXC container (using community scripts)
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/<script>.sh)"

# VM
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/vm/<script>.sh)"
```

Verify the service is running by accessing it directly via IP and port before moving on.

### 2. DNS

All `.lab` domains resolve through Pi-hole to the reverse proxy. Every new service gets a DNS entry pointing to the proxy's IP, not to the service directly.

```toml
# /etc/pihole/pihole.toml - add to dns.hosts
"<reverse-proxy-ip> servicename.lab",
```

```bash
# Restart DNS and verify resolution
systemctl restart pihole-FTL
nslookup servicename.lab
```

This means DNS is centrally managed. If the reverse proxy moves, only one IP changes - not every DNS record.

### 3. Reverse Proxy

Nginx Proxy Manager handles SSL termination for all services. Backend services run on plain HTTP internally - HTTPS is enforced at the proxy layer.

Each proxy host gets:

- Domain: `servicename.lab`
- Forward IP/port pointing to the backend service
- Wildcard SSL certificate (`*.lab`) via local CA
- Force SSL, HSTS, HTTP/2, Block Common Exploits enabled
- WebSocket support if the service uses real-time UI

The result: every service is accessed via `https://servicename.lab` with a trusted certificate, regardless of what the backend supports natively.

### 4. Monitoring

Every web-accessible service gets an Uptime Kuma monitor. If it goes down, I know about it before I notice.

- Type: HTTP(s)
- URL: `https://servicename.lab`
- Heartbeat: 60 seconds

### 5. Remote Access

If the service needs to be reachable outside the local network, it gets added to the VPN mesh. For LXC containers, this requires enabling the TUN device on the Proxmox host first.

```bash
# Enable TUN device for an LXC container
./tools/enable-tun.sh <VMID>

# Install and authenticate inside the container
curl -fsSL https://tailscale.com/install.sh | sh
systemctl enable --now tailscaled
tailscale up
```

Approve the device in the admin console and record the overlay IP.

### 6. Documentation

No service is "done" until it's documented. Every service gets:

- A dedicated page with a details table (VMID, type, hostname, IP, port, URL)
- Installation method and any special configuration
- Common commands for management and troubleshooting
- An entry in every inventory table across the docs site

The docs are built with MkDocs and deployed via rsync.

### 7. Verification

Final check before considering a service fully deployed:

- Service responds on direct IP:port
- DNS resolves `servicename.lab` to the reverse proxy
- `https://servicename.lab` loads with a valid certificate
- Uptime Kuma monitor shows UP
- Documentation page exists with complete details
- Service appears in all inventory tables

---

## Offboarding

Removing a service follows the reverse path. The goal is zero orphaned records - no stale DNS entries, no dead monitors, no documentation referencing something that doesn't exist.

### 1. Shutdown and Backup

Stop the service, export any data worth keeping, then stop the container or VM.

```bash
pct stop <VMID>   # LXC
qm stop <VMID>    # VM
```

### 2. Remove DNS, Proxy, and Monitoring

- Delete the DNS record from Pi-hole and restart the service
- Delete the proxy host from Nginx Proxy Manager
- Delete the monitor from Uptime Kuma
- Remove the device from the VPN admin console (if applicable)

### 3. Destroy

```bash
pct destroy <VMID>   # LXC
qm destroy <VMID>    # VM
```

### 4. Documentation Cleanup

Remove the service from every location it was added during onboarding: service page, nav, inventory tables, architecture diagram, cheat sheet, DNS reference. Deploy the updated docs.

### 5. Verification

- Container/VM no longer appears in `pct list` / `qm list`
- DNS no longer resolves the `.lab` domain
- No proxy host exists for the domain
- No monitoring entry exists
- No references remain in documentation

---

## Drift Audit

Infrastructure drifts. Services get added without full documentation, or a container gets destroyed without cleaning up its DNS record. Running a periodic drift audit catches these gaps.

### Process

Compare what's actually running against what's documented:

```bash
pct list   # Running LXC containers
qm list    # Running VMs
```

Every running VMID should have:

1. A row in all inventory tables
2. A dedicated documentation page
3. A DNS record (if web-accessible)
4. A reverse proxy host (if web-accessible)
5. An Uptime Kuma monitor (if web-accessible)

Anything that's running but undocumented is a gap. Anything that's documented but not running is stale. Both get fixed.
