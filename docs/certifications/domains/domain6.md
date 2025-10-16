#### Domain 6

# Security Assessment and Testing

## Design and validate assessment, test, and audit strategies

!!! note "Overview"


    Focuses on providing assurance to stakeholders, how security is contributing to goals and objectives, and that the right level of security is built into an architecture that provides value to the organization.

    ***Ensure that security requirements/controls are defined, tested, and operating effectively*** 



### Validation and Verification

!!! note "Core Concepts"

    - Validation answers one fundamental question:

    - *Are we building the **right product**?*
    - Develop a level of confidence that business requirements are clearly understood and have been validated with the business owner
  - Cannot build the right product if it is not clearly understood what the owner wants

- Verification follows validation and asks a related and equally important question:

    - *Are we building the **product right**?*
  - Develop a level of confidence that whatever is being build is mieeting all the defined requirements. The product is being built correctly based on the requirements defined during the validation stage

  

### Effort to Invest in Testing

!!! note "Core Concepts"

    - The purpose of security assessment and testing is to provide assurance regarding the architecture, application, or system being assessed and tested
    - Assurance is provided through validation and verification
    - The effort to invest in testing should be proportionate to the value the application or system represents to the organization
    - Assessment, Testing, and Auditing strategies include:
      - **Internal**
        - testing conducted by somebody internal to the organization
      - **External**
        - somebody internal examining an external provider's controls
        - an organization asking somebody external from the company to come in and provide and unbiased examination of an app or system
      - **Third** **party**
        - customer, vendor, independent audit firm
    - The role of a security professional is to:
      - identify risk and advise testing processes to ensure risks are appropriately evaluated



## Conduct security control testing

### Testing Overview

!!! note "Core Concepts"

    - Security control testing typically includes steps that align with the phases of the application and systems development process
    - software testing includes several types of testing that build upon one another: unit testing, interface testing, integration testing, system testing



###### Examples of Testing Performed

- Planning
    - Capture related requirements to a system before any design takes place and validate the requirements have been accurately captured
- Design
    -  System, Architecture, Module, design
- Develop
    - Numerous types of testing must be perfored to confirm all controls are being implemented correctly
- Deploy
    - Moving an app from a QA/Pre-Prod/test environment to the actual PROD deployment
- Operate
    - COnfiguration management reviews can performed to ensure the product is working as inteded without its security being compromised
- Retire
    - Testing and ensuring that data has been migrated into the new system in a secure manner in addition to safely disposing it from the old one



###### Software Testing Overview

- **Unit testing**
    - Examines and tests **individual components** of an application. As specific aspects/units of functionality are finished, they can be tested
- **Interface testing**
    - as more and more individual components are built and tested, interface testing can take place. Interfaces are standardized, defined ways that units connect and communicate with each other. Interface testing server to **verify components connect** properly
- **Integration testing**
    - Focuses on testing **component groups** (groups of software units) together
- **System testing**
    - System testing tests the integrated system (**THE WHOLE SYSTEM**)

### Testing Techniques

!!! note "Core Concepts"

    - Testing techniques are broken down broadly into 2 categories
        - manual
          - performed by a person
        - automated
          - performed by an automated tool
    - Static application security testing (SAST) looks at the underlying source code of an application while the application is not running; SAST is considered white box testing, because the code is visible 
    - Dynamic application security testing (DAST) examines an application and system as the underlying code executes; DAST is consider black box testing, because the code is not visible
    - Fuzz testing is a form of dynamic testing and is premised upon chaos, to see how an application responds to complete randomness
    - Code review is considered from 2 perspectives: white/black box
    - Test types include: positive, negative, misues
    - Equivalence partitioning is testing, where specific input values are used to test from a grouping perspective (partitions of values and possible inputs)
    - Boundary value analysis is testing from a bounds perspective (lower and upper bounds of groups or partitions)



###### Runtime

