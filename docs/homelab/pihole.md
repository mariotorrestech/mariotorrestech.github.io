# Pi-hole (DNS & Ad Blocking)

!!! abstract "BLUF"
    **What I built:** A Pi-hole LXC container on Proxmox to provide DNS resolution and network-wide ad blocking.  
    **Why it mattered:** Centralized DNS lets me map `.lab` domains to Nginx Proxy Manager for clean hostnames, while also filtering ads and telemetry.  
    **Outcome:** Services are now accessible via simple hostnames (`proxmox.lab`, `npm.lab`, etc.) with HTTPS handled at NPM, and the entire LAN benefits from ad filtering.

---

## Context & Goals

- **Problem:** Internal services were only reachable by IP:port → messy and insecure.  
- **Goal:** Centralize DNS for homelab + LAN, provide hostname-based access, and block ads globally.  
- **Constraints:**  
  - Local-only `.lab` domain (no external resolution).  
  - DNS resolution must forward to NPM, not direct service IPs.  
  - Upstream DNS → Google (8.8.8.8) for non-local lookups.  

---

## Environment

**Proxmox LXC (Unprivileged)**

- Installed via community script:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/pihole.sh)"
```
---

## Design & Decisions

- **Local DNS:** Pi-hole resolves all `.lab` hostnames to the NPM container (`10.10.10.165`).  
- **Routing:** NPM then forwards requests to the correct backend service and terminates TLS.  
- **Upstream fallback:** Any non-local query resolves via Google DNS.  
- **Ad-blocking:** Gravity enabled by default with Pi-hole’s blocklists; no custom lists.  

---

## Implementation

### DNS Records

Examples of local DNS records:

- `proxmox.lab` → `10.10.10.165` (NPM forwards to PVE host)  
- `pi.lab` → `10.10.10.165` (NPM forwards to Pi-hole admin UI)  
- `npm.lab` → `10.10.10.165` (direct to NPM UI on :81)  
- `yt.lab` → `10.10.10.165` (NPM forwards to yt-dlp Material service)  

<!-- SCREENSHOT PLACEHOLDER -->
*(Insert Pi-hole Local DNS Records UI screenshot here.)*

### Clients

- Router/DHCP assigns `10.10.10.31` as DNS server to all LAN clients.  
- Homelab services explicitly pointed to Pi-hole for consistency.  

---

## Pitfalls & Fixes

- **Initial mistake:** Pointed hostnames directly to service IPs (e.g., `10.10.10.x:port`).  
  - **Fix:** Corrected records so all `.lab` domains point to NPM (`10.10.10.165`), which handles routing and SSL termination.  

---

## Reflection

- **Skills demonstrated:** DNS management, integration with reverse proxy, network-wide ad blocking.  
- **Next steps:**  
  - Document a standard naming convention for `.lab` records.  
  - Export DNS config for backups.  
  - Feed Pi-hole query logs into the SIEM/logging stack.  
