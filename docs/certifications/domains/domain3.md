#### Domain 3

# Security Architecture and Engineering

##### Overview:

_This domain focuses on the different process/standards/framworks/structures to design and implement secure architectures and how, in order to achieve that, the security function needs to be involved at the start of the engineering life cycle and throughout each of the subsequent phases_

---

## Research, implement, and manage engineering processes using secure design principles

### Security's Involvement in Design and Build

######Core Concepts:

- Security must be involved in all phases of designing and building a product or system; it must be involved from beginning to end

### Determining Appropriate Security Controls

######Core Concepts:

- Regardless of the framework, model, or methodology used, the risk management process should be used to identify the most valuable assets and risks to those assets, and to determine appropriate and cost-effective security controls to implement this.

##### Secure Defaults

- Any default settings a system has should be secured to the extent possible, so no compromise is facilitated.

##### Fail Securely

- If a system or components fail, they should do so in a manner that doesn't expose the system to a potential attack. Example: a lock should remain engaged if electricity fails at the building.

##### Keep It Simple and Small

- Remove as much complexity from a situation as possible and focus on what matters most.

  - Smaller attack surface

  - Less errors and vulnerabilities

  - Less complex testing

  - Easier and more efficient troubleshooting and problem resolution

##### Zero Trust and Trust but Verify

Instead, authentication/authorization required before granting access to systems/individuals

- **Micro-segmentation of networks**
- **Granular enforcement of permitter ingress/egress points**

TRUST NOTHING and is based upon the premise that organizations should not automatically trust anything internal or external to enter their perimeter.

##### Privacy by Design

- Premised on the belief that privacy should be incorporated into networked systems and technologies by default and designed into the architecture

1. Privacy as proactive and preventative, not reactive and remedial
2. Privacy as the default setting
3. Privacy embedded into design
4. Full Functionality within a given solution
5. End-to-end security
6. Visibility and Transparency
7. Respect for User Privacy

##### Shared Responsibility

- Cloud/third-parties are partly responsible

##### Cyber Kill Chain

- **Recon**
  - Involves identifying a target and looking for information that will be useful
- **Weaponization**
  - Involves building an exploit that aims to take advantage of any vulnerabilities identified in the recon step
- **Delivery**
  - Involves the attacker launching their attack
- **Exploitation**
  - The attacker executes their malicious code on the target's systems
- **Installation**
  - Comes immediately after exploitation, and the attacker not has software installed 0n the target's systems
- **Command** **and** **Control**
  - Allows the attacker to remotely control their malware running within their target's systems
- **Actions**
  - The attacker carries out their initial objective

## Understand the fundamental concepts of security models

### Security models

######Core Concepts:

- A model is a representation of something real
- A security model is a representation of what security should look like in an architecture

###### Concept of Security

Bottom line: to ensure protection of any architecture, it must be broken down into individual components, and adequate security for each component needs to be put in place.

The chain is only as strong as it's weakest link

### Enterprise Security Architecture

######Core Concepts:

- An architecture is a group of components that work together
- Security architecture involves breaking down a system to its components and protecting each component based upon its value

###### Security Models

- Essentially, they're rules that need to be implemented to achieve security
- Two types exist: Layer/Lattice based models and rule-based models

### Layer-based models

Core concepts:

- Layer-based security models are also considered lattice-based security models
- Bell-LaPadula addresses on confidentiality
- Biba addresses only integrity
- Lipner implementation is not a model, it is an implementation that combines the best features of Bell-LaPadula and Biba

#### Bell LaPadula

Addresses only confidentiality
Based on three basic principles:

1. **Simple security property**, aka – '**no read up**' property.

   - Relates to reading and denotes that any subject at a particular security level may not read an object at a higher level.

2. The **star (*) property**, aka – "**no write down**" property

   - relates to writing and denotes that any subject at a particular level may not write at a lower level

3. The **strong star** property relates to both r/w.

   - Having an ability to both r/w means a subject should be able to r/w at their own layer, nothing higher or lower.

#### Biba

Bieba == RuWd (Rude)

- Read up, write down
- Focuses on ensuring data integrity only

Also based on three basic principles:

1. **Simple integrity property**
   - "No read down" relates to reading and denotes that a subject at a particular level may not read an object at lower integrity level
2. **Star (*) integrity property**
   - "No write up": relates to writing and denotes that a subject at a particular level of integrity may not write to an object at a higher integrity level
3. **Invocation property**
   - A subject can't send information to someone that is rated at a higher layer of information than the current one the subject holds

_BELL LAPADULA IS FOR **CONFIDENTIALITY**_

_I IN BIBA IS FOR **INTEGRITY**_

###### Comparison:

###### Lipner Implementation

- Not a model, an implementation that takes the both of the above
- Confidentiality and Integrity

### Rule-based models

######Core Concepts:

- Information flow models track the flow of information and can help uncover covert channels
- Covert channels are unintentional communication paths: 2 types exist:
  - storage and timing
- Clark-wilson is an integrity focused rule based model that includes 3 goals and 3 rules
- Brew-Nash "Chinese wall" - designed to prevent conflicts of interest

Core of any model is a set of rules between subjects and objects

#### Information Flow

If it can be tracked, it can be tracked throughout its lifecycle. Meaning vulnerabilities are detected, and insecurities like covert channels.

#### Covert Channels

**Unintentional** communication paths that may lead to the disclosure of confidential information

Covert channels are unintentional & may involve storage or timing; when they exist, confidentiality may be compromised.

- Storage:
  - Process writes sensitive data to RAM, and the data remains present after the process completes; now, other processes can potentially read the data
- Timing
  - An online web server responds to a user providing an existing username within 3s, while if the username doesnt exist it takes 1s. That allows the attacker perform username enum.

---

#### Clark-Wilson

- Rules based model that focuses only on **integrity**

- Biba which only prevents unauthorized subjects from making any changes, CW offers further protection and meets 3 **goals of integrity:**

  1. Prevents unauthorized subjects from making any changes (this is the only one that Biba also addresses)

  2. Prevent unauthorized subjects from making bad changes

  3. Maintain consistency of the system

##### Well-formed transactions:

