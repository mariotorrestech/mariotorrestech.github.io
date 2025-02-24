---
title: Homelab
---

# Security Learning Environment & Homelab
A learning-focused environment for developing cybersecurity and infrastructure skills

[About Me / Professional Background](about.md)

## 📋 Executive Summary
A dedicated homelab environment built for hands-on learning in cybersecurity, with a current focus on [PNPT (Practical Network Penetration Tester) certification](https://certifications.tcm-sec.com/pnpt/). This environment serves as both a practical learning platform and a foundation for developing real-world security testing experience.

## 🎯 Current Learning Focus
### Certification Preparation
- Active Directory attack methodologies
- Windows domain security testing
- Building practical testing experience in isolated lab environment
- Actively pursuing [PNPT certification](https://certifications.tcm-sec.com/pnpt/)

### Skill Development
- Security testing fundamentals
- Network security concepts
- Infrastructure automation basics

## 🔬 Security Labs & Testing Environments

### Active Directory Lab
- Dedicated network segment for testing:
  - Windows domain environment for PNPT preparation
  - Kali Linux attack machine, Windows 11/Windows Server
  - Isolated from production services
  - AD attack and defense scenarios

### Web Application Security Lab
- OWASP Juice Shop with Burp Suite and FoxyProxy setup
- Key vulnerability focus:
  - SQL Injection and authentication attacks
  - Data exposure and XXE vulnerabilities
  - Access control and security misconfigurations
  - Cross-Site Scripting (XSS) techniques
- Emphasis on testing methodology and documentation

## 🛡️ Network Architecture


## 🏗️ Environment Overview
<img src="/images/homelab-diagram.svg" style="width: 500px; max-width: 100%;" alt="Homelab Infrastructure Diagram">

### Security Design
- Isolated internal network - no external exposure
- Network segmentation for service isolation
- Internal PKI using Step-CA signed certificates


### Network Segmentation

| Network     | Purpose         | Description                                    |
| ----------- | -------------- | ---------------------------------------------- |
| Production  | Core Services  | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management     | Administrative access and management           |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources |

## 🖥️ Infrastructure Overview
### Core Platform
- **Primary Server**: Intel NUC8 Hades Canyon
  - Intel i7-8709G with Radeon Graphics
  - 64GB RAM
  - Storage: 250GB SSD (OS) + 1TB SSD (VMs)
- **Hypervisor**: Proxmox VE 8.0
  - Snapshot capabilities
  - Virtual networking
  - Resource management

### Core Services
- Infrastructure:
  - Pi-hole DNS and ad blocking
  - Step-CA certificate authority
  - Nginx Proxy Manager
- Containerized Services:
  - Docker deployments
  - Container security practice

## 🛠️ Tools & Technologies
### Primary Tools
- Proxmox VE
- Docker
- Kali Linux
- Common security testing tools
- Network analysis tools

### Development Tools
- Bash scripting
- Infrastructure automation
- Service configuration

---
<<<<<<< HEAD:site/docs/index.md
*Last Updated: February 2025*  
[About Mario Torres](about.md)
=======
*Last Updated: November 2024*  
[About Mario Torres](about.md)
>>>>>>> parent of 814e61a (Info update):index.md