- **SAST**: app not running, underlying source code is examined
    - white box 
- **DAST**: app running, focuses on the app and system as the underlying code executes
    - black box
    - **Fuzz testing** AKA *Chaos*
      - throwing randomness at an app to see how it responds
      - **Mutation** (dumb fuzzers)
        - The input is randomly changed by flipping bits or appending/replacing addtl random input
        - The fuzzer has no understanding of the input structure so it's DUMB
      - **Generation** (intelligent fuzzers)
        - new input to an app is generated from scratch based on an understanding of the file format or protocol.
        - The fuzzer must understand the input structure so it's SMART





Positive Testing

- focuses on the response of a system, baed upon normal usage and expectations. testing login works

Negative Testing

- focuses on the response when normal errors are introduced. testing bad login fails

Misuse Testing

- Perspective of someone trying to BREAK the system is applied





###### Equivalence Partitioning and Boundary Value Analysis 

- both techniques are designed to make testing more efficient
- **Boundary Value Analysis**
    - <u>Boundary</u> - finding the boundary. like where 7 is rejected but 8 characters is accepted
    - Testing can be focused on either side of the boundaries
- **Equivalence** **Partitioning**
    - Starts with the same first step (identifying boundaries) but takes it a step further  to identify partitions.
    - <u>Partitions</u> - are groups of inputs that exhibit the same behavior
      - partition 1
        - password consisting of 0-7 chars (all rejected)
      - partition 2
        - password consisting of 8-16 chars (all accepted)
      - partition 3
        - Password consisting of 17+ chars (all rejected)



### Vulnerability Assessment and Penetration Testing

!!! note "Core Concepts"

    - Vulnerability testing techniques tend to be automated and can be performed in minutes, hours, or days; penetration testing techniques tend to be manual and can take several days, depending on complexity
    - Penetration testing stages include: recon, enum, vulnerability analysis, execution, and document findings
    - Testing perspectives include: internal and external (corporate network)
    - Testing approaches include: blind, double-blind
    - Testing knowledge includes: zero/black box, partial/grey box, full/white box



### Vulnerability Management 

!!! note "Core Concepts"

    - Vulnerability management is the cyclical process of identifying, classifying, prioritizing, and mitigating vulnerabilities 

### Vulnerability Scanning

!!! note "Core Concepts"

    - Automated vulnerability scanning can help ID vulnerabilities from an organizational perspective as well as from the perspective of an attacker

- 2 primary types of vulnerability scans:

    - credentialed/authenticated scans and uncredentialed/unauthenticated scans

- Banner grabbing is a process used to ID a system's OS, apps, versions

- Fingerprinting works to ID the unique characteristics of a system through examiniation of how packets and other system-level information is formed

- interpretation and understanding of scan results is often achieved with the help of 2 tools:

    - CVE - Common Vulnerability and Exposures dictionary
    - CVSS - Common Vulnerability Scoring System

- Two types of alerts

    - False-positives
        - system claims vulnerable exists, but there is none

    - False-negatives
        - system claims everything is fine, but a vulnerability exists; false negatives are bad

  

### Log Review And Analysis

!!! note "Core Concepts"

    - log review and analysis is a best practice that should be used in every organization 

- logs should include what is relevant, be proactively reviewed, and be especially scrutinized for errors and anomalies that point to problems, modifications, or breaches

- Synchronized log event times is critical for activity correlation, especially if a breach occurs; NTP is typically used for purposes of time synchronization

  

### Limiting Log Sizes

- log file management is important
- 2 log file management methods are used:
    - circular overwrite
        - limits the max file size of a logfile by overwriting entries, starting from the earliest
    - clipping levels
        - focuses on when to log a given event, based upon threshold settings, and log filesizes are limited as a result


### Operation Testing - Synthetic Transactions and RUM

!!! note "Core Concepts"

    - Operational testing occurs while a system is operating
    - Operational testing techniques include:
        - Real User Monitoring
            - monitors user interactions and activity with a website/app
        - Synthetic Performance Monitoring
            - examines functionality and performance under load

