---
title: Security Homelab

---

# Security Learning Environment & Homelab

A learning-focused environment for developing cybersecurity and infrastructure skills

## Executive Summary

A purpose-built security lab environment where I develop and test cybersecurity skills, with current focus on penetration testing and security infrastructure. This lab serves as both my learning platform and a practical environment for real-world security scenarios.

## Current Learning Focus

- [PNPT certification](pnpt.md) preparation
- Active Directory attack methodologies
- Web application security testing
- Infrastructure security and system hardening

## Security Labs & Testing Environments

### [Active Directory Lab](../infrastructure/ActiveDirectoryLab.md)

- Purpose: Hands-on experience with vulnerable Windows domain controller and machines
- AD attack and defense scenarios in guideline with TCM's PNPT course/labs

### [Web Application Security Lab](../infrastructure/WebAppLab.md)

- OWASP Juice Shop with Burp Suite and FoxyProxy setup
- Key vulnerability focus areas:
  - SQL Injection and authentication attacks
  - Data exposure and XXE vulnerabilities
  - Access control and security misconfigurations
  - Cross-Site Scripting (XSS) techniques
- Emphasis on testing methodology and documentation

## Environment Overview

### [Network Segmentation](../infrastructure/network.md)

| Network     | Purpose          | Description                                       |
| ----------- | ---------------- | ------------------------------------------------- |
| Production  | Core Services    | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management       | Administrative access and management              |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources    |

## Infrastructure Overview

My lab is built on an Intel NUC8 Hades Canyon running Proxmox VE 8.2.2, providing a compact yet powerful platform for hosting both infrastructure services and security testing environments.

## Tools & Technologies

- Virtualization: Proxmox VE
- Penetration Testing: Kali Linux, Burp Suite, Metasploit, Nmap
- Network Security: Pi-hole, NGINX, Step-CA
- Containerization: Docker


---

*Return to [Home](../index.md)*
