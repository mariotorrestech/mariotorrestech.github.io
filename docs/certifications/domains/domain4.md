#### Domain 4

# Communication and Network Security

## Implement secure design principles in network architecture

### Open System Interconnection (OSI)

PDNTSPA - Please do not throw sausage pizza away

### PHYSICAL

##### Performance Metrics

- Bandwidth
  - the max amount of data that can be transmitted
- Throughput
  - the actual rate of successful data transfer achieved, measured over a period of time
- Signal-to-noise ratio
  - level of desired signal in comparison with the amount of background noise
- Latency
  - amount of time it takes for a signal to travel from its source to its destination and back
- Jitter
  - variation in time delay between data packets over a network

##### Traffic Flows

​	N/S. W/E

##### Physical Segmentation

- In-band management
  - does not involve any physical segmentation
  - involves managing network devices through the same network that is used to transmit user or application data
  - Managing a switch via the same network that transmits user traffic
- Out-of-band management
  - contrasts with in-band management because it involves a separate network
  - Network devices are managed from a dedicated network that is separate from the main network over which user traffic travels. More Secure.
- Air-gapped management
  - an extreme form of segmentation that involves physically isolating a network from all others

##### Logical Segmentation

- Virtual Local Area Networks (VLANs)
  - a single physical network can logically partitioned into multiple smaller networks
- Virtual Private Networks (VPNs)
  - allow you to securely connect to a private network across public network infrastructure
- Virtual routing and forwarding (VRF)
  - Allows us to make many virtual networks with just a single network component
- Virtual Domains
  - provides the ability to create multiple separate security domains within a single physical device

### DATALINK

Protocols

- L2F
  - Layer 2 Forwarding tunneling protocol
- Point-to point tunneling protocol (PPTP)
  - 3 distinctive authentication protocols
    - Password Authentication Protocol (PAP)
      - Simplest be least secure, uses static plaintext password
    - Challenge Handshake Authentication Protocol (CHAP)
      - More secure than PAP, as password is encrypted before sent over the wire
    - Extensible Authentication Protocol (EAP)
      - Considered the most rebust of the three, due to increased flexibility, allowing to to be combined with other protocols
- L2TP
  - Layer 2 Tunneling Protocol
- SLIP
  - Serial Line Internet Protocl - an older protocol used for remote access via serial ports and modem connections
- ARP IP to MAC
  - used to map ip addresses to MAC addresses
- RARP MAC to IP
  - used to map MAC addresses to IP addresses

PEAP - EAP with TLS tunnnel

### NETWORK

Protocols

- ICMP
- IGMP
- IPsec
- OSPF

### TRANSPORT

TCP - Transmission Control Protocol

- Reliable/ordered transmission (truck delivery)

UDP - User Datagram Protocol

- unreliable, unordered transmission (send/pray)

Ports

- 20 - FTP data transfer port
- 21 - FTP control port
- 22 - Secure Shell (SSH)
- 23 - Telnet (remote CLI)
- 25 - Simple Mail Transfer Protocol (SMTP)
- 80 - Hypertext Transfer Protocol (HTTP)
- 443 - Hypertext Transfer Protocol Secure (HTTPS)

### SESSION

Supports interhost communicating and coordinated diaolgue between cooperating application processes.

Maintains logical connection between two proceses on end hosts

Ideal place for identification and authentication

Protocols:

PAP, CHAP, EAP

NetBIOS

- Network Basic Input/Output System is a legacy communications protocol that allows computers within a local network to communicate with each other and with various peripherals like printers/FS

RPC

- Remote Procedure Call is a communication protocol that facilitates communications between clients and servers to execute procedures

### PRESENTATION

Formatting and encryption of data for end users

Ensures compatible syntax in how the information is represented for exchange by applications

Provides translation, encryption/decryption, and compression/decompression

### APPLICATION

Layer where most functionality resides, also the layer where most security breaches and attacks occur

Provides a user interface through which a user gains access to communication services

Ideal place for end-to-end encryption and access control

##### Protocols:

HTTP/S

- HTTPS incorporate SSL/TLS for purposes of tunneling and therefore protecting traffic from interception across the internet

FTP/FTPS/TFTP

DNS/DNSSEC

Telnet

- insecure, best used with SSH

SSH

- network protocol that utilizes public-key cryptography for purposes of secure connections to a remote computer

SMTP/POP3

