---
title: Security Homelab
---

# Security Learning Environment & Homelab

## Infrastructure Overview

My lab is running on Proxmox, a baremetal hypervisor. The hardware is an Intel Hades Canyon NUC. Born for gaming, now runs the lab.

### Tools & Technologies

- Virtualization: Proxmox VE
- Penetration Testing: Kali Linux, Burp Suite, Metasploit, Nmap
- Networking: Pi-hole, NGINX, Step-CA
- Containerization: Docker, Proxmox LXC

### Current Learning Focus

#### [Active Directory Lab](activedirectory.md)

- Purpose: Hands-on experience with vulnerable Windows domain controller and machines. Practicing various penetration techniques such as Kerberoasting, Pass-the-hash, and more.

#### [Web Application Security Lab](webapplab.md)

- OWASP Juice Shop with Burp Suite and FoxyProxy setup
- Key vulnerability focus areas:
  - SQL Injection and authentication attacks
  - Data exposure and XXE vulnerabilities
  - Access control and security misconfigurations
  - Cross-Site Scripting (XSS) techniques
- Emphasis on testing methodology and documentation
- Hands-on experience with baremetal hypervisor (Proxmox) and provisioning of interna/services

### Environment Overview

#### [Network Segmentation](network.md)

| Network     | Purpose          | Description                                       |
| ----------- | ---------------- | ------------------------------------------------- |
| Production  | Core Services    | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management       | Administrative access and management              |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources    |

---

_Return to [Home](../index.md)_