### Regression Testing

!!! note "Core Concepts"

    - Regression testing is the process of verifying that previously tested and functional software still works after updates have been made
    - Regression testing should be performed after enhancements have ben made or after patches to address vulnerabilities or problems have been issues
    - Results of regression testing should be captured and communicated in a manner that is specific and relevant to the party reading the results– this is done using 'metrics that matter'



### Compliance Checks





## Collect security process data (ex. technical and administrative)

### Key Risk and Performance Indicators

!!! note "Core Concepts"

    - Key risk and performance indicators help inform goal setting, action planning, performance, and review, among other things
    - Key <u>performance</u> indicators (KPI) are **backward**-looking indicators and look at historical data for purposes of evaluating if performance targets were achieved
    - Key <u>risk</u> indicators (KRI) are **forward**-looking indicators and aid risk-related decision-making
    - SMART metrics are: 
        - **Specific** - results clearly stated and easy to understand
        - **Measurable** - results can be measured/have the data
        - **Achievable** - Results can drive desired outcomes
        - **Relevant** - Aligned to business strategy 
        - **Timely** - Results available when needed




## Analyze test output and generate report

### Test Output

!!! note "Core Concepts"

    - Results of security assessments and testing should include steps related to: 
        - **Remediation**
            - based upon assessments and testing, remediation steps for all identified vulnerabilities should be documented
        - **Exception handling**
            - if an identified vulnerability will not be remediated, this should be documented too, including the reason why. Example: perhaps remediation would be costly relative to the value of the asset.
        - **Ethical disclosure**
            - some identified vulnerabilities might be new discoveries and point to significant flaws/weaknesses in widley used software/hardware.



## Conduct or facilitate security audits

### Audit Process

!!! note "Core Concepts"

    - Audit approaches include:
        - **Internal**
            - Employees focused on organizational processes
        - **External**
            - Employees focusing on vendor processes 
        - **Third-party:**
            -  Independent auditors focusing on vendor processes

- Audit plans include: defining the audit objective, defining the audit scope, conducting the audit, refining the audit process



### System Organization Controls (SOC) Reports

!!! note "Core Concepts"

    - Audit standards hve matured over the years from SAS70 - SSAE 16 - SSAE 18
    - ISAE 3402 is the international standard in assurance engagements and is quite similar to SSAE 16/18 standards with slight variations



SOC audits are used to **build trust** between service organizations and their customers

- #### SOC 1

    - Reports are quite basic and focus on financial reporting risks

- #### SOC 2

    - Reports are much more involved and focus on the controls related to the **five** trust principles: 

      - Security, Availability, Confidentiality, Processing Integrity, and Privacy
      - **<u>Type 1</u>** reports focus on a **point** in time
      - **<u>Type 2</u>** reports focus on a **period** of time, covering design, and operating effectiveness
        - SOC 2 - TYPE 2 (*MOST DESIRABLE*)

    

- #### SOC 3 

    - Summarized and **sanitized** version of SOC 2 for **PUBLIC** distribution

### Audit Roles and Responsibilities 

!!! note "Core Concepts"

    Audit roles include: 

  
      - #### Executive sr management

          - Sets the **proper tone** from the top, promotes the audit process, and provides support 

      - #### Audit committee

          - Composed of members of the board/sr stakeholders to **provide oversight** of the audit program

      - #### Security officer

          - **Advise on security** related risks to be evaluated in the audit program

      - #### Compliance manager 

          - Ensure **corporate complicance with applicable laws** and regulations, profiessional, standards, and company policy

      - #### Internal auditors

          - Company employees who **provide assurance that corporate internal controls** are operating effectively

      - #### External auditors

          - Provide an unbiased and independent audit report as they are **independent** of the entity being audited

- Audit responsibility vary based upon the audit role
