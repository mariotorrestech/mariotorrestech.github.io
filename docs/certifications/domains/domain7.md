#### Domain 7

# Security Operations

##### Overview:

*Domain 7 is where the rubber meets the road and focuses on integrating security within organizational operations.* Often, this integration is in the form of processes that are put in place and configured to ensure that systems remain secure. Security operations are the day-to-day activities that the security function performs to support the entire organization in achieving its goals and objectives.

## Understand and Comply With Investigations

### Securing the Scene

###### Core Concepts:

- Securing the scene is an essential and critical part of every investigation.
- Securing the scene might include any/all of the following:
    - Sealing off access to the area where a crime may have been committed.
    - Taking photos.
    - Documenting the location of evidence.
    - Avoiding touching anything.

### Evidence Collecting and Handling

###### Core Concepts:

- The forensic investigation process should include, among other things, the identification and securing of a crime scene, proper collection of evidence that preserves its integrity and the chain of custody, examination of all evidence, further analysis of the most compelling evidence, and final reporting.
- Evidence collection should be guided by early establishment and maintenance of the chain of custody.
- The chain of custody focuses on who handled what evidence, when, and where, and its primary focus is control, which implies integrity.
- Sources of information/evidence: oral/written statements, written documents, computer systems, visual/audio recordings, photos, surveillance footage, etc.
- MOM = Motive, Opportunity, Means.

##### Sources of Information

- Oral/written statements.
- Written documents.
- Computer systems.
- Visual/audio.

##### Types of Evidence

- **Real evidence**
    - Tangible physical objects.
- **Direct evidence**
    - Speaks for itself and requires no inference.
- **Circumstantial evidence**
    - Also known as indirect evidence.
    - Suggests a fact by implication or inference and can prove an intermediate fact (e.g., defendant being near the computer storage area that was broken into).
- **Corroborative evidence**
    - Supports other facts.
- **Hearsay evidence**
    - Witnesses who were not present.
- **Best evidence rule**
    - Original evidence rather than a copy or duplicate of the evidence should be entered as evidence.
- **Secondary evidence**
    - A reproduction or substitute for an original document or item of proof.

###### Motive Opportunity Means (MOM)

- What might have motivated the suspect? Did the suspect have the opportunity to perpetrate the crime? Did the suspect have the means?

### Locard's Exchange Principle

###### Core Concepts:

- Locard's exchange principle: with every crime, something is taken and left behind.

### Digital/Computer Forensics

###### Core Concepts:

- Digital forensics is the scientific examination and analysis of data.
- Live evidence is data that is stored in a running system in places like RAM, cache, buffers, etc.
- Forensic copies refer to identical, bit-for-bit copies of a digital media source, like a HDD.

### Chain of Custody

uCore Concepts:

- The primary focus of the chain of custody is control of evidence to maintain integrity for the sake of presentation in court.

- Must be established immediately and maintained.

### Five Rules of Evidence

###### Core Concepts:

- Five rules of evidence state that evidence should be:
  - **Authentic**
    - Not fabricated or planted and can be proven so through crime scene photos or things like bit-for-bit copies.
  - **Accurate**
    - Not been changed or modified — evidence has integrity.
  - **Complete**
    - Evidence must be complete, and all parts presented.
  - **Convincing/Reliable**
    - Evidence must be conveyed in a manner that allows anybody to understand what is being presented.
  - **Admissible**
    - Accepted as part of a case and allowed into the court.

### Types of Investigation

**Criminal**

- Deals with crimes and oftentimes with accompanying legal punishment. Convictions often lead to time in jail as well as criminal record. These are conducted by law enforcement at the state, local, and federal level.
- Primarily law enforcement with support from the organization.

**Civil**

- Deals with disputes between individuals or organizations, and whichever party is found guilty usually pays a fine or other monetary penalty as well as related court costs.
- Organizations, individuals, and their attorneys.

**Regulatory**

- Deals with violations of regulated activities.
- Associated regulatory body.

**Administrative**

- Focus on internal violations of organizational policies and incidents identified by an organization.
- The organization.

## Conduct Logging and Monitoring Activities

### Security Information and Event Management (SIEM)

###### Core Concepts:

- Security Information and Event Management (SIEM) systems ingest logs from multiple sources, compile and analyze log entries, and report relevant information.
- One major advantage: combining and correlating log events between disparate systems for suspicious activity.
- SIEM intelligence allows significant amounts of logged events and analysis and correlation of the same to take place very quickly.
- **Aggregation**
    - Events logged throughout the network can all be brought under one umbrella.
- **Normalization**
    - Logs are normalized, because different systems log events using different formats. Deduplication.
- **Correlation**
    - Seeks to line up events and determine which one of them alone and in combination might be important/indicative of problems.
- **Secure storage**
    - The concept where the SIEM keeps a copy of all logged events from each device. Designed to store data for long periods of time.
- **Analysis / Reporting**
    - Refers to the rules that have been put in place, looking at data related to the same, and taking action when appropriate.

###### Threat Intelligence

- Encompasses threat research/analysis and emerging threat trends.