- SMTP using TCP port 25 is the protocol used for sending email over the internet
- POP3 using TCP over port 110 is the one used for receiving email

SNMP

- SNMP using UDP ports 161 and 162 is a protocol most often used by network admin to collect, organize, and manage information related to devices on a network

---

### Network Admin

### Convergence and VOIP

######Core Concepts:

- **Convergence** refers to the ability of native IP networks to carry non-IP traffic via what are known as converged protocols
  - Popular converged protocols include Fibre Channel over Ethernet (FCoE), Internet Small Computer Systems Interface (iSCSI), Voice over Internet Protocol (VoIP)


- VoIP Protocols: SRTP (Secure Real-Time Transport Protocol) and SIP (Session Initiation Protocol)
- Vishing is a specific type of attach that takes place in VoIP environments

Common Terms Related to Voice:

- PBX:

  - Private Branch Exchange is a private telephony network that supports internal communications, usually in the context of an organization or a place like a hotel

- PSTN:

  - Public switched telephone network is essnetial the traditional, copper-wire based telephone network that allows people and business to communicate with each other

- VoIP: Voice over Internet Protocol

  - allows people to communicate via an internet connection, instead of a traditional copper-wire-based phone line

  - 2 main VoIP protocols:

    1. Secure real-time transport protocol (SRTP)
       - This is the secure version of RTP, which uses encryption, authentication, integrity, and replay attack protection.
       - RTP is mainly used for straiming voice/video over IP, with no existing security in it
       - SRTP also provides good bandwidth optimization, low resource requirements, and is independent from underlying protocols
    2. Session Initiation Protocl (SIP)
       - SIP is responsible for initiating, maintaining, and terminating voice and video sessions. It can also support a direct connection between PBX and public telephony networks

- Infiniband

  - Protocol for remote direct memory access (RDMA)
  - Designed to provide access to memory as quickly as possible across the network. commonly used in apps like machine learning

- Compute Express Link

  - protocol for connecting CPUs to other components, such as devices and memory as quickly as possible

### Network security attacks

######Core Concepts:

- Network attacks resembe network assessments in terms of the steps/phases that each follows, with exception that attacks also include an exploitation phase
- Passive attacks do not change the environment or information; avtive attacks can change information
- SYN scanning is an active attack that abuses the way the normal 3-way TCP handshake operates and helps an attacker determine what services might be running on a target machine
- SYN flooding abuses the normal 3-way TCP handshake by rapidly 'flooding' a target machine with mulitple SYN requests that ultimately exhaust the target machine's resources, causing it to crash
- A Denial-of-Service (DoS) attack is any attack that attempts to impede or completely deny functionality.
- ARP poisoning involves a malicious user modifying their ARP table to direct network traffic meant for another device to their device
- ARP uses tables to map IP addresses to physical addresses - the MAC addresses - of a deice . Every device on a network has a physical address and an ARP table

### IP-based attacks

#### Fragment Attacks

- Overlapping fragments
  - This attack uses overlapping fragments in an attempt to bypass firewalls and IDS/IPS tools to gain access to a target system.
- Teardrop
  - With this TCP attack, the attacked sends fragments of packets of differing sizes, out of order, and with fake fragment sequence numbers to a target system. The target system cannot reassemble the packets, causing it to consume its resources and degrade its performance and even crash, thus causing a DoS attack

#### IP Spoofing attacks

