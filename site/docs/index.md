---
title: Homelab
---

# Security Learning Environment & Homelab
A learning-focused environment for developing cybersecurity and infrastructure skills

[About Me / Professional Background](about.md)

## 📋 Executive Summary

## 🎯 Current Learning Focus
### Certification Preparation
- Active Directory attack methodologies
- Windows domain security testing
- Building practical testing experience in isolated lab environment
- Actively pursuing [PNPT certification](https://certifications.tcm-sec.com/pnpt/)

### Skill Development
- Security testing fundamentals
- Network security concepts

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


### Network Segmentation

| Network     | Purpose         | Description                                    |
| ----------- | -------------- | ---------------------------------------------- |
| Production  | Core Services  | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management     | Administrative access and management           |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources |

## 🖥️ Infrastructure Overview
### Core Platform
- **Primary Server**: Intel NUC8 Hades Canyon
  - 64GB RAM
  - Storage: 250GB SSD (OS) + 1TB SSD (VMs)
- **Hypervisor**: Proxmox VE 8.0
  - Snapshot capabilities
  - Virtual networking
  - Resource management

### Core Services

## 🛠️ Tools & Technologies
### Primary Tools

### Development Tools

---
*Last Updated: February 2025*  
[About Mario Torres](about.md)
=======
*Last Updated: November 2024*  
[About Mario Torres](about.md)
>>>>>>> parent of 814e61a (Info update):index.md
