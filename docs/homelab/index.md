---
title: Security Homelab
---

# Security Learning Environment & Homelab

## Infrastructure Overview

My lab is built on an Intel NUC8 Hades Canyon running Proxmox VE 8.2.2, providing a compact yet powerful platform for hosting both infrastructure services and security testing environments.

### Tools & Technologies

- Virtualization: Proxmox VE
- Penetration Testing: Kali Linux, Burp Suite, Metasploit, Nmap
- Network Security: Pi-hole, NGINX, Step-CA
- Containerization: Docker

### Current Learning Focus

- [CISSP certification](../certifications/cissp.md) domain topics to provide hands-on experience.
- [Active Directory](activedirectory.md) penetration techniques and methodologies
- [Web application security](webapplab.md) testing by way of OWASP Juice Shop
- Hands-on experience with baremetal hypervisor (Proxmox) and provisioning of interna/services

### Security Labs & Testing Environments

#### [Active Directory Lab](homelab/activedirectory.md)

- Purpose: Hands-on experience with vulnerable Windows domain controller and machines
- AD attack and defense scenarios in guideline with TCM's course/labs

#### [Web Application Security Lab](homelab/webapplab.md)

- OWASP Juice Shop with Burp Suite and FoxyProxy setup
- Key vulnerability focus areas:
  - SQL Injection and authentication attacks
  - Data exposure and XXE vulnerabilities
  - Access control and security misconfigurations
  - Cross-Site Scripting (XSS) techniques
- Emphasis on testing methodology and documentation

### Environment Overview

#### [Network Segmentation](../infrastructure/network.md)

| Network     | Purpose          | Description                                       |
| ----------- | ---------------- | ------------------------------------------------- |
| Production  | Core Services    | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management       | Administrative access and management              |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources    |

---

_Return to [Home](../index.md)_