- ##### Smurf (OLD)

  - Attacker spoofs their IP address to match the victim's

  - Attacker sends multiple ICMP echo requests packets to intermediary network devicesss

  - Those devices respond with ICMP replies, which are directed to the victim (Since the attacker spoofed their IP address to match the victim's in step #1)

    This causes a DOS to take place at the victim's device, which is inundated with ICMP reply traffic

- Fraggle (OLD)

  - Like a smurf attack, a fraggle attack is also a DoS service attack that begins with IP spoofing. The attacker then sends massive amounts of UDP packets to the target systems

#### Common Tools and Protocols

- Ping
  - TCP/IP based
- Traceroute
  - TCP/IP based. Like Ping but maps out a network connection from one host to another
- ICMP
  - Internet Control Message Protocol and supports TCP/IP utilities like ping and trace route, among others.
  - ICMP messages come as different types that are differntiated by types and associated codes (subtypes)
- DHCP
  - Dynamic Host Control Protocol
    - used to assign a valid IP address to a device when it firsts connects to a network

### Wireless

######Core Concepts:

- IEEE 802.11 specifications define wireless standards
- Wireless authentication requires an authenticated key exchange mechanism
- Temporal Key Integrity Protocol (TKIP) was designed to replace WEP without requiring the replacement of legacy hardware, due to a significant flaw found in WEP
- To protect any wireless communication, **four** things are needed:
  - **access control**
  - **authentication**
  - **integrity protection**
  - **encryption**

- Wireless Authentication
  - 3 main ways to authenticate to a wireless network
    - Open authentication
      - device connect by using the network's SSID with no security enabled
    - Shared key
      - pre-shared network key is used, which is shared across any device tha needs to connect to the network
    - EAP
      - authentication requires an authentication key exchange mechanism
      - EAP used can lead to one or two factor authentication:
        - One factor: EAP-MD5, LEAP, PEAP-MSCHAP, TTLS-MSCHAP, EAP-SIM
        - Two factor: EAP-TLS, TTLS with OTP, and PEAP-GTC
- Wireless Encryption
  - Temporal Key Integrity Protocol (TKIP)
    - Was instituted as a fix of the WEP vulnerabilities and was used in WPA but is vulnerable to attacks mainly due to the WPA requirement to support hardware compatibility with WEP
  - Counter-Mode-CBC-MAC Protocol (CCMP)
    - Uses advanced encryption standard (AES) with 128 bit keys which is used in WPA2 and WPA3

​**importance of TKIP relative to WEP and why WEP is considered weak**

---

#### TKIP Summary

- Deisgned to **replace WEP** without requiring the replacement of legacy hardware
- Required due to significant flaw found in WEP — specifically, the use of a weak IV that allowed WEP to be easily cracked
- Sends each new packet with a unique encryption key (key mixing)
- TKIP is no longer considered secure and is superseded by AES

STOPGAP protocol

A stronger protocol was devloped, a counter mode version, that uses stronger encryption (AES)

TKIP implements a **Message Integrity Check (MIC)**, often referred to as "Michael"

- basically, it provides integrity control, like a hashing algorithm
- Additionally TKIP, was implemnted in a manner almost like applying a patch.

### VLAN and SDN

VLANs we know…

#### SDN

- Two primary planes:

  - Control Plane
    - acts as the "brain" of the SDN and understands everything about the network
    - determines routing packets
  - Data Plane
    - handles the actual forwarding of packets to the proper destination


### Wide area networks (WAN)

######Core Concepts:

- WANs connect LANs through technologies such as:
  - dedicated leased lines, dial up, phone lines, satellite/other wireless links, and data packet carrier services
- WAN Protocols include:
  - X.25, Frame Relay, Asynchronous Transfer Mode (ATM), and Multi-Protocool Label Switchins (MPLS)

Data packet carrier sersvices are most often used

**MPLS** is at the forefront of current WAN connectivity solutions because it offers network connectivity that includes built-in security.

- using features like forwarding tables and labeling schemes, MPLS providers can guarantee that customer's data transmissions cannot be touched by anyody else while traveling

## Secure network components

### Network Architecture

######Core Concepts:

- Network architecture includes employing concepts such as:

  - defense in depth
    - combing multiple layers of security controls to protect a network
  - partitioning / a well-protected network perimeter
    - refer to the same concept where visibilty of certain network traffic is limited through the user of networking devices like switches/routers/firewalls
    - Partitioning: control the flow of traffic between segments
    - Network perimeter: the last point any organization can control
      - controls should comprise preventive, detective, and corrective measures
      - Choke points to be used for limiting egress/ingress

  - network segmentation
    - e-commerce and email shouldnt really be ran on internal networks. from a security perspective this is unwise because people from the public network/internet would be on the inside, where everything would be at risk
  - DMZ:
    - To mitigate the above Risk can be mitigated through the creation of a subnet, referred to as a DMZ - where services and apps that require public internet access can be segregated
    - not part of the internet or internal network, it sits in between the two and is controlled by the organization
  - bastion hosts
    - devices and apps within a DMZ are referred to as bastion hosts
    - Within the DMZ, hosts and apps that have been hardened and strengthened to protect against exploits/attacks are referred to as bastions
    -

- Proxies are devices that act on behalf of someone else

- NAT and PAT are examples of proxies that faciliate wide scale access to the internete and serve as a layer of protection against eavesdropping of internal network structures

###### Microsegmentation

By way of quick/cheap virtualization tech to deploy logical networks, cost effectiveness of virtualized networks allows us to segment our networks at a more granular level

**Virtualized networks allow you to deploy virtual firewalls easily and at low cost**

The benefit is virtualized segments get their own firewalls that feature much stricture rules to limit the opportunites for malicious traffic to get through

<u>Comparison</u>:

image 1
### VS
image2


Some technologies that we use alongside microsegmentation are outlined below:

- Network overlays/encapsulation
  - The creation of virtual networks that are abstracted or overlaid on top of the physical network
- Distributed firewalls
  - Micro segmentation can be used to easily and cheaply deploy multiple firewallss
- Distributed routers
  - Similarly, distributed routers allow us to distribute routing rules to individual workloads as opposed to having one central routes
- IDS/IPS
  - can be strategically deployed to protect individual workloads or network segments
- Zero trust architecture
  - Allow us to implement granular trust zones

###### Proxy

- A proxy/proxy server is an intelligent application or hardware that acts as an intermediary and is placed between clients and a server
- Layer 7, often found at this layer because it's inherently intelligent
- device that acts on behalf of of something else, like an app or user
- Helps facilitate the connection between a client and a server, because it is better equipped to manage and direct outgoing/incoming traffic!

###### NAT and PAT

- NAT:
  - mechanism that allows us to translate private IP addresses to public ones and vice versa
- PAT:
  - helps us transform port translation, in the same notion as IP address translation
  - an inherent part of NAT
- These two technologies provide a layer of security to organizations by masking internal networking schemes, which can hinder reconnaisance efforts of attackers

### Firewall Technologies

_reminder: **PLEASE DO NOT THROW SAUSAGE PIZZA AWAYYYYYY**_

- _PDNTSPA_
- _not… PDNTASP_

######Core Concepts:

- Firewall: a concept that enforces security rules between two or more networks

- Firewall technologies include:

  ​_SORTED by simplest - complex // lowest - highest latency_

  - **simple packet filtering firewalls**
    - Layer 3 (NETWORK)
    - Examines packet headers to either block/allow
    - Uses ACLs to accept/deny access
  - **stateful packet filtering firewalls**
    - Layer 3 (NETWORK)
    - Involves keeping records of active connections and making decisions based on the state
    - Can identify which packets are coming from an established connection and allow them
  - **Circuit-level firewalls**
    - Layer 5 (APPLICATION)
    - Create a circuit between client and server without requiring knowledge about the service
    - Have no app-specific controls
    - Ex: SOCKS server
  - **application-level firewalls**
    - Layer 7 (**APPLICATION**, duh)
    - ability to inspect packet paylod
    - different proxy needed for each service
    - can be a performance bottleneck

Context-based Access Control (CBAC)

- intelligentyly filters TCP/UDP packetssbased on application layer protocol session information

### Firewall Architectures

######Core Concepts:

- Firewall architectures can vary based upon multiple factors and needs
- common firewall architecture includes:
  - **packet filtering**
    - can only make decisioned based upon the layer it operates at, layer 3 – the header portion of the packet, which contains source/dest. IP address, services, etc
  - **dual-homed host**
    - imporves upon packet filtering router by replacing it with a more intelligent computer that contains two network cards
    - the host can understand ALL layers of the OSI model and can therfore support all types of firewall technologies (simple to very complex decisions)
  - **screened host**!
    - combining the above 2
    - The router can handle the first level of decision-making related to incoming packets - and any packets allowed through are furhter examined by the bastion host.
  - **screened subnet**!
    - where two firewalls are usedand between them a subnet, such as a DMZ, is created.
    - Traffic from the outside can be specifically directed to the DMZ and thereby protect the internal network from potential attacks
    - expensive as 2 firewalls are
  - **three-legged firewall**!
    - aka 3-zoned firewall

### IDS and IPS!

######Core Concepts:

- data inspection involves monitoring and examining data
- <u>Intrustion Detection System</u>: Performs data inspection and **detects/logs/reports/sometimes triggers other devices to take corrective actions**
  - the sole purpose is to detect
  - to gain the benefits of a complete control, the IDENTITIES would need to be coupled with something else that could provide the additional capabilities of prevention and correction
  - an IDS is connected to the network via a mirror/span port
    - this allows the IDS to get a copy of all network traffic
    - if maliicious traffic identified, the identities can communicate with the firewall which can then take preventive/corrective actions

- <u>Intrusion Prevention System</u>: performs data inspections and **additionally precents or takes corrective actions**
  - IPS is placed in line with the network traffic because it has the capability to detect, precentm and correct
  - Network traffic passes thru the IPS
  - If a rule is triggered for malicious activity, the IPS can act and precent that from traversing the network
- Mirror/span/promiscous port:
  - refers to setting a specific port on a network device (like a switch) to receive ALL traffic transiting the network device for monitoring purposes
- Two types:
  - host-based
    - installed on a server and monitors only that host
  - network-based
    - monitors network traffic transiting a network segment
- Two methods of detection:
  - Pattern
    - no hope of detecting the latest threats if they don't have the signatures for them
  - Anomaly
    - can help detect threats even if it's a new attack and we don't already have the signatures for it

Ingess/egress

Allow/deny list

### Sandbox

######Core Concepts:

- safe area where untrusted code can be isolated and run
- four possible alert scenarios:
  - true positive
    - alarm is generated and attack is present
  - false positive
    - alarm is generated but no attack is present
  - true negative
    - alarm is not generated and no attack is taking place
  - false negative (WORST CASE)
    - alarm is not generated and attack is actually taking place
    -

### Honeypots and Honeynets

### Endpoint Security (ex, host-based)

######Core Concepts:

- endpoint security focuse on protection of devices found on corporate networks and seeks to minimize the attack surface and therby prevent/minimize attacks
- Network access control (NAC) solutions seek to unify endpoint security technology, user authentication, and overall network security

## Implement secure communication channels according to design

### Tunneling and VPNs

### IPSec

######Core Concepts:

- preferred for establishing a VPN and is embedded into ipv6as a default feature
- IPsec offers authentication via Authenticaiton Header (AH) and encryption via Encapsulating Security Payload (ESP)
- IPsec works in one of two modes:
  - transport
  - tunnel
- Internet Key Exchange (IKE) is used to generate the session key shared at each end of the VPN
- Security Associations (SA) are used to establish components in each direction for an IPsec-based VPN. One SA is needed for each component in each direction

### SSL/TLS

######Core Concepts:

- Secure Sockets Layer / Transport Layer Security (SSL/TLS) provide secure client to server connections; the two names refer to the same thing but TLS is now the proper standards and most current version. SSL is obsoleted
- DROWN attack is a major threat to SSLv2
- SSL/TLS connection steps:
  - client hello
  - Server hello
  - creation and sharing of session key
  - establishment of secure session
- Asymmetric cryptography is used to encrypt the symmetric session key created by the client
- Unencrypted SSL sessions can exist, where a browser and server authenticate to one another, but the communications channel is not encrypted (?)

### Remote Authentication

######Core Concepts:

- remote authentication protocols include:
  - RADIUS
    - Originally developed to support dial-in neetworking and provides authentication, authorization, and accounting
  - TACACS+
    - uses TCP and encrypts all packets
  - Diameter
    - successor to RADIUS and includes much-improved security, including EAP

---

OSI REVIEW:

1. ### Physical

   ​_Binary transmission of data across physical media (wire, fiber, etc)_

   1. Devices:
      1. Hubs, NICs, Network media
   2. Protocols:
      1. **802.1x**

2. ### Datalink

   _Physical addressing, and reliable point-to-point connection_

   1. **MAC** address
   2. Devices:
      1. switches / bridges
   3. Protocols:
      1. ARP, PPTP, PPP, PAP, CHAP, EAP, L2TP

3. ### Network

   _Logical addressing, routing, and delivery_

   1. IP address
   2. Devices
      1. Routers / packet-filtering firewalls

   3. Protocols
      1. ICMP (ping), IPSec, IGMP

4. ### Transport

   _End-to-end connection with error correction and detection_

   1. Common Ports (ports == services)
   2. Protocols
      1. TCP/UDP, SSL/TLS, BGP, iSCSI (SAN)

5. ### Session

   _Interhost communications and session management_

   1. Devices:
      Circuit Proxy Firewall
   2. Protocols:
      1. NetBIOS / RPC

6. ### Presentation

   _Formatting of data_

   1. Protocols:
      1. XML, JPEG, ANSi

7. ### Application

   _Identify capabilities of applications and resource availability_

   1. Devices:
      1. Application Firewall

   2. Protocols
      1. HTTP/S, DNS, SSH, SNMP, LDAP, DHCP
