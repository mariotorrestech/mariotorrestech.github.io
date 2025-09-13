# Active Directory - Kali Lab

!!! note "Overview"

    Environment based on attacking vulnerable Windows Domain Controller and user machines.

=== "Kali based tools"

    * nmap
    * burp suite
    * JackTheRipper

### Environment Components

```mermaid
graph TD
    subgraph Lab Network - 10.0.3.0/24
        DC[Domain Controller<br>Windows Server 2019]
        WS1[Workstation 1<br>Windows 10]
        WS2[Workstation 2<br>Windows 11]
        SVR[File Server<br>Windows Server 2019]
        VULN[Vulnerable Server<br>Windows Server 2016]
        KALI[Kali Linux<br>Attack Machine]
    end
    
    DC --- WS1
    DC --- WS2
    DC --- SVR
    DC --- VULN
    KALI -.- DC
    KALI -.- WS1
    KALI -.- WS2
    KALI -.- SVR
    KALI -.- VULN
```

!!! note "Connectivity details"

    Kali had access to internet - AD LAB
    AD Lab including DC only had internal LAN access, no external access.

## Domain Infrastructure

- **Domain Name**: MARVEL
- **Forest/Domain Functional Level**: Windows Server 2016
- **Domain Controller**: Windows Server 2019
  - Roles: AD DS, DNS, DHCP

=== "Client systems"

    | System    | OS             | IP         | Purpose          |
    | --------- | -------------- | ---------- | ---------------- |
    | Punisher  | Windows 10 Pro | 10.0.3.100 | User workstation |
    | Spiderman | Windows 10 Pro | 10.0.3.101 | User workstation |

=== "Server systems"

    | System            | OS                  | IP        | Purpose                     |
    | ----------------- | ------------------- | --------- | --------------------------- |
    | Domain Controller | Windows Server 2019 | 10.0.3.10 | File shares, sensitive data

---

_Return to [Home](../index.md)_

_Return to [Homelab](../homelab/index.md)_
