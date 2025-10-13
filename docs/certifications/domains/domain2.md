#### Domain 2

# Asset Security

!!! Overview

    Asset security includes the concepts, structures, principles, and controls aimed at protecting assets - anything that represenets value to the organization.



    Domain 2 gives an overview of the steps involved in asset security to address some of the issues that security professionals often encounter while implementing them.


## Identify and classify information and assets

### Asset Classification

!!! note "Core Concepts"

    - Asset Classification: Assigning assets the level of protection they require, based on their value to the organization 
    - Asset classification policies, procedures, and processes help achieve proper protection of assets

**Classification is driven by the value of the asset**

Proper asset clasification ensures that assets receive an appropriate level of protection based on the value that they represent to the organization.

#### Information Classification Benefits

- Identification of **critical** information
    - Identifies information that the organization considers critical to business success
- Identification of **sensitivity** to modification
    - Classificaition helps identify data that must only be modified in specific authorized ways
- Commitment to **protect** valuable assets
    - Creates awareness among users that the organization is commited to protecting assets from unauthorized access
- Commitment to **confidentiality** (where applicable)
    - Classification helps ensure that sensitive information remains confidential

### Classification Process

!!! note "Core Concepts"

    - Asset classification begins with a detailed asset inventory
    - Asset owners determine the classification assigned to an asset
    - Asset classification is an ongoing process

Data classification ensures that data receive an appropriate level of protection. This is an ongoing process as data importance may change from one year to another.

**Asset classification steps**

### Classification vs Categorization

!!! note "Core Concepts"

    - Classification refers to a system of classes, ordered according to value
        - IE: Top secret, secret, sensitive, restricted, proprietary, trade secret, PII, etc
      
    - Categorization refers to the act of sorting assests into defined classes
    - Ideally, all assets should be categorized into a classification system to allow them to be protected based on value

## Labeling and Marking

!!! note "Core Concepts"

    - Labeling refers to the classification of the asset and is system-readable
    - Marking refers to the handling instructions of the asset and is human-readable
    - Should be consistently applied to all assets within an organization
    - Labeling should be cost-effective

**Main differences between the two**

Labeling results in output that is system-readable

  - Metadata, barcodes, QR codes, RFID, GPS tags

Marking extends the intent of labeling in a way that can clearly be understood and executed by humans

| LABELING                                                                                                   | MARKING                                                                      |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| System-readable                                                                                            | Human-readable                                                               |
| Association of security attributes of **subjects and objects** represented in **internal data structures** | Association of security attributes with objects in a **human-readable form** |
| Enables **system-based** enforcement                                                                       | Enables **process-based** enforcement                                        |

**Cost-effectiveness of different labeling approaches**

Depends on customer use case basically

## Establish information and asset handling requirements

### Media Handling

!!! note "Core Concepts"

    - Handling requirements are based on the classification of the asset, not the type of media
    - Owners determine who may access media, especially sensitive meia

**Media Storage**

- Use encryption, use physically secure locations based on storage requirements and classification of data.

**Media Retention and Destruction**

Based on organization data classification and data archiving policies.

## Provision information assets securely

### Data Classification Roles and Responsibilities

- Owners are accountable
- Assignment of ownership drives the data classification process
- Data classification roles and responsibilities

Identifying owners is an essential part of the classificaiton process since they are the ones accountable for the assets being protected. no owners = no accountability

**Owners are ultimately accountable for an asset and protecting its value**

The owner is:

- The person who directly interacts with the asset the most. Intimacy makes them understand the asset's value best.
- Even though IT may help manage the underlying systems related to the assets, they are only functioning as a custodian

Owners need to have clearly defined **accountabilities**

- Classificaiton and categorization of assets
- Managing access to assets
- Ensuring appropriate controls are in placed based on asset classification

Owners can delegate **responsibility** for an asset, but they always remain **accountable**. Accountability cannot be delegated.

- data owners, process owners, system owners, product owners, service owners, hardware owners, applications owners IP owners, etc

Regardless of the type of owner, each holds the same accountability:

- to understand the value of the assets to an organization and classify them properly and ensure appropriate protection as they progress through their life cycle

**Undestand different data roles and responsibilities**

- **Owner/Controller**
    - **Accountable** for protection of data; holds legal rights and defines policies
  