- Good, consistent validated data
- Only perform operations in a manner that won't compromise in the integrity of objects

##### Separation of duties

- One person shouldn't be allowed to perform all tasks related to a critical function

##### Access Triple

- Subject | Program | Object
- A subject cannot directly access an object, ie. In a database
- **Access must go through a program that enforces access rules**

---

#### Brewer-Nash (the Chinese Wall) Model

- Prevents conflicts of interest
- Stipulates and ensures that information flows between subjects and objects are only allowed if the information does not provide a conflict of interest.

Example:

Between Dev and Prod departments in an organization, as the 2 departments should not be able to influence each other or even allow access between each other.

Like Ball-LaPadula, Brewer-Nash primarily addresses issues related to _**confidentiality**_

---

###### Graham-Denning Model

###### Harrison-Ruzzo-Ullman Model

### Certification and Accreditation

######Core Concepts:

- **Certification** is the comprehensive technical analysis of a solution to confirm it meets the desired needs
- **Accreditation** is a management's official sign-off of certification for a predetermined period of time

### Evaluation Criteria (ITSEC and TCSEC)

######Core Concepts:

- TCSEC, aka - the orange book - is the first evaluation criteria system
- ITSEC followed TCSEC and was developed by Europeans to include elements of the Orange book and others
- ITSEC applies to networked environments and measures functional and assurance elements separate from one another

#### TCSEC - The Orange Book

- Classification levels - the criteria:
  - A1 - Verified Design
  - B3 - Security labels, verification of no covert channels and must start secure during start up
  - B2 - Security levels and verification of no covert channels
  - B1 - Security labels
  - C2 - Strict login procedures
  - C1 - Weak protection mechanisms
  - D1- Failed or was not tested

Only measure confidentiality.

#### Information Technology Security Evaluation Criteria (ITSEC)

Unlike the orange book, ITSEC measures more than confidentiality. It works well in a network environment.

- Assurance levels

  - E6: Formal end-to-end security tests + source code reviews
  - E5: Semi-formal system + unit tests and source code review
  - E4: Semi-formal system + unit tests
  - E3: Informal system + unit tests
  - E2: Informal system
  - E1: System in development
  - E0: Inadequate assurance

  ITSEC was replaced by COMMON CRITERIA in 2005.

### Common Criteria

######Core Concepts:

- Evaluation criteria system is the best and most popular system
- Compromised of a multiple components that work together and alllow a globally recognized rating to be assigned to products
- Common Criteria EAL rating levels

###### Common Criteria Process

1. The <u>first component</u> is the **Protection Profile (PP)**

- **Specification of functional and assurance requirements for a specific type of security product**

- Example:
  - Protection Profile for firewalls state the security capabilities that any firewall should contain, 2FA, VPN capabilities, ability to encrypt, secure logging, etc.

What the CC PP components represent:

2. The <u>second component</u> **Target of Evaluation (TOE)**

   1. **The specific product/system to be evaluated**

      Example: If a vendor desires for the firewall to be rated according to the CC, the firewall would be considered the TOE.

3. The <u>next component</u>, Security Targets (ST)

   - **Writtent statement by vendor explaining how functional and assurance specifications of the product meet the protection profile (PP)**

   1. Describe – from the vendor's perspective – each of the firewall's security capabilities that _**match up**_ the capabilities outlined in the PP.
   2. Security targets are going to be scrutinized under the dual sense of **functional** and **assurance security** capabilities
   3. ST is where the value of the CC lies. As each capability tested extensively, there is much documentation that is produced that highlights the security capabilities/deficiences of each ST being tested. This provides potential consumers the information that is needed for them to evaluate vendor products

The **evaluation** process is part of the CC that creates meaningful documentation that becomes available to any interested parties. At the end, after the evaluation, an overall EAL level will be assigned to the firewall.

**Assign EAL**

#### EAL LIST 1-7

1. Functionally tested
2. Structurally tested
3. Methodically tested and checked
4. Methodically designed, tested, and reviewed
5. Semi-formalll designed and tested
6. Semi-formally verified, designed, and tested
7. Formally verified, designed, and tested

###### The potential negative implications if a product is rated too high

- Could be too secure and require extensive configuration, admin skills, maintenance. Could leave org at greater risk if consumers dont use the feature. IE it's too annoying to use.
- Functional and security must be balanced.

###### If a product is patched or receives software/firmware updates, the EAL remains the same

- EAL remains through its lifespan, unless a major change in product functionality is introduced.

## Select Controls based upon system security requirements

### Security Control Frameworks

Core Concepts:

- Security control frameworks
  - aid with the control selection process
  - provide guidance, based up best practices
  - Features from multiple frameworks can be used to meet the needs of an org

Control frameworks provide comprehensive guidance based upon best practices.

###### Understand the major frameworks at a high level, especially ISO 27001/02, which is internationally recognized framework

- ##### COBIT

  - Control objectives for IT framework is particularly useful for IT assurance, such as conducting audits and gap assessments
  - Created for IT governance, and therefore particularly useful for IT assurance activities

- ##### ITIL

  - Defines the processes a well run IT department
  - from the onboaording process, to procurement, change management, configuration management, and access control, etc.
  - Defines the processes for IT service management that focuses on aligning IT services with business goals and objectives

- ##### NIST SP 800-53

  - Best practices to help organize cybersecurity control

- ##### PCI DSS

  - Standards for organizations handling credit cards

- ##### <u>ISO 27001</u>

  - Specific the requirements for establishing, implementing, maintaining, and continuinally improving an information security management system within the context of the organization.
  - Also includes requirements for the assessment and treatment of information security risks tailored to the needs of the organization.
  - The requirements set out in the ISO 27001 are generic and are intended to be applicable to all organizations, regardless of type/size/nature
  - **Organizations can be certified against ISO 27001**
    - **Annex A** of the standard contains the following domains
      1. Information security policies
      2. Organization of information security
      3. Human resource security
      4. Asset management
      5. Access control
      6. Cryptography
      7. Physical and environmental security
      8. Operations security
      9. Communications security
      10. System acquisition, development, and maintenance
      11. Supplier relationships
      12. Information security incident management
      13. Information security aspects of business continuity management
      14. Compliance

