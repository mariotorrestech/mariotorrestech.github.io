---
title: Homelab
---

# Security Learning Environment & Homelab
A learning-focused environment for developing cybersecurity and infrastructure skills

[About Me / Professional Background](about.md)

## 📋 Executive Summary
A purpose-built security lab environment where I develop and test cybersecurity skills, with current focus on penetration testing and security infrastructure. This lab serves as both my learning platform and a practical environment for real-world security scenarios.

## 🎯 Current Learning Focus
### Certification Preparation
- Active Directory attack methodologies
- Windows domain security testing
- Building practical testing experience in isolated lab environment
- Actively pursuing [PNPT certification](https://certifications.tcm-sec.com/pnpt/)

### Skill Development
- Security testing fundamentals
- Network security concepts
- Infrastructure security and system hardening 

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
- Strictly isolated internal network - no external exposure
- Defense-in-depth network segmentation for critical service protection
- Internal PKI using Step-CA for secure certificate management and authentication 


### Network Segmentation

| Network     | Purpose         | Description                                    |
| ----------- | -------------- | ---------------------------------------------- |
| Production  | Core Services  | Infrastructure services (Pi-hole, Step-CA, Nginx) |
| Admin       | Management     | Administrative access and management           |
| Testing Lab | Security Testing | Isolated AD lab and security testing resources |

## 🖥️ Infrastructure Overview
### Core Platform
- **Primary Server**: Intel NUC8 Hades Canyon
  - Intel i7 with Radeon Graphics
  - 64GB RAM
  - Storage: 250GB SSD (OS) + 1TB SSD (VMs)
- **Hypervisor**: Proxmox VE 8.0
  - Snapshot capabilities
  - Virtual networking
  - Resource management

### Core Services
- Security Infrastructure:
  - DNS security and filtering with Pi-hole
  - Certificate management through Step-CA
  - Secure proxy services with NGINX
- Containerized Environment:
  - Secured Docker deployments
  - Container isolation practices

## 🛠️ Tools & Technologies
### Primary Tools
- Proxmox VE for virtualization
- Docker container platform
- Kali Linux for penetration testing suite
- Security tools (Burp Suite, Metasploit, Nmap)
- Network analysis tools and monitoring tools

### Development Tools
- Bash scripting for security tool automation
- System hardening configurations
- Service deployment and security configurations (NGINX, Docker, PKI)

---
*Last Updated: February 2025*  
[About Mario Torres](about.md)
