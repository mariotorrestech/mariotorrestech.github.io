---
title: Nginx Proxy Manager
---

# Nginx Proxy Manager (Reverse Proxy)

## Why a reverse proxy

Once [Pi-hole](pihole.md) was resolving `.lab` hostnames, services were reachable as `myhome.lab:8001` — better than raw IPs, but with two problems left: I had to remember a port for every service, and everything was still plain HTTP. I wanted them to behave like real websites — `https://myhome.lab`, no port, no warnings.

Nginx Proxy Manager solved both. Every `.lab` hostname points at NPM (see [Pi-hole](pihole.md)), and from there NPM:

- routes each hostname to the right backend IP and port, and
- terminates TLS with the [`*.lab` wildcard certificate](pki.md), so the port disappears and the connection is HTTPS.

`myhome.lab:8001` became `https://myhome.lab`, and the same pattern scaled to every service after it.

I stayed with NPM rather than reaching for Caddy or Traefik. Pi-hole was already handling DNS for the network, and NPM's web UI made per-host setup quick without hand-writing nginx config files — the two tools split DNS and ingress cleanly without overlapping.

## Architecture

```mermaid
graph LR
    BROWSER[Browser] -->|HTTPS| NPM[Nginx Proxy Manager<br/>TLS Termination]

    subgraph Backends
        DOCS[Documentation]
        GIT[Git Server]
        DNS[Pi-hole Admin]
        HYPERVISOR[Proxmox]
    end

    NPM -->|HTTP| DOCS
    NPM -->|HTTP| GIT
    NPM -->|HTTP| DNS
    NPM -->|HTTP| HYPERVISOR
```

## Proxy host configuration

Each service gets a proxy host in NPM with:

- **Domain**: `service.lab`
- **Forward target**: the backend IP and port, over plain HTTP
- **SSL**: the `*.lab` wildcard cert, with Force SSL, HSTS, and HTTP/2
- **Block Common Exploits** enabled
- **Websockets Support** where the service needs it

## Websockets: the Proxmox console

Most services proxy fine with the defaults. The one that didn't was the **Proxmox web UI** — its built-in shell and VM/console viewer run over websockets, and without the "Websockets Support" toggle the console loads but the terminal never connects. Enabling it fixed it, and it's now a default thing I check for any service with a live or interactive UI element.

---

_Return to [Homelab Overview](index.md)_