- **Processor**
    - **Responsible for processing** data on behalf of the owner/controller. IE cloud provider
- **Custodian**
    - **Technical responsibility** for data
    - Network administration, database custody, security, availability, capacity, etc
- **Steward**
    - **Business responsibility** for data (ex. metadata, quality, governance)
- **Subject**
    - Individual to whom personal data pertains

### Data Classification Policy

!!! note "Core Concepts"

    - Data classification policy is concerned with the management of inforamtion to ensure that sensitive and valuable information is protected and handled accordingly
    - Data classification policy considers laws, regulations, privacy requirements, customer requirements, cost of creation, operational impact, liability, and reputation

## Manage data life cycle

### Information Life Cycle

- Information life cycle phases
- Data must be protected at each phase

#### Data lifecycle stages:

- **Create**
    - Generation of new digital content, or the alteration/updating/modifying of existing content

- **Store**
    - Committing digital data to some sort of storage repo, which typically occurs nearly simultaneously with creation

- **Use**
    - Data viewed, processed, or otherwise used in some sort of activity, not including modifying

- **Share**
    - Information made accessible to others, such as company users, customers, and partners

- **Archive**
    - Data leaves active use and enters long-term storage

- **Destroy**
    - Data is permanently destroyed using physical or digital means

### Data Destruction

!!! note "Core Concepts"

    - Data remanence refers to residual representation of information even after attempts to securely delete or remove the data
    - Categories of sanitization - destruction, purging, clearing
    - Secure removal of data in the cloud

Most experts today consider any number of overwriting passes as being 'clearing' and not 'purging'

**Physical destruction of media is best, but it may be too costly, unavailable, or otherwise infeasible**

## Ensure appropriate asset retention

### Data Archiving

!!! note "Core Concepts"

    - Data archiving is part of the asset life cycle
    - Data archiving includes requirements for archived data
    - Data archiving should be driven by an appropriate retention policy

**Data archiving policies**

- Archiving/retention policy are based on laws, regulations, industry standards, and business needs

- Classify records accordingly
- Educate employees and provide them with the right tools

**Questions to consider when writing a policy**

- Who needs access to the data?
- Do access requirements change over time?
- How long does data need to be kept?
- What are the disposal requirements?

## Determine data security controls and compliance requirements

**What is the best way to ensure data receives appropriate protection based on classification?**

### Protecting Data at Rest

!!! note "Core Concepts"

     - Methods used to protect data at rest:
          - Encryption
          - Access control
          - Backup
          - Restoration

### Protecting Data in Transit

!!! note "Core Concepts"

    - Methods used to protect data in transit:
        - E2E encryption
        - Link Encryption
            - Decrypted at each link, unlike E2E
        - Onion network

### Protecting Data in Use

!!! note "Core Concepts"

    - Methods used to protect data in use:
        - Homomorphic encryption
            - Allows calculations to be performed on data while the data remains encrypted
        - Role Based Access Control (RBAC)
        - Digital Rights Protections (DRP)
        - Data Loss Prevention (DLP)

Refers to data that is being used in some type of computational activity

### Information Obfuscation Methods

Obfuscation makes something harder to understand

Obfuscation methods:

  - **Concealing Data**
    - Unlike pruning, completely removes access to sensitive data. Users do not have access, nor do they have visibility and the attribute field does not appear on computer screens and reports

  - **Information Pruning/Pruning Data**
    - Primarily takes place in non-prod environments and involves removal of sensitive data from attributes. The attribute will still be visible as a field on computer screens/reports but will not be populated with data

  - **Fabricating Data**
    - Especially when testing functionality

  - **Trimming data**
    - Unlike pruning, removes part of an attribute's value and is typicalled used for purposed of identification. IE, SSNs where only the last 4 are visible

  - **Encrypting data**
    - Creates ciphertext of a value

### Digital Rights Management (DRM)

!!! note "Core Concepts"

    - DRM protects IP assets and the rights of asset owners
    - DRM Techniques
    - Legal basis for protection in the US through the Digital Millennium Copyright Act (DMCA)

### Data Loss Prevention (DLP)

!!! note "Core Concepts"

    - Data loss prevention focuses on the identification, monitoring, and protection of data
    - DLP data activites take place in three contexts: data in use, data in motion, data at rest
    - DLP takes place for multiple reasons