###### User and Entity Behavior Analytics (UEBA)

- Analysis engines are typically included with SIEM solutions/subscriptions.

### Continuous Monitoring and Tuning

###### Core Concepts:

- After a SIEM is set up, configured, tuned, and running, it must be routinely updated and continuously monitored to function most effectively.
- Effective continuous monitoring encompasses technology, processes, and people.

### Security Orchestration, Automation, and Response (SOAR)

Focuses on 3 key areas:

- **Threat and vulnerability management**.
- **Incident response**.
- **Security operations automation**.

## Perform Configuration Management (CM)

### Asset Inventory

###### Core Concepts:

- Provisioning relates to the deployment of assets — hardware, software, devices, and so on — within an organization.
- Part of provisioning should include maintaining and updating a related asset inventory database anytime an asset is added or removed.
- Assets should be managed as part of an overall asset management life cycle.

### Configuration Management

###### Core Concepts:

- Configuration management is an integral part of secure provisioning.
- Configuration management relates to the proper configuration of a device at the time of deployment.
- Policies, standards, baselines, and procedures inform configuration management.
- Hardening should be considered as part of the configuration management process.
- Automated provisioning tools can help ensure consistency with the configuration and deployment process and save time.

## Apply Foundational Security Operations Concepts

###### Core Concepts:

- Implementation of foundational security operations concepts can significantly improve security within an organization.
- Foundational security operations concepts include:
  - **Need to Know**
    - Restricts a user's knowledge (access to data).
  - **Least Privilege**
    - Restricts a user's actions/privileges.
  - **Separation of Duties (SoD) and Responsibilities**.
  - **Privileged Account Management (PAM)**.
  - **Job Rotation**.
  - **Service Level Agreements (SLA)**.

## Apply Resource Protection Techniques

### Protecting Media

###### Core Concepts:

- Media management should consider all types of media as well as short and long term needs.
- Mean Time Between Failures (MTBF) is an important criterion to consider when evaluating storage media, especially where valuable or sensitive information is concerned.
- Media protection techniques consider media and media management needs and incorporate several tools for the sake of protection of media.

## Conduct Incident Management

### Incident Response Process

###### Core Concepts:

- Incident response is the process used to detect and respond to incidents.
- **Event** = observable occurrence of something.
- **Incident** = an adverse event.
    - Not all events are incidents.
- Incident response process includes:
  - **Preparation**
    - Critical as it helps anticipate the following steps.
    - Develops the IR process, assigning IR team members, and everything related to what happens when an incident is identified.
  - **Detection**
    - The goal: identify an adverse event — an incident — and begin dealing with it.
  - **Response** (IR Team)
    - After an incident is detected, the IR team should be activated. Impact assessment is one of the first steps.
  - **Mitigation** (containment)
    - In addition to an impact assessment, the IR team will attempt to minimize/contain damage or impact from the incident.
  - **Reporting**
    - Occurs through the IR process.
    - One person should take on the role to update all stakeholders as to not distract the response.
  - **Recovery** (return to normal)
    - The goal: start returning things to normal.
  - **Remediation** (prevention)
    - In parallel with recovery, remediation is taking place.
    - The goal: implement fixes/improvements to systems to prevent similar incidents.
  - **Lessons Learned** (improve process)
    - Take a step back and view the situation to an incident.
        - What process can be put in place?
        - How did our organization get here?
        - What can be done differently to improve how we run and protect our organization?

## Operate and Maintain Detective and Preventative Measures

### Malware

###### Core Concepts:

- Malware is malicious software that negatively impacts a system.
- Virus, worm, logic bomb, trojan horse, polymorphic, ransomware, rootkit, zero-day.

### Anti-Malware

###### Core Concepts:

- Anti-malware software designed to prevent malware from being triggered.
- Policy and user training and awareness can help prevent malware outbreaks.
- **Signature-based** anti-malware software can also help prevent malware outbreaks.
- **Heuristic** anti-malware software looks at the behavior of code or a file to help identify malware.
    - **Static**
        - The scanner scans code in files (white box).
    - **Dynamic**
        - The scanner runs executable files in a sandbox to observe their behavior.

## Implement and Support Patch and Vulnerability Management

### Patch Management

###### Core Concepts:

- Patch management helps create a secure environment by fixing — patching — security flaws and vulnerabilities in systems.
- Patching only secures a system against known vulnerabilities.
- Change management should be part of a patch management program.
- Determining patch levels can be done via:
  - **Agent**
    - Update software (agent) installed on devices.
  - **Agentless**
    - Remotely connect to each device.
  - **Passive**
    - Monitor traffic to infer patch levels.
- Deploying patches can be done manually or automatically.

## Understand and Participate in Change Management Processes

### Change Management

###### Core Concepts:

- Change management ensures that changes are made in a deliberate manner.
- The change management process includes multiple steps that build upon each other.

## Implement Recovery Strategies

### Failure Modes

###### Core Concepts:

- Failure modes refer to what happens in an environment when something fails.
- Three failure modes:
  - **Fail-soft (open)**
    - Fail into a state of less security.
    - A firewall allowing all traffic through if it fails.
  - **Fail-secure (closed)**
    - Fail into a state of the same or greater security.
    - A firewall blocking all traffic if it fails.
  - **Fail-safe**
    - Fail-safe prioritizes the safety of people.
    - Doors that secure a facility unlock automatically in the event of a fire alarm going off.

### Backup Storage Strategies

###### Core Concepts:

- Backup strategies are driven by organizational goals and objectives and typically focus on backup and restore time as well as storage needs.
- **Archive bit:**
  - Metadata that indicates the status of a backup relative to a given backup strategy.
    - 0 = no changes to file or no backup required.
    - 1 = file has been modified or backup required.
- Backup strategies:
  - **Incremental**
    - Only the changes (new/modified files) since the last backup are backed up each evening.
  - **Differential**
    - Changes since last full backup, including all previous days since last full.
  - **Full**
    - All data.
  - **Mirror**
    - An exact copy of a data set is created, and no compression is used.
- Backup rotations refer to different types of tape backup strategies.
- Reasons for rotating backups include when a given tape is used, how long a tape is retained, and restoration requirements.
- A backup checksum is also known as a cyclic redundancy check (CRC). A CRC ensures the integrity of data through a bit of math and can be used anywhere data resides.

### Spare Parts

###### Core Concepts:

- Spare parts strategies include:
  - **Cold spare**
    - Parts sitting on a shelf, perhaps in a storage room.
    - If the primary part fails, the system will go offline until the needed spare part can be retrieved and installed.
    - Cold spares result in downtime, but they're also the least expensive.
  - **Warm spare**
    - Installed in a computer system, but not powered and available.
    - If the primary part fails, the system will go offline, but getting back online quickly is often a simple matter of switching over to the spare part.
    - Warm spares lead to less downtime, but this benefit costs a bit more.
  - **Hot spare**
    - Installed in a system, powered, and available.
    - If the primary part fails, the spare part instantly takes over the primary part's function.
    - Hot spares are expensive as are the systems within which they're used, but they also provide significant benefits to an organization.
- Which strategy is used is often dependent upon organizational goals and objectives.
- Key considerations include: cost, criticality.

### Redundant Array of Independent Disks (RAID)

###### Core Concepts:

- Redundant array of independent disks (RAID) refers to multiple drives being used in unison in a system to achieve greater speed or availability.
- **RAID 0**
  - Also known as Striping, provides significant speed data writing and reading advantages.
    - All about speed of read/write.
- **RAID 1**
  - Also known as Mirroring, utilizes redundancy to provide reliable availability of data.
    - All about availability through redundancy.
- **RAID 10 (1+0)**
    - Mirroring and Striping, requires a minimum of four hard drives and provides benefits of striping (speed), and mirroring (availability) in one solution; this type of RAID is typically one of the most expensive.
- **RAID 5**
    - Parity protection, requires a minimum of 3 hard drives and provides a cost-effect balance between RAID 0 and RAID 1; RAID 5 uses a parity bit, computed from an XOR operation, for purposes of storing and restoring data.
    - Attempts to strike a balance between RAID 0 and RAID 1 and provide an availability in an efficient and cost effective manner.
    - RAID 5 offers very quick read/write as well as redundancy.
    - Uses parity data — if either part of the file was lost, it could be reconstructed with the remaining part and the data in the parity data.

### Clustering and Redundancy

###### Core Concepts:

- **Clustering**: a group of systems working together to handle a load.
- **Redundancy**: typically a primary system and secondary system, with the secondary system on standby mode and ready to take over if something goes wrong with primary.
- Clustering and redundancy both include high availability as a by-product of their configuration.

### Recovery Site Strategies

###### Core Concepts:

- Recovery site strategies consider multiple elements of an organization — people, data, infrastructure, and cost, as well as factors like availability and location.
- Geographically remote and geographic disparity refer to where a recovery site is located relative to the primary site.
- Internal recovery sites are owned by the organization; external recovery sites are owned by a service provider.
- Multiple processing sites are more than one site where key business functionality is performed.
- System resilience, high availability, quality of service (QOS), and fault tolerance are achieved using recovery site strategies as well as things like clustering, redundancy, replication, spare parts, and RAID.

## Implement Disaster Recovery (DR) Processes

### BCM, BCP, and DRP

###### Core Concepts:

- A disaster is something that interrupts normal business operations.
- **BCM**
    - Business Continuity Management.
    - Process and function by which an organization is responsible for creating, maintaining, and testing BCP and DRP plans.
- **BCP**
    - Business Continuity Planning.
    - Focuses on survival of the business processes when something unexpected impacts it.
- **DRP**
    - Disaster Recovery Planning.
    - Focuses on the recovery of vital technology infrastructure and systems.

### RPO, RTO, WRT, and MTD

###### Core Concepts:

- RPO, RTO, WRT, and MTD/MAD are all measurements of time.
- **Recovery Point Objective (RPO):**
    - Max tolerable data loss measured in time.
- **Recovery Time Objective (RTO):**
    - Max tolerable time
