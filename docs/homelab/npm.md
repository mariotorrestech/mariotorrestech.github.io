# Nginx Proxy Manager (Reverse Proxy)

!!! abstract "BLUF"
    **What I built:** A central reverse proxy (Nginx Proxy Manager) to front-end all homelab services over HTTPS.  
    **Why it mattered:** Consolidates ingress, simplifies routing by hostname, and terminates TLS in one place using certificates from my Step-CA.  
    **Outcome:** Clean `https://<service>.lab` access for all apps, with consistent security policies and a single pane for certificate and proxy management.

---

## Context & Goals

- Replace per-service ports (e.g., `:3000`, `:8080`) with stable HTTPS hostnames.
- Terminate TLS at the edge (NPM) using certs issued by my **Step-CA**.
- Keep everything internal (LAN/Tailscale), no WAN exposure.

---

## Design & Decisions

- **Ingress consolidation:** NPM terminates TLS and routes to backends on the internal network.
- **Certificates:** Issued from **Step-CA** (manual) → imported to NPM as custom certificates.
- **DNS:** Pi-hole provides A/CNAME records for `*.lab` pointing to the NPM address.
- **Security posture:** Only reachable on LAN/Tailscale; no WAN port-forwarding. IP allowlists can be applied in NPM if needed.

---

## Implementation

### Install

```bash
# Proxmox community script (LXC)
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/nginxproxymanager.sh)"
```

### Certificates (Step-CA → NPM)

Issue leaf certs per host with Step-CA (manual workflow):

```bash
# Example: issue cert for grafana.home.lab
step ca certificate "grafana.home.lab" grafana.crt grafana.key
```

Import into NPM:

- NPM UI → **SSL Certificates** → **Add** → **Custom**
- Paste/upload `grafana.crt` and `grafana.key`
- Save and name the certificate clearly (e.g., `grafana.home.lab (step-ca)`)

<!-- PATHS PLACEHOLDER -->
*(If storing certs on disk for NPM to mount/reference, document your paths here.)*

### Add Proxy Hosts

For each app:

1. **Hosts → Proxy Hosts → Add Proxy Host**
2. **Domain Names:** `grafana.home.lab`  
3. **Scheme:** `http` (or `https` if backend does TLS)  
4. **Forward Hostname / IP:** `10.10.10.<backend-ip>`  
5. **Forward Port:** `<backend-port>`  
6. **Block Common Exploits:** enabled  
7. **Websockets Support:** enable if the app needs it  
8. **SSL Tab:** Select your Step-CA certificate  
9. **Force SSL:** enabled (if appropriate)  
10. Save

Repeat for your core set:

- `npm.home.lab` → `10.10.10.165:81` (optional convenience)
- `proxmox.home.lab` → `10.10.10.<pve-ip>:8006`
- `grafana.home.lab` → `10.10.10.<ip>:3000`
- `pihole.home.lab` → `10.10.10.31:80`
- etc.

---

## Pitfalls & Fixes

- **Browser trust warnings**: root CA not installed on client.  
  *Fix:* Import Step-CA root into OS/browser trust stores.

- **502/504 after enabling Websockets app**: forgot to enable “Websockets Support”.  
  *Fix:* Toggle in the Proxy Host → Options.

---

## Reflection

- Skills demonstrated: reverse proxy design, TLS termination with internal CA, DNS mapping, and secure internal ingress patterns.
- Why it matters: mirrors a production pattern where edge proxies centralize security policy, certificate lifecycle, and routing.
- Next steps: script certificate rotation; add Access Lists (per-service auth); feed NPM logs into SIEM for visibility.