- ##### <u>ISO 27002</u>

  - Provides **guidelines** for organization information security standards and information security management practices including selection, implementation, and management of controls, taking into consideration the organization's information security risk environment.
  - **Essentially ISO 27002 provides guidance for implementing controls in ISO 27001**

- ##### COSO

- ##### HIPAA

  - Relates to security controls in the **healthcare industry**

- ##### FISMA

  - Requires federal agencies to develop, implement agency wide security programs provide information security for the operations/assets of the agency

- ##### FedRAMP

  - Any cloud services that hold US federal govt data must be FedRAMP authorized

- ##### SOX

  - Sarbanes-Oxley Acts is a direct result of the financial fraud at Enron.
  - Prevents financial fraud by public companies and thereby protects the financial interests of shareholders

## Understand security capabilities of information systems

### RMC, Security Kernel, and TCB

######Core Concepts:

- Security within information systems always pertains to subjects and objects
- The Reference Monitor Concept (RMC) is a **concept**
- **Implementation** fo the RMC is known as a security kernel
- A security kernel should consist of 3 properties or characteristics:
  1. Completeness
  2. Isolation
  3. Verifiability
- The term Trusted Computing Base (TCB) refers to all the protection mechanisms within an architecture; the TCB is the **totality** of protection mechanisms within an architecture

##### Subjects and Objects

- **Active** entities -- Person, process, or program that actively tries to access an object
- **Passive** entities -- anything that is being passively accessed by a subject like a file, server, process

##### Reference Monitor Concept (RMC)

RMC features include:

    - must mediate all access
    - Be protected from modification
    - Be verifiable as correct
    - Always be invoked

The implementation of the RMC is called the security kernel

##### Security Kernel

- ## The implementation of the RMC. A viable security kernel should contain 3 properties
  1. **Completeness** - means it's impossible to bypass the mediation
  2. **Isolation** - relates to the mediation rules and specifically ensures that that mediation rules are tamper-proof. Only authorized individuals may change.
  3. **Verifiability** - relates to the aspect of assurance. Logging and monitoring verify that it's functioning correctly

##### Trusted Computer Base (TCB)

### Processors (CPUs)

- A CPU is the brain of a computer, it processes all instructions and ultimately solves problems
- CPU process involves an ongoing 4 step process: Fetch -- Decode -- Execute -- Store
- CPU oeprates in one of 2 states: the supervisor state or the problem state

From a security perspective, these states can also be thought of as privilege levels and are simply **operating modes for the processor that restrict the operations that can be performed by certain processes**

Supervisory State:

- Higher privilege level
- Typically, where the system kerne runs, allowing full access to all of the instructions and capabilities of a CPU

Problem State

- Lower privilege level
- Limited access to CPU instructions
- The standard operating mode of a CPU
- Known as a 'problem' state because fundamentally that's what a CPU does, solve problems

### Process Isolation

######Core Concepts

- Prevents interactions that could result in negative consequences
- Two primary methods:
  - Memory segmentation
  - Time division multiplexing

From a security perspective, process isolation is a critical element of computing, it prevents objects from interacting with each other and their resources.

In other words**, the actions of one object should not affect the state of other objects**

###### Time-Division Multiplexing

- Process isolation is determined by the CPU. **CPU allocates very small slots of time to each process.**

###### Memory segmentation

- Relates more to RAM. **Memory segmentation ensures that the memory assigned to one application is only accessible by that application**

### Types of Storage

######Core Concepts:

- 2 types of storage: primary/secondary storage
- Primary: fast/volatile
  - Data is lost when device is powered off
  - Cache, RAM
- Secondary: slow/non-volatile
  - Large size
  - Hard drives, SSDs, tapes

### System Kernel

######Core Concepts:

- Core of the OS that has complete control over everything in the system
- System kernel and security kernel are not the same thing
- Relies on privilege levels for smooth and safe operation

### Privilege Levels

######Core Concepts:

- Privilege levels establish operation trust boundaries for software running on a computer
- **User mode** results in lower trust and only allows access to a small subset of system capabilities
- **Privileged** **mode** aka kernel mode, results in higher trust and allows access to more system capabilities
- The ring protection model describes a form of CPU layering that is designed to protect critical elements of a computing system

### Middleware

######Core Concepts:

- Middleware acts as an intermediary between two applications
- Middleware is a layer of software that can speak the languages of two disparate applications and thereby facilitate communication between them

### Abstraction and Virtualization

- Abstraction: refers the the underlying complexity and details of a system being hidden
- Virtualization: extend the computing example further

### Layering/Defense-in-Depth

######Core Concepts:

- Protection of an asset is best accomplished through the implementation of multiple control layers

### Trusted Platform Modules (TPM)

######Core Concepts:

- A TPM is a piece of hardware that implements an ISO standard, resulting in the ability to trust involving security/privacy
- A TPM is an independent component of a computing system and functions similarly to a black box
- Binding and sealing are important elements that help a TPM maintain integrity
  - Binding: A cryptographic operation in which data is encrypted in such a way that it is tied (BOUND) to a specific TPM's hardware/software configuration
  - Sealing: a cryptographic operation that involves encrypting data.
    - Unlike binding, sealing is not tied to the TPM's state/configuration.
    - Instead, Sealing is used to only allow the data to be decrypted in certain conditions, such as after user authentication.

## Assess and mitigate the vulnerabilities of security architectures, designs, and solution elements

######Core Concepts

- A single point of failure is something that will result in negative operation impact if realized
- Redundancy can help alleviate the risks associated with a single point of failure, and it should only be implemented where it is cost-justifiable
- Bypass controls are a potential vulnerability, and their existence creates risks
- The risks associated with bypass controls can be mitigated using segregation of duties, logging and monitoring, and physical controls
- Time-of-Check Time-of-Use (TOCTOU), aka a race condition, represents a short window between two events -- typically when something is used and when authorization for that use is checked.
- Frequent access or authorization checks can reduce the risk of race conditions
- Emanations are unseen elements leaking out of systems that might reveal confidential and valuable information if captures and analyzed with the proper equipment
- Shielding, white noise, and control zones can prevent emanations from being captured

###### Single Point of Failure

###### Reduce Risk of single point of failure

- Implement redundancy

###### Bypass Controls

- Potential vulnerability or new source of risk, but they are <u>_intentional_</u>.
- Example: needing access to admin settings of a home router, but you cant remember the password
  - Performing a factory reset of the device would allow me to enter new configuration details/credentials and set it up from scratch

###### Reduce Risk of Bypass Controls

- Bypass controls are needed, and other compensating controls should always be implemented with them to mitigate or prevent their exploitation

###### TOCTOU or Race Condition

- Time of Check // Time of Use

  - Short window of time between when something is used and when authorization or access for that use is checked
    - In that short time period, something unintended or malicious can transpire
  - AKA: race condition - a user or process attempts to 'race in' and make changes

- ###### Reduce Race conditions

  - Increase frequency of access checks, but not too often where it's annoying. Balance between security and functionality is important

**What describes a race condition** (not sure why this section was bolded and then the only thing after it is emanations...)

###### Emanations

- Manifest in the form of unseen things leaking out.

- Radio, magnetic waves, sound, light, etc.

- **Shielding**: one of the best ways to protect against unauthorized capturing of emanations

- **White noise**: strong signal of random noise

- **Control zones**: prevent access or proximity to a device

### Hardening

######Core Concepts:

- Hardening is the process of looking at individual components of a system and then securing each component to reduce the overall vulnerability of the system

###### Vulnerabilities in Systems

###### Reduce Risk in Client and Server-based systems

- Disable unnecessary services
- Install security patches
- Close certain ports
- Install anti-malware
- Install host-based firewall/IDS
- Use encryption
- Strong passwords
- Backups

**What drives hardening decisions?**

- What is this system meant to do?

### Risk in Mobile Systems

######Core Concepts:

- Mobile Device Management (MDM) and Mobile Application (MAM) solutions help organizations secure devices and the applications that run on them
- Mobile device management solutions should particularly focus on securing remote access using a VPN and end-point security as well as securing applications on the device through application whitelisting

###### Mobile Devices

###### Reduce Risk in Mobile-based Systems

- **What is the primary different between MDM and MAM?**

  - MDM software allows a security admin to perform tasks like enforcing different security controls or even wiping a device remotely
  - MAM software can secure applications that interact with corporate data.
  - MDM and MAM can be combined with policy enforcement, application of device encryption, and related polices to adequately protect mobile devices if lost/stolen

- **What are ways to reduce risk associated with mobile devices/workers?**

  - Policies

    - Acceptable Use, BYOD, training

  - Process related to lost or stolen devices

    - Involves notification of IT/ security personnel to remotely wipe

  - Remote access security

    - VPN / 2FA capabilities should be enabled by default, to prevent a mobile device from being used to connect to a remote network in an insecure manner

  - Endpoint security

    - Antivirus, DLP, and similar MDM-provisioned software should be installed

  - Application whitelisting

    - Organizations should control which apps users may install on their mobile device

### OWASP Mobile Top 10

- OWASP Mobile Top 10 adheres loosely to OWASP Top 10 methodology, with a focus on mobile apps
- M1 - Improper Credential Usage
- M2 - Inadequate Supply Chain Security
- M3 - Insecure Authentication/Authorization
- M4 - Insufficient Input/Output validation
- M5 - Insecure Communications
- M6 - Inadequate Privacy Controls
- M7 - Insufficient Binary Protections
- M8 - Security misconfiguration
- M9 - Insecure Data Storage
- M10 - Insufficient Cryptography

### Distributed Systems

######Core Concepts:

- Distributed systems are systems that are spread out and can communicate with each other across a network. The internet is a great example
- Distributed file systems are systems where files are speread across multiple hosts and made available via sharing across a network
- Grid systems are interconnected systems that are usually working together to solve a specific and usually very complex problem

What's an underlying risk to distributed file systems (DFS)?

- Providing a means for potential attackers to gain access to the corporate network and cause mayhem (data breaches, DoS, ransomware)
- DFS, takes the concept of distributed systems a step further by allowing files to be hosted by multiple hosts and shared across a network.

### Inference and Aggregation

######Core Concepts:

- Data warehouse
- Big data
  - Variety, volume, velocity
- Data mining/analytics
  - The rest of this section and example will show inference, especially unauthorized inference, can create a significant risk to an organization

- Inference and aggregation
  - **Inference**: deducing information from evidence and reasoning rather than from explicit statements
  - **Aggregation**: Collecting, gathering, or combining data for the purpose of statistical analysis

- Reduce the risk of unauthorized inference and aggregation
  - One method is 'polyinstantiation', which allows information to exist in different classification levels for the purpose of presenting unauthorized inference and aggregation (more details in Domain 8)

### Industrial Control Systems (ICS)

######Core Concepts:

- ICS is a general term used to describe control systems related to industrial processes and critical infrastructure

- 3 primary types of ICSs:

  - #### Supervisory Control and Data Acquisition (SCADA)

    - System architecture that comprises computer, networking, and proprietary devices as well as graphical interfaces for management of the entire system
    - Used to manage small and large-scale industrial, infrastructure, and facility processes

  - #### Distributed Control System (DCS)

    - Process control system that monitors, controls, and gathers data from components like controllers, sensors, and other devices typically found in large processing facilities
    - Unlike SCADA, which includes local and remote management capabilities, DCS is typically controlled locally

  - #### Programable Logic Controller (PLC)

    - Industrial computer, specifically used for the control of manufacturing processes
    - Key features include high reliability, ease of programming and diagnosis of process problems
    - Often networked with other PLC devices and SCADA systems

- Due to inherent complexity and the things they manage, ICS can be quite vulnerable to attack; the best way to reduce risk to ICS is to keep them offline -- airgap them from direct or indirect access to the internet.

### Internet of Things (IoT)

- Reduce the risk of IoT? Dont use it.

### Cloud Service and Deployment Models

###### 

######Core Concepts:

