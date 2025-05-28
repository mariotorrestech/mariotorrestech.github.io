---
title: Infrastructure

---

# Infrastructure Overview

## Origins & Use Case

Originally built for multimedia services access (yt-dlp), evolved into a comprehensive security lab environment with core services:

- Pi-Hole (DNS and ad blocking)
- NGINX Forward Proxy (internal service access)
- Step-CA (internal PKI for SSL certificates)

## Hardware Details

- **System**: Intel NUC8 Hades Canyon
- **CPU**: Intel i7 with Radeon RX
- **RAM**: 64GB
- **Storage**: 250GB NVMe SSD (OS) + 1TB NVMe SSD (VMs)

## Network Configuration

Dual bridge configuration via Proxmox allows for easily configurable virtualized network hardware for my attack machine (Kali) and the vulnerable environment.:

=== "Attack domain"
    * Kali is the only machine with dual access and allows for attack/pivot in offensive scenarios and labs.
    * vmbr0 access for internet-connectivity
    * vmbr1 access for vulnerable network for AD lab and sensitive OWASP
  

=== "Vulnerable domain" 
     
    * Includes the virtualized [AD Lab](ActiveDirectoryLab.md)
    * vmbr1 access only (intranet-only)

## Lab Environments

- [Active Directory Lab](ActiveDirectoryLab.md)
- [Web Application Lab](WebAppLab.md)
- [Network Details](network.md)

![Intel NUC8](../assets/nuc8.jpg)


---

*Return to [Home](../index.md)*