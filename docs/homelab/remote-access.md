---
title: Remote Access
---

# Remote Access (Tailscale)

## Why Tailscale

Some services need to be reachable when I'm away from home — but I didn't want to expose anything to the public internet or open ports on the router. Tailscale builds a private mesh VPN (WireGuard underneath): every enrolled device gets a stable `100.x` address on my tailnet and can reach the others directly, with nothing listening on the WAN.

## How it works today

Remote access is opt-in per service. The services that need it run the Tailscale client directly and join the tailnet; from outside the house I reach them at their `100.x` tailnet address. No port forwarding, no public exposure — if a service isn't on the tailnet, it simply isn't reachable from outside the LAN.

## The hard part: Tailscale inside LXC containers

Most of my services are LXC containers, and Tailscale doesn't start in one out of the box. Unprivileged LXC containers don't get a `/dev/net/tun` device, and without it `tailscaled` has no TUN interface to build the tunnel on — `tailscale up` just fails. Working out *why* took some digging.

The fix is to enable the TUN device for the container on the Proxmox host **before** installing Tailscale:

```bash
# On the Proxmox host — enable TUN for the container
./tools/enable-tun.sh <VMID>

# Inside the container — install, enable, and authenticate
curl -fsSL https://tailscale.com/install.sh | sh
systemctl enable --now tailscaled
tailscale up
```

Then approve the device in the Tailscale admin console and record its `100.x` address. This is the remote-access step of the [service lifecycle](service-lifecycle.md).

## Current limitation and what's next

Today I connect to remote services by their `100.x` Tailscale address, not their `.lab` hostname — [Pi-hole](pihole.md)'s `.lab` resolution only works on the LAN, so the friendly names don't follow me onto the tailnet.

The planned improvement is to point Tailscale's DNS at Pi-hole (split DNS) so `service.lab` resolves over the VPN too, and remote access feels identical to being on the home network.

---

_Return to [Homelab Overview](index.md)_