- ### Characteristics

  - **self-service**
    - resources can be provisioned immediately and automatically when needed
  - **Broad network access**
    - cloud can be accessed from anywhere
  - **Resource pooling**
    - relates to sharing three primary sources of cloud computing (processors, disk space, and the network)
    - this point to significant economies of scale and value
  - **Rapid elasticity and scalability**
    - Relaters to how quickly compute, storage, and network can be increased/decreased in the cloud
  - **Measured service**
    - cloud provider tracks resources usage
  - **Multitenancy**
    - means everybody has access to the cloud - its open to the public - and cloud resources potentically be shared with anybody

- ### Cloud service models

  - **IaaS - Infrastructure**
    - deploy virtaulized INFRASTRUCTURE, including compute, storage, and networking components
  - **PaaS - Platform**
    - PLATFORM which provides the services and functionality for customers to develop and deploy applications. In between IaaS and SaaS
  - **SaaS - Software**
    - offered by a CSP which is available on demand, typically via the internet
  - **CaaS - Containers**
    - automates the hosting and deployment of containerized software apps and allows dev teams to focus on more important matters.
  - **FaaS - Function**
    - serverless - implies an architecture where devs dont have to worry about dealing with server or other infrastructure
    - microservice - very particular, self-contained services that provide specific business functionality
    - AWS Lambda is one of the earlist examples

- Deployment models

  - Public, Private, Community, Hybrid

- _Protection and privacy of data in the cloud should be carefully considered_

### Compute in the Cloud

######Core Concepts:

- Hypervisor, aka virtual machine manager (VMM), is software that allows multiple OS to share the resources of a single physical machine
- A VM is emulated computing

### Cloud Forensics

######Core Concepts:

- Focus is on the forensic process in cloud computing environments
- Typically, more complex than on-premises forensic investigations
- Virtual disks and VM images are often analyzed as part of cloud forensics

On premises computing investigations is straightforward and primarily involves securing the scene, capturing data that may reside in volatile memory/storage, and making bit-for-bit copies of HDD and other non-volatile storage

Cloud forensics process can be much more complex. Public cloud environments involve multiple customers sharing the same physical infrastructure, including HDD, physical access to the equipment and storage devices that may contain relevant info to the investigate is typically not possible or allowed to be accessed

**SaaS**:

- consumers must rely entirely on CSP

**PaaS**:

- For underlying infrastructure, consumers must rely on entirely on CSP

- Consumer is responsible for any application layer code they deployed and application logging

**IaaS**:

- consumers can perform forensic investigations on their VMs
- Investigation of network traffic, access to snapshots of memory, or the creation of a hard disk images may require investigative support by the CSP

### Cloud Computing Roles

######Core Concepts:

- Multiple computing roles relate to cloud computing:

  - #### Cloud consumer (customer)

    - Individual or organization who is accessing cloud services

  - #### Cloud provider

    - Organization that is providing cloud services/resources to customers

  - #### Cloud partner

    - Organization which supports either the cloud provider or customer (ex. Cloud auditor or cloud service broker)

  - #### Broker

    - Carrier, architect, administrator, developer, operator, services manager, reseller, data subject, owner, controller, processor, steward (why so many titles?)

  - Cloud consumer is always accountable for their data stored in the cloud

  - Responsibility can be delegated to other cloud computing roles

- **Data controller = owner of data = cloud customer = _accountable_**

- **Data processor = processor of data = cloud provider or other agent of the customer = _responsible_**

### Cloud Identities

######Core Concepts:

- 3rd party identity provider is a trusted organization that manages user identities and related attributes for purposes of authentication and authorization
- Identity federation involves protocols, standards, practices, and policies that support identity portability and trust relationships among unaffiliated resources and organizations
- SPML
  - enables the automation of adding users to multiple cloud services (DEPRECATED)
- SAML (**Security Assertion** Markup Language)
  - SAML is an XML based, OASIS standard that utilizes security tokens that contain assertions about a user
  - SAML facilitates service requests made by users to service providers, which result in SAML assertions allowing the user access to the service
- OAuth (Authorization)
  - is an open-standard protocol that typically works in conjunction with openID (authentication). OAuth provides users and applications with "secure delegated access" via access tokens versus credentials. OAuth enables disparate resources to securely interact in a manner that ultimately allows a client to access data owned by a resource owner

- On-prem IAM solutions include Microsoft AD and LDAP based
- Clous-based IAM solutions include those offered by Amazon, Google, and many other cloud vendors
- Identity as a Service IDaaS refers to cloud based IAM services
-

### Cloud Migration

######Core Concepts:

- Cloud migration involves benefits and risks that should be carefully considered
- One significant risk of cloud migration is vendor lock-in
- Security in the cloud should be understood thoroughly, and organizations should work closely with the cloud service provider to implement security that follows best practices

### Edge Computing

Distributed computing approach that can reduce latency, speed up response times, and increase bandwidth availability.

**Ingress**:

- Ingress traffic is traffic **entering** a network. In edge computing, it's often generated by users who are accessing services that are hosted at the edge.

**Egress:**

- Egress traffic is traffic **exiting** a network. In edge computing, this is generally data sent from services at the edge, either back to users, or to another network.

**Peering:**

- Is the **interconnection** between separate networks for exchanging traffic. This approach allows them to exchange traffic without going through the internet.

**SASE**:

- Sassy, Suite of tech that is often looked upon as the future of wide area networks (WANs).
- **Combines** network security and WAN into a cloud-based service. It aims to get data/services as close to the end users as possible, while still maintaining robust security

### XSS and CSRF

######Core Concepts:

- ### XSS:

  - **Stored/persistent**

    1. Baddie discovers vulnerable website
    2. Baddie injects malicious code into webpage
    3. Victim's browser downloads and executs code
    4. Victim's info is sent to Baddie

  - **Reflected (most common)**

    1. Baddie sends URL (containing code) to Victim
    2. Victim clicks on URL
    3. Vulnerable website reflects code
    4. Victim's browser executes code
    5. Victim's info is sent to Baddie

  - **Target**: user's browser

- ### CSRF

  1. Baddie forges a request for fund transfers
  2. Baddie embeds Request in hyerplink and sends to Victim
  3. Victim clicks link sending request to bank website
  4. Bank website, which Victim is logged into, acts on request sending funds to Baddie

  - Relies on **persistence facilitated by cookies** in browsers

  - **Target**: web server

### SQL Injection

######Core Concepts:

- Utilizes SQL code/commands
- Input validation is the best method to prevent SQL injection attacks

### Input Validation

######Core Concepts:

- No input validation can lead to numerous web apps vulnerabilities being exploited

- Server-side input validation reduces web-based vulnerabilities and the risk of XSS/SQL Injection attacks from succeeding

- Allowlist input validation only allows acceptable input

## Select and Determine Cryptographic solutions

### Intro to Cryptography

######Core Concepts:

- Most critical aspect of cryptography is key management (PROTECT THE KEY)
- Cryptographic system can provide up to 5 services:
  - confidentiality
  - integrity
  - authenticity
  - nonrepudiation
  - Access control
- Cryptography is used extensively

### Cryptographic Terms

######Core Concepts:

- Cryptography involves its own nomenclature

- Important terms to be familiar with include:

  - #### Initialization vector (IV) aka 'nonce'

    - An IV, or noncem is a random number that is used in conjunction with the key and fed into a cryptographic algorithm when encrypting plaintext

  - #### Confusion

    - Focuses on hiding the relationship between <u>**the key** and the resulting ciphertext.</u>
    - Suggests that if 1 bit of the **KEY** is changed, then about half of the bits in the cipher text should change

  - #### Diffusion

    - Focuses on hiding the relationship between <u>**plaintext** and resulting ciphertext</u>
    - Similar to confusion, but focused on **plaintext**
    - Suggests that if a single bit of the plaintext is changed, the approximately half of the bits in the cipher text should change

  - #### Avalanche

    - To determine the security/effectiveness of an algorithm
    - Looks at the degree of confusion and diffusion that an algorithm provides
    - **Ideal case**: single bit change to either key/plaintext == at least 50% the bits in the ciphertext

  - #### Key space

    - Refers to the unique number of keys that are available based on the length of the key. IE a 2-bit key has total of 4 possible keys

### Substitution and Transposition

######Core Concepts:

- Encryption involves methods known as substitution and transposition

  - **Substitution**: character are replaced
  - **Transposition**: characters are rearranged

- Encryption is accomplished through the manipulation of bits via synchronous and asynchronous means

  - ##### Synchronous

    - Timing element involved
    - Encrypted / decrypted requests are performed immediately

  - ##### Asynchronous

    - Dictated by some other element or entity that requires input
    - Encrypted / decrypted requests are processed in batches (queue)

- Patterns must be avoided

- When implemented and used correctly, one-time pads are the only unbreakable cipher systems

- Bits are encrypted and decrypted as stream ciphers or block ciphers

  - ##### Stream ciphers:

    - Plaintext bits that need to be encrypted are combined with bits generated by a **keystream generator**, which is seeded by a crypto variable
    - Bits are combined using "exclusive or" XOR, which helps create the needed confusion and diffusion to make stream cipher secure
    - The result from each XOR operation becomes the ciphertext. Most common: RC4

  - ##### Block ciphers

    - Encrypt data in chunks that we call blocks. AES has a 128 bit block size
    - Plaintext blocks, like letter GUB / BIN, are processed by a block cipher that has been seeded by a crypto variable
    - The output of each operation results in chunks of cipher texted, JXE, ELQ, and the S as V
    - Each block is processed individually

Stream ciphers provide a clear speed advantage over clock mode ciphers, because they work with one bit at a time as opposed to block ciphers that need to fill blocks and do creative operations with those blocks

### Steganography and Null Ciphers

### Symmetric Cryptography

- Advantages
  - Fast
  - Strong
