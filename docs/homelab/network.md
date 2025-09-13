# General networking setup

## Overview

Separate the virtualized testing environment and use Kali as the pivot point.

!!! note "Overview"

    Unifi UI makes this straightforward and configurable.

## Network Topology

```mermaid
graph TD
    INTERNET((Internet)) --> ROUTER[UniFi Gateway]
    ROUTER --> FW{Firewall Rules}
    FW --> PROD[Production VLAN]
    FW --> ADMIN[Admin VLAN]
    FW --> LAB[Testing Lab VLAN]
    
    PROD --> CORE[Core Services]
    ADMIN --> MGMT[Management Interface]
    LAB --> ADLAB[AD Security Lab]
    LAB --> WEBLAB[Web Security Lab]
```

## Network Segmentation

| VLAN       | IP Range    | Purpose                      | Security Controls                                                                      |
| ---------- | ----------- | ---------------------------- | -------------------------------------------------------------------------------------- |
| Production | 10.0.1.0/24 | Core infrastructure services | • Strict firewall rules<br>• Limited external access<br>• Service isolation            |
| Admin      | 10.0.2.0/24 | Management access            | • Admin-only access<br>• Restricted to authorized devices<br>• Enhanced authentication |
| Lab        | 10.0.3.0/24 | Security testing environment | • Completely isolated<br>• No internet access<br>• Sandboxed environment               |

---

---

_Return to [Home](../index.md)_\
_Return to [Homelab](../homelab/index.md)_
