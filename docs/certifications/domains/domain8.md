# Domain 8

# Software Development Security

_Application Security. Needs to be involved during an application's entire life cycle, not just at development._

## Understand and integrate security in the software development life cycle (SDLC)

### Security's Involvement in Development

#####Core Concepts:

- Security should be involved at every phase of the development life cycle

### SDLC and SLC

#####Core Concepts:

- Security should be considered at every phase of sdlc/SLC
- Risk analysis and threat modeling are very important components of the eaerly phases of SDLC/SLC
- Testing should include static, dynamic, and fuzz (a form of dynamic testing) tests
- Certification and accreditation should be performed prior to release/deployment/implemnetation

### Development Methodologies

#####Core Concepts:

- Development methodologies exist for the sake of efficient and effective code development
- Many methodologies are a reflection of the waterfall methodology
- Regardless of the methodology, security should be considered at every stage of the development process
- Methodologies can be combine to utilize the best features of each of them
- Agile scrum masters understand how all team efforts fit together and can. therefore effectively and efficiently lead activities

###### Be familiar with various development methodologies and key characteristics of each:

- **Waterfall**
    - Complete each phase of devlopments before flowing/waterfalling into the next phase
    - Does not allow a previous phase to be revisited
- **Structured Programming Development**
    - A logical programming approach that is said to be foundational to OOP
    - Structured programming places heavy emphasis on structured control flow and aims to improve clarity, quality, and development time
- **Agile**
    - Divide the development process into multiple, rapid iterations of defining, developing, and deploying - with heavy customer interaction throughout the process
- **Scaled Agile framework**
    - A version of Agile that is designed to allow large organizations with may teams to collaborate and effectively deliver software
- **Spiral Method**
    - A risk-driven development process that follows an iterative model - while also including elemnts of waterfall
    - The spiral model follows defined phases to completion and then repeats the process; this model resembles a sprial when mapped to paper
- **Cleanroom**
    - Development process intended to produce software with a certifiable level of reliability by focusing on defect prevention

###### Understand the different priorites of waterfall and agile methodologies

- Agile appears to be several waterfalls back to back, known as sprints

###### Understand the role of a scrum master in agile devlopment

### Maturity Models

#####Core Concepts:

- Like development methodologies, maturity models also help improve the development process

- Capability Maturity Model Integration (CMMI) is one of the most popular models and includes six levels of maturity

  - Level 0: **Incomplete**
      - This phase is <u>unknown and ad hoc</u>
      - Indicating that work may not be getting completed
  - Level 1: **Initial**
      - this is a <u>reactive and unpredictable stage</u>
      - Indicating that work is getting finished, but often coming in over budget and late
  - Level 2: **Managed**
      - This stage indicates that projects are <u>managed and planned.</u>
      - The tasks are performed, key metrics are taken, and the project is controlled
  - Level 3: **Defined**
      - In this phase, the organization is <u>being proactive as opposed to reactive.</u>
      - There are standards across the organization that guide programs, portfolios, and projects
  - Level 4: **Qualitatively managed**
      - This is a <u>controlled and measured stage.</u>
      - It indicates that an organization is driven by data, using it to measure performance improvement objectives. These objectives meet the needs of stakeholders and are predictable
  - Level 5: **Optimizing**
      - This phase is <u>flexible and stable.</u>
      - The organization is focused on continually improving and it is able to pivot when change and opportunity present themselves. The stability of the organization allows it to innovate and be agile

- Each level of maturity of the CMMI is defined by certain characteristics

###### SAMM

1. Initial Implementation
2. Structured Implemetation
3. Optimized Implementation

### DevOps

#####Core Concepts:

- An integrated product team is really a fancy term for DevOps: software development, operations, quality assurance (QA)
- Ideally, DevOps should include security as an integral part of the development process and be referred to as DevSecOps

### Canary Testing and Deployments

#####Core Concepts:

- **Canary** testing and deployments refer to hyperfocused testing of new application code/features by pushing out the changes to a small subset of users versus pushing out to all users
- **Smoke** testing

## Identify and apply security controls in software development ecosystems

### Software Development overview

### Code Obfuscation

#####Core Concepts:

- Obfuscation refers to hiding or obscuring something; code obfuscation refers to hiding or obscuring code to protect it from unauthorized viewing or interpretation of the logic

- Three primary types of code obfuscation

  - **Lexical**
    - Modifies the look of the code (changing comments, removing debugging info, format of code)
    - Easiest but weakest form of obfuscation
  - **Data**
    - Modifies the data structure
  - **Control Flow**
    - Modifies the flow of control through the code (reordering statements, methods, loops, and creating irrelevant conditional statements

### DBMS, Concurrency, and Lock Controls

#####Core Concepts:

- Components of DBS include: hardware, software, language (SQL), users, data
- Database terms: cols/fields = attributes; records/rows = tuples
- Foundation of a relational database is the concept of primary and foreign keys
  - **Primary keys:**
    - one ore more cols whos value uniquely identify a tuple (row) within a relational database
  - **Foreign keys:**
    - one or more cols whose values in a table refer to the primary key in another table
  - **Concurrency**
    - abiity for multiple processes to access or change shared data at the same time
  - Locks prevent data corruption when multiple users try to Write to the database simultaneously
  - ACID: Atomicity, Consistency, Isolation, Durability

### Metadata

#####Core Concepts:

- Data about other data

### Development Ecosystems

#####Core Concepts:

- CI/CD, SOAR, and SCM are development ecosystems
- Though the focus of each is different, they each share common characteristics

## Assess the effectiveness of software security

### Software Security Assessment Methods

#####Core Concepts:

- Software security effectiveness can be determined through auditing and logging of changes and risk analysis and mitigation, among other methods
- Review domain 6 for more details

## Assess security impact of acquired software

### Acquiring Software

#####Core Concepts:

- Acquiring software should be taken as seriously as developing softwarwe, and security should be considered at every step in the process
- Software assurance phases for acquisition including:
    - Planning/requirements
    - Contracting
    - Acceptance
    - Monitoring
    - Etc.
- Common ways to acquire software is via: Commercial-off-the-shelf (COTS), open source, third party, managed services

## Define and apply secure coding guidelines and standards

### Secure Coding Guidelines

- OWASP, NIST, CIS offer secure software development frameworks and resources
- Covert channels, buffer overflows, memory/object reuse, executable mobile code, TOCTOU, backdoors, trapdoors, malformed input, citizen developers

### Buffer Overflow

#####Core Concepts:

- Buffer overflow is a common problem with applications and happens when information sent to a storage buffer exceeds the capacity of the buffer
- Buffer overflow vulnerabilities can be exploited to elevated privileges or launch malicious code
- **Address space layout randomization (ASLR)**
    - One of the best ways to mitigate buffer overflows
    - Randomizes the locations of where system executables are loaded into memory.

- **Bounds checking:**
    - Another way to protect against buffer overflows

### Application Programming Interfaces (APIs)

#####Core Concepts:

- APIs provide a way for apps to communicate with each other; APIs act as translators
- 2 of the most common APIs are Representational State Transfer (REST) and Simple Object Access Protocol (SOAP)
- APIs should be secured along with other components of an application; security can include authentication and authorization mechanisms, TLS encryption for data traversing insecure channels, API gateways, and data validation, among others

### Secure Coding Practices

#####Core Concepts:

- Secure programming can help preven software vulnerabilities
- Secure coding practices include:
    - Input validation
    - Authentication and password management, session management, among others
    - Coupling and cohesion are relational terms that indicate the level of relatedness between units of a code base (coupling) and the level of relatedness between the code that makes up a unit of code (cohesion)
    - Low coupling (meaning units of code can stand alone) and high cohesion (meaning the code that makes up a unit of code is highly related) are optimal
    - Polyinstantiation refers to something being instantiated into multiple separate or independent instances and can be used to prevent unauthorized inference

### Software Development Vulnerabilities

#####Core Concepts:

- Insecure coding practices and citizen developers writing code usually leads to software development vulnerabilities
- Backdoor/trapdoor attacks often result from software vulnerabilities
- Between-the-lines attack = attacker intercepts/modifies communication between devices/people over a network; also known as a man-in-the-middle attack

---


[RETURN to CISSP home](../cissp.md)