- Disadvantages:
  - key distribution and sacalabilty are major disadvantages
  - Out-of-band communication can facilitate key distribution
  - Know symmetric algorithms from weakest (DES) to strongest (AES

###### Out of band key distribution

- one of the biggest challenges is key distribution, because the sender and receiver of an encrypted message must have the same key
- Sending the key via the same communciation channel as the message itself is ineffective because the key could easily be intercepted and used to read the encrypted message
- Some type of out of band distribution - or more secure methods - are necessary. might mean the two parties meet someplace and exchange the key, sending a letter, phone call,

### Asymmetric Cryptography

######Core Concepts:

- Utiilizes key pairs consisting of public key and private key
- 2 primary types of hard math problems
  - factoring
  - discrete logarithms

- **Advantages**:
  - solves the key exchange problem associated with symmetric cryptography
  - enables digital signatures, certificates, authenticity, and nonrepudiation (origin/delivery)
  - Solves scalability
- Popular asymmetric algorithms include RSA (uses factoring) and Elliptical Curve (ECC, uses discrete logarithms)

### [3.6.7 ]Hybrid Key Exchange

######Core Concepts:

- **Diffie-Hellman Key Exchange** (uses discrete logarithms) is an asymmteric algorithm used primarily for symmetric key exchange.
- Hybrid cryptography blends the advantage of symmetric cryptography -extremely fast- with the advantage of assymmetric cryptography-solves the key distribution problem

##### Diffie-Hellman Key Exchange Protocol

_SESSION KEYS_

The value and use of Diffie-Hellman Key Exchange Protocol

- Symmetric cryptography is the only type that can host the speeds required for being able to encrypt/decrypt fast enough for the apps that require cryptography today.
- For example, with a VPN, only symmetric key cryptography can be used to efficiently support the amount of data traversing the network
- **Session keys**:
  - symmetric keys used for specific sessions – they are only used for one session, and when a new session is started a new session key will be generated.
  - new session = new key
  - **<u>How it works?</u>**
    1. A's and B's systems each generate a random number, 7 and 3, in this example. THe numbers are essentially a secret, as they dont know each other's numbers
    2. On each end, the random is multiplied by the same number, in this example 2. As a result - Alice's number is now 14, bob's is 6. In practice, the number is mathematically complex
    3. At this point, the numbers are mathematically related. Alice's and Bob's systems send the numbers to each other; alice's system sends 14 to bob. bob sends 6 to Alices
    4. At this point, they realte the number they received back to the original random number through a multiplication operation. So, Alice multiples the number she recieved (6) with her original number 7, and bob does the same (14 x 3)
    5. quick math shows the result of the mathematical operation to be 42 - the key- on both sides

###### hybrid cryptography

- sharing a symmetric key securely by way of encrypting it with Bob's public key.
- Bob will decrypt with his private key
- That decryption reveals the symmetric key which matches the symmetric side of the encryption


### Message Integrity Controls

######Core Concepts:

- Message integrity checks (MIC) help to ensure the integrity of a message between the time it is created and the time it is read
- a MIC works by creating a representation of the message, which is sent with the message
- Message integrity checks are based upon math, some more complex– and therefore more effective– than others
- The use of simple math can result in a collision, meaning two different messages can result in the same representation
- Hashing is a very effeective as a MIC and works the same way, regardless of the lenghth of input; the result is always a fixed length digest, based on the hashing algorithm used
- The birthday paradox best illustrates how collisions occur and why they should be avoided to maintain integrity

Remember: 5 cores services that can be provided by cryptograpy:

CIA + NA

- **C**ondifidentiality
- **I**ntegrity
- **A**uthenticity (proof of origin)
- _Non-repuditation_
- _Access control_

**Message integrity checks (MICs)** are designed to ensure that messages remain unchanged from the time of creation to the time they're read


Hashing algorithms are much more sensitive to small bit changes and much more resistant to collisions

- Therefore hashing is much more effective as integrity control mechanisms

###### Hashing

- **Fixed length digest**
  - Any length input always equals the same length output
- **One-way**
  - not possible to determine the input of a hashing algorithm by inspecting the output
- **Deterministic**
  - The same inut always equals the same output. same message hashed 2x will be the same hash value
- **Calculated on entire message**
  - message digest must calculate entire message, not just part of it
- **Uniformly distributed**
  - Good hashing function should map the inputs as evenly as possible over its ouput range. In other words, there should be equal probability of any hash value being generated
- **Collision resistant**
  - it should be very hard to find two inputs that hash to be the same output

###### Hashing Algorithms

MD5 128 bit

Sha1 160

Sha2/3 224 to 512 bit

Longer digest = less opportunity for collisions

### Digital Signatures

######Core Concepts:

- digital signatures provide three services:
  - **integrity, authenticity, nonrepudiation**
- Digital signature uses include having the same legal signficance as a written signature, code signing to verify the integrity and authenticity of softare, and nonrepudiation (of origin and delivery)

### Digital Certificates

######Core Concepts:

- Digital certificates bind an individual to their public key
- All certificate authorities conform to the **X.509** certification standard
- The 'root of trust' or 'trust anchor' is the foundation of all digital certificates and is represented by a root certificate authority.
- Digital certificate best practices suggest that public/private key pairs be periodicailly replaced, which means the associated digital certificate is also replaced
- **when a private key has been compromised, a digital certificate should be revoked by the issuing certificate authority**
- With certificate pinning, when a certificate from a web server is trusted, each subsequent visit to the site does not include a request for a new copy of the certificate

###### How can we be certain we have someone's public key?

The CA signs an individual certificate with the CA's private key, thereby ensuring the integrity and validity of the certificate and public key being issued

###### Revocation Confirmation Methods

- Certificate Revocation List (CRL) (**OLD METHOD**)

  - contact a CA and ask if a particiulare certificate has been revoked.
  - in return, the CA would send a full list of revoked certificates, which can be alot

- Online Certificate Status Protocol (OSCP)

  - systems queries the CA, and the CA will reply yes or no

###### Certificate Life Cycle

- Enrollment
  - request submitted for a certificate to a CA
- Issuance
  - identity proofing is done to information validity is confirmed. Certificate is stored in certificate store after it's issued
- Validation
  - Validity of the certificate is typically automatically confirmed with the issuing CA
- Revocation
  - A certificate may be revoked for any number of reasons and will be added to the certificate revocation list
- Renewal
  - All certificates are issued with an expiration date

###### Certificate pinning

### Public Key Infrastructure (PKI)

######Core Concepts:

- Public Key Infrastructure (PKI) is the basis for keys to be distributed and owners of public keys to be verified
- The standard used to create all digital certificates is X.509
- PKI consists of serveral components: Certificate Authority (CA), Registration authority (RA), intermediate/issuing CA, certificate DB, certificate store
- The root of trust in any PKI is the CA, which ultimately issues certificates

### Key Management

######Core Concepts:

- _Proper key management is paramount to the security of any cryptographic system_

- **Kerchkoffs' principle**

  - a cryptosystem should be secure even if everything about the system, except the key, is public knowledge

- Key management activities:

  - ###### Generation/creation

    - Fully automated process
    - Keys randomly chosen from the entire available key space
    - Asymmetric keys are much longer than symmetric keys

  - ###### Distribution

    - Practice of securely distributing keys, including:
      - out ouf band distrubition
      - key wrapping using key encrpyting keys (KEK)

  - ###### Storage

    - One of the most critical aspects. Two types of systems:
      1. Trusted Platform Module (TPM)
      2. Hardware Security Module (HSM)

  - ###### Change/rotation

    - how often keys should be replaced

  - ###### Disposition/destruction

    - refers to how keys are handled, especially in instances where data in the cloud is concerned. Two primary methods of key disposition/destruction:
      - crypto shredding
      - key destruction

  - ###### Recovery

    - refers to techniques used to recover a key. Three primary techniques exist:
      1. Split-knowledge
      2. Dual control
      3. Key escrow

### S/MIME

Secure/Multipurpose Internet Mail Extensions - aka S/MIME

######Core Concepts:

- S/MIME is a standard for public key encryption and provides security services for digital messaging applications
- S/MIME requires the establishment or utilization of a public key infrastructure (PKI) in order to work properly

SMIME Is a standard for public key encryption and provides a number of security services for digital messaging apps. basic security services offered:

- Authentication
- Nonrepudiation of origin
- Message integrity
- Confidentiality

Also offers optional security services including:

- Signed receipts, security labels, secure mailing lists, extended method of identifying the signer's certificates

---

## Understand methods of Cryptanalytic attacks

### Cryptanalysis

######Core Concepts:

- cryptanalysis is a multidisciplinary science
- 2 primary types of cryptanalysis attacks:
  - cryptanalytic attacks
  - cryptographic attacks
- The main purpose of cryptanalysis is to deduce or figure out the key (since in cryptography, everything is known except for the key)

### Cryptanalytic Attacks Overview

######Core Concepts:

- the primary goal of a cryptanalysis attack is to determine the key
- brute-force attack involves trying every possible key until the correct key is identified; typically not effective unless the key length is very short
- **cryptanalytic** attack: ciphertext only, known plaintext, chosen plaintext, chosen ciphertext
- linear and differential attacks use complicated math to deduce the key;
  - **linear**: uses a known-plaintext approach
  - **Differential**: uses a form of chosen-plaintext attack
- Factoring attacks attempt to factor a very large prime number, to determine the private key, and are utilized agains the RSA algorithm (which uses factoring as the underlying hard mathematical problem)

###### Cryptographic Attacks

######Core Concepts:

- the goal of cryptographic attacks can vary
- multiple types of attacks including popular ones likes mitt, replay, side-channel, social engineering, and ransomware

## Apply security principles to site and facility design

### Intro to Physical Security

######Core Concepts:

- physical security seeeks to protext an organization from the outside to the inside
- primary goal is the safety and protection of human life
- physical security goals
- threats to physical security

### Layered Defense Model

######Core Concepts:

- the best physical security involves a layered, or defense-in-depth approach

- physical security must always consider the safety and protection of people

## Design site and facility security controls

### Security Survey

######Core Concepts:

- security, or site, surveys are an extension of risk management and involve: threat definition, target identification, and facility characteristics

- Crime Prevention Through Environmental Design (CPTED) is a specific professional practice that outlines guidelines and best practies regarding design of buildings/structures

### Perimeter

######Core Concepts:

- perimete controls are an important elemtn of physical security, including things such as landscaping, grading, fences, gates, and bollards
- Like access points (doors) to a building, the less access points through a fence, the better the security of the perimeter

### CCTV

- CCTV cameras serve primarily as a DETECTIVE control
- CCTV cameras also DETER and MONITOR, and it can be used for security audits

### Passive Infrared Devices

- motion sensor that detects motion by picking up on infrared light

- Passive IR devices are very sensitive to temperature chnages

- Passive IR device must continonually recalibrate themselves based on ambient temperature

### Lighting

######Core Concepts:

- external lighting server as a detterant and as a safety precaution
- External lighting allows camera systems to have better visibilty of the surrounding area

### Doors and Mantraps

######Core Concepts:

- door composition and frame construction are significant
- mantraps typically consist of a double set of doors or a turnstile and prevent piggybacking/tailgating
  - prevents

### Locks

######Core Concepts:

- locks are a delay control, do not prevent access
- Two types of locks
  - Mechanical
    - Key
    - Combination
    - Magnetic
  - Electronic
    - Proximity/RFID
    - Combination
    - Biometric

### Card Access/Biometrics

######Core Concepts:

- Card access is inexpensive compared to biometics. More prone to abuse and are not foolproof though

- Biometric locks more prevalent but employees may not desire to use them due to privacy concerns
- The security of a combination lock is dependent on the complexity of the combination

### Windows

- often represent a point of vulnerability
- shock and glass break sensors can help detect breaches
- sensors that detect sound and frequencies are useful in quiet environments
- shock sensors detect vibrations related to glass breaks and are useful in noisy environments
- glass break sensors are essentially microphes that listen for the sound of glass breaking

### Walls

######Core Concepts:

- composition and height of walls is important for the sake of strong physical security

### ATM Skimming

######Core Concepts:

- Skimming utilizes disguiesed technooligy to steal information

### Power

######Core Concepts:

- Power disruption of any kind can seriously impact the viabilitiy of an organization
- UPS units, systems, and generator can provide a clean, predictable, and consistent power in the event of an outage or other power degredation
  - **Blackouts**
    - No power for long period of time (seconds, hours, days)
  - **Fault**
    - No power for short period of time (ms)
  - **Brownout**
    - Not enough power for a long period of time
  - **Sags/dips**
    - Not enough power for short period of time (ms)
  - **Surges**
    - Too much power for long period of time
  - **Spikes**
    - Too much power for short period of time (ms)

### HVAC

######Core Concepts:

- an important element of physical security is temp and humidity control, for the sake of people, equipment, and areas of a building that may require specific temperature and huimidity setting
- air quiality is an equially important consideration
- positive pressuraization help ensure that contaminiatns do notenter a building, room, or space

### Fire

######Core Concepts:

- Requires fuel, oxygen, and heat

  - If any of the three are removed, the fire goes out

- Fire and the risk of fire should be prevented via complete control of prevention, detection, and correction

- **Fire detectors**

  - ###### Flame

    - detects infrared and UV light created by a flame

  - ###### Smoke

    - Ionization
      - detected have a small amount of radioactive material embedded in the sensor that ionizes particles that flow between the 2 metal plates
      - if smoke particles enter the chamber, the ionization process is interrupted and fire will be detected
      - **This type of detected responds more quickly to flaming/fast fires**
    - Photoelectric/Optical
    - Dual
    - VESDA

  - ###### Heat

- **Water based fire suppression systems:**

  - **Wet pipe**
    - pipes are wet, filled with pressurized water
    - risk of leaks, when used in freezing locations, pipes can freeze/burst
  - **Dry pipe**
    - do not always have pressurized water in the pipe
    - Typically filled with pressurized gas
    - Sometimes combined with pre-action system, when triggered activates the flow of water to fill the pipes
  - **Pre-action**
    - Advantages:
      - due to detection systems, concerns of water damage due to false activations can be eliminated
      - Water is held back until detectors in the area are activated, thus, other floors would not be showered
  - **Deluge**
    - involves a massive amount of water flowing at once
    - only to be used when immediate extinguishment of ther fire is required, like in a fireworks or explosives factory, where a fire == catastrophe

- **Gas based fire suppression systems**

  - INERGEN
  - Argonite
  - FM-200
  - Aero-K

- Fire extinguishers

- CO2 is noncorrosive, but must be used with caution if people are around

## Manage the Information System Lifecycle

​
