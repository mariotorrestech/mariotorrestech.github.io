#### Domain 5

# Identity and Access Management (IAM)

## Control physical and logical access to assets

### Access Control

######Core Concepts:

- Refers to the collection of mechanisms that work together to protect organization assets while simultaneously allowing controlled access to authorized subjects
- Fundamental access control principles includes:
  - Need to know
    - Restricting access to only required personnel who require access
  - Least privilige
    - Granting only the minimum permissions required by the user
  - Separation of duties
    - Requiring more than one person to complete a task, to prevent errors and fraud
- Access control is applicable at all levels of an organization and covers all types of assets

### Administration Approaches

######Core Concepts:

- Access control administration often takes one of two approaches:

  - **Centralized**
    - 1 system control access to remote systems
    - 1 username and password in the central system used to access all systems
    - Central admin point represents a single point of failure and potential target of attack

  - **Decentralized**
    - Control is granted to the people closer to the resource
    - Access requests are not processed by one centralized entity; separate usernames and passwords exist on each resource
    - Lack of standardization, overlapping rights, and security holes may exist
    - Peer-to-peer relationship
  - Many organizations also use a **hybrid** approach
    - Approach taken by most organizations
    - often due to legacy systems in an organization that cant be integrated with newer/modern access control systems (thinking mainframe)

## Design identification and authentication strategy

## The Seven Laws of Identity

<u>IN MY OWN WORDS:</u>

User control/consent

Minimal disclosure and constrained use of ID information

Justifiable parties (who have necessary reason to be part of identity relationship)

Directed Identity, sounds like public facing ID for other users - but private ID for that service, say Twitter, would only have a private ID on your file and not able to correlate data/info (_?_)

Pluralism of operators and tech - universal use across companies

Human integration - humans should be present in the relationship, and comms guarded to be extremely reliable

Consistent experience across disparate systems

---

1. #### User control and consent:

   - Identity systems should be designed so that information identifying a user is only revealed with the **consent** of the user

2. #### Minimal disclosure and constrained use

   - The most staable long-term identity solution is the one that reveals the least amount of identifying information **and** limtes the use of this data

3. #### Justifiable parties

   - Identity solutions should be designed to only disclose identifying information to parties that have justifiaable and necessary reason to be part of the identity relationships

4. #### Directed Identity

   - As an example, a public website should have omni-directional identifiers so that users can easily find and connect to it. These users should have uni-directional identifiers so that they can connect to the website while preserving their privacy from other parties
   - IN OTHER WORDS:
     - A universal ID meta-system must support both OMNI identifiers for user by public entities – and UNI identifiers for user by private entities. Thus facilitating discovery while proventing unnecessary release of correlation handles

5. #### Pluralism of operators and technologies

   - Universal identity systems should be interoperable with a range of identity providers and technologies

6. #### Human Integration

   - Identity systems must be designed under the consideration that **human users are a vital component**. They must be **integrated** into the system, with protections in place to also guard the communications between the human and the system itself.
   - Identity systems need to ensure that the communication between the users and the system is extremely **reliable**

7. #### Consistent experience across contexts

   - The identity system must provide users with a consistent and simple experience even whenb they use different identity providers and technologies

### Access Control Services

######Core Concepts:

- Access control services consist of:
  - Identification
    - Refers to the assertion of a user's identity or a process to a system
  - Authentication
    - Refers to the verification of an identity through knowledge, ownership, or charactestics
  - Authorization
    - Refers to the level of access defined for the identified and authenticated user or process
  - Accountability
    - Refers to proper identification, authentication, authorization, that is logged and monitored
    - AKA, the Principle of Access Control

### Identification

######Core Concepts:

- Identification is the component of Access Control Services that uniquely asserts a user's identity or a process to a system
- Identification guidelines include: unique IDs, nondescriptive of job role, secure issuance

### Authentication by Knowledge

######Core Concepts:

- Authentication by knowledge is the component of Access Control services that refers to SOMETHING YOU KNOW

### Authentication by Ownership

######Core Concepts:

- Refers to verification of an identity through SOMETHING YOU POSSESS
- OTP are generated via a synchronous or asynchronous process
- Soft tokens: Google Authenticator, MS Authenticator
- Hard tokens: RSA's SecureID device, that generate OTPs
- Smart cards
- Memory cards

### Authentication by Characteristics

######Core Concepts:

- Refers to physiological and behavioral biometric types
- Biometric device accuracy can vary and is not always 100 percent acurate
- consider processing speed, user acceptance, protection of biodata, accuracy
- **Crossover Error Rate (CER**) represents the intersection between Type 1 - False Rejects AND Type 2 - False Accepts, it measures the accuracy of a biometric system

#### Biometric Device Considerations

Factors must be considered:

- Processing Speed
- User Acceptance
- Protection of Biometric Data
- Accuracy

Biometric systems can be much slower than other types of authentication systems. Users may be less willing to accept this. Biometric is inherently unique so it must protected to a paramount importance. Finally, accuracy of biometric systems be carefully considered.

#### Biometric Device Accuracy/Types of Errors

When considering biometric systems and their accuracy, 2 primary types of errors need to be understood:

- #### TYPE 1

  - When a valid user is falsely rejected.
  - False rejection rate (**FRR**) is the probability that a valid user will be rejected by the system

- #### TYPE 2

  - When an **invalid user** is given access to a system. It is much more serious and potentially dangerous situation
  - False Acceptance Rate (**FAR**) is the probability that an invalid user will be accepted by the system

#### Crossover Error Rate (CER)

Measures overall accuracy of a biometric system. No system has a CER of zero, but more lower == more better.

#### Biometric Templates

Regarding proteciton of biometric data…

Raw/original biometric data should never be stored, such as a simple picture of a fingerprint. Instead, good biometric systems will use one-way mathematical functions to create a representation of the features/characteristics from the source data – this digital representation is called a **template**.

- 1 to N for Identification
  - The scanner captures the biometric data, generating a new template, and then searches through a database of existing templates to try to find a reasonabley close match to identify the person
  - **A 1 : N scan of biometric templates is used for identification**
- 1 to 1 for Authentication
  - The scanner captures the user's biometric data, generate a new template, and because the user has already been identified with their username, the system will look up the user's existing template in a databse and compare the user's existing template to the new template. If the templates reasonably match, then the user is authenticated
  - **A 1 : 1 comparison of biometric templates is used for authentication**

#### Biometric Devices

##### Physiological

- Fingerprint
- Hand geometry
- Vascular pattern
- Facial
- Iris
- Retina - MOST ACCURATE

##### Behavioral

- Voice
- Signature
- Keystroke
- Gait

### Factors of Authentication

######Core Concepts:

- Refers to the 3 types of authentication (discussed above )
  - Authentication by knowledge
  - Authentication by ownership
  - Authentication by characteristic
- **Single**-factor authentication refres to any of the three types of authentication being used
- **Multi**-factor Authentication (**MFA**) refers to two or more of the 3 types of authentication being used

### Credential Management Systems

######Core Concepts:

- Password vaults:
  - Allows us to generate, store, sync, and manage unique passwords for each account
  - Can improve security by making it practical to create strong passwords. however they are a single point of failure

### Single Sign-On (SSO)

######Core Concepts:

- SSO refers to authenticating one time and being able to access multiple systems
- A disadvantage of SSO is the implication of centralized admin, which represents a single point of failure
- Kerberos is one of the major SSO protocols, and it provides accounting, authenticating, and auditing services
- SESAME is an improved version Kerberos, but not widely adopted
- Kerberos disadvantages include that it only supports symmetric encryption, and it is vulnerable to TOCTOU attack – time of check, time of use

Kerberos is an old and complicated protocol. Dont need to be an expert on how the protocol works. If alice does not currently have a valid ticket, she must first be authenticated by the Kerberos service before she can access the desired service

- Alice (**CLIENT**), sends a couple of initial messages to the Kerberos **Authentication Service (AS)**
- The Authentication Service will verify that Alice is a valid user and, if so, will send a few messages back to Alice.
  - one message is encrypted with Alice's password as the encryption key
  - another message is the **Ticket Granting Ticket** (TGT) – a message that Alice cannot decrypt as it is encrypted with the **Ticket Granting Service's** (TGS) key
- Thus, Alice decrypts the messages from the authentication service using their password (the encryption key)
- Assuming Alice still knows her password and decrypts the message, she will create a couple of new tickets and send them along with the still encrypted TGT to the TGS
- When the TGS receives the messages from Alice, it performs a number of verification stesp, and if it's ALL GOOD, it will create some new messages to send back to Alice including the encrypted **Service Ticket** (encrypted with the service's key)
- When Alice recieves the messages from the TGS, she creates some new messages and send them to the **Service** along with the still encrypted service ticket
- When the service receives the messages from Alice, it does a final few verification steps, and if everything looks good, the service will finally grant Alice access

Provides a sufficient overview of the critical messages, and major services of Kerberos – the Authentication Service and Ticket Granting Service – both of which are components of the **Key Distribution Center (KDC)**

One downside is encryption standards are poor.

Another downside, only one major ticket is used. TOCTOU susceptible. session hijacking. The point is – it can be frustrating to keep authenticating to low level/daily systems (because you have access to a secure system requiring frequent K8 authentication)

### CAPTCHA

######Core Concepts:

- A security measure that works by asking a user to complete a test to prove they're human
- Prevents automated account creation, spam, brute force

### Session Management

######Core Concepts:

- Session management refers to management of sessions created through a successful user identification , authentication, and authorization process
- A session represents the connection and interaction between a user/system
- Session hijacking is a risk where no session management exists
- Session termination and re-authentication is the best way to prevent or mitigate session hijacking

### Registration and Proofing of Identity

######Core Concepts:

- Identity proofing - registration - is the process of confirming or establisjhing that somebody is who they claim to be

- Identity proofing is a component of provisioning in the identity life cycle

### Authenticator Assurance Levels (AAL)

######Core Concepts:

- Authenticator Assurance Levels (AAL) refer to the strength of authentication processes and systems
- AAL levels rank from AAL1 (least robust) to AAL3 (most robust)
  - **AAL1**
    - some assurance, single factor authentication, Secure Authentication protocol

  - **AAL2**
    - High confidence, MFA, Secure Authentication protocol, approved cryptographic techniques

  - **AAL3**
    - Very high confidence, MFA, Secure Authentication protocol, "Hard" cryptographic authenticator providing proof of possession of key and impersonation resistance

### Federated Identity Management (FIM)

######Core Concepts:

- SSO refers to one-time authorization to gain access to multiple sytems in one organization; federated identity management (FIM) refers to one-time authentication to gain access to multiple systems, including systems associated with other organizations
- FIM relies on trust relationshisp established between different entities. FIM trust relationships include 3 components:
  - **principal/user**
    -  the person who wants to access a system
  - **Identity provider**
    - the entity that owns the identity and performs the authentication
  - **relying party**
    - aka the service provider

### Federated Access Standards

######Core Concepts:

- Key federated access protocols include:
  - Security Assertion Markup Language (SAML), WS-Federation, OpenID (for authentication), OAuth (authorization)
  - SAML is frequently used in FIM solutions and provides authentication and authorization
  - OpenID And OAuth are open-standard federated access protocols that provide authentication via Open ID and authorization via OAuth
  - SAML assertions are written in a language called XML, extensible markup language. XML is a way of communicating in a mannter that is machine and human-readable

**SAML**:

- provides authentication/authorization

**WS-Federation**

- provides authentication/authorization

**OpenID**

- provides authentication

**OAuth**

- Provides authorization

### Accountability = Principle of Access Control

######Core Concepts:

- Accountability = the principle of access control

  - Users must be uniquely ID'd

  - Users must be properly authenticated

  - Users must be properly authorized

  - All actions should be logged/monitored

### Just-in-Time (JIT) Access

######Core Concepts:

- Just-in-time access refers to the elevation of user privileges to an authorized user for a short period of time, so a user may complete necessary but infrequent tasks
- JIT access mitigates the need for long-term elevation of privileges, which minimizes potential security risks

## Federated identity with a third-party service

### Identity as a Service (IDaaS)

######Core Concepts:

- IDaaS refers to the implementation or integration of identity services in a cloud-based environment
- Risks of IDaaS include those related to availability of service, protection of critical identity data, and trusting a 3rd party with potentially sensitive or proprietary information

## Implement and manage authorization mechanisms

###### Core Concepts:

- ##### Discretionary Access Control (DAC)

  - means an asset owner determines who can access the asset
  - access given at the discretion of the owner

- ##### Rule based

  - based upon rules and can be utilized in a very granular manner, though it is very admin-heavy as a result
  - set of rules, ACL

- ##### Role-based (RBAC)

  - based upon roles/job functions, firewall admin or accts payable. users can be assigned to one or more roles that include authorizationd to perform duties
  - Users can be assigned to 1 or more roles and access is determined by a given role.
  - KEY: RBAC provides ability to assign privileges to users with minimal admin overhead
    - RBAC types
      - **Non-RBAC**
        - No roles. Individual accounts in each app.
      - **Limited-RBAC**
        - Some apps have per-app roles
      - **Hybrid-RBAC**
        - Combination of single role across multiples applications and per application roles
      - **Full-RBAC**
        - Organization role granting access to multiple applications
        - Full RBAC may actually increase the access admin burden. most firms use limited/hybrid because of this

- ##### Attribute-based (ABAC) / Context-based

  - very granular and is based upon user attributes, such as job function, type of device, working hours, asset classification, and so on
  - User, Environment, Resource, Action are fed into the **authorization engine**, policy is checked and matched against a variety of attributes that relate to the user and their environment = permit/deny

- ##### Mandatory Access Control (MAC)

  - System determines access rules based on **labels**
  - Rare to see, usually only in government organizations where **confidentiality** is primary importance
  - MAC requires:
    - every asset in an organization to have a **classification**
    - every user be assigned a clearance level
  - MAC system determines access based upon clearance level of the subject and classification, or sensitivity, of the object
  - KEY: access is determined by a **system**. designed to protect **confidentiality**

- ##### Risk-Based access control

  - Considers elements of a user connection (IP address, time of request) to determine a risk profile associated with the request.
  - Based upon the result, further authentication may be presented to the user

- Other access control approaches include:

  - context-based access control and risk-based access control

- eXtensible Access Control Markup Language (XACML) is one tool that defines and enables attribute-based access control

### Non-Discretionary Access Control

######Core Concepts:

- Non-discretionary access control means that **somebody other than the asset owner** determines who gets access
- Non-discretionary access control should be avoided, if possible

### Access Policy Enforcement

Policy Enforcement Point (PEP)

- PEPs are parts of an application that **receive authorization requests** for protected systems and data
- they function as gatekeepers and send the requests to the PDP where they are evaluated. When the PDP sends back the decision, the PEP enforces it by either granting or denying access. They are placed throughout an application's access points

Policy Decision Point (PDP)

- PDPs make decisions on the authorization requests that may have been sent ot them by PEPs.
- They make decisions based upon pre-defined rules and are generally centralized

## Manage the identity and access provisioning life cycle

### Vendor access

######Core Concepts:

- Vendor identity and access provisioning for systems and data should be considered with the same or more care than employee identity and access provisioning
- Vendor provisioning might also include a security review component that includes a deeper review of the vendor or inspection of a vendor's facilities, systems, and other relationships

### Identity Life Cycle

######Core Concepts:

- Identity Life Cycle is composed of three parts:
  - **Provisioning**
    - upon hiring of new employee and when employee changes roles
  - **Review**
    - should take places as often as necessary, and more frequently for higher privilege accounts
  - **Revocation**
    - upon voluntary or involuntary termination

### User Access Review

######Core Concepts:

- account access review is an ongoing process, regardless of the type of account (user, system, service)
- account access review frequency should be based upon the value of resources and associated risks
- privileged accounts should be reviewed more frequently

### Privilege Escalation

- use of sudo, etc by way of privileged accounts and not with normal standard user accounts

### Service Account Management

######Core Concepts:

- Service account management involves managing the accounts used by services (not humans)
- We should limit these accounts to single purposes and reduce their privileges to limit the chances of compromise

## Implement Authentication Systems

### Authentication Systems

######Core Concepts:

- Authentication systems are used to prove or verify an identity or system assertion
- Popular authentication systems include: OpenID Connect (OIDC), Open Authorization (OAuth), Security Assertion Markup Language (SAML), Kerberos, Remote Authentication Dial-In User Service (RADIUS) and Terminal Access Controller Access Control System Plus (TACACS+)

#### OpenID Connect (OIDC) / Open Authorization (OAuth)

- OAuth
  - is an **access delegation standard** that target applications can use to provide client applications with secure delegated access over HTTPS
  - **Authorizes** devices, APIs, servers, and applications with **access tokens** rather than credentials
- OpenID Connect (OIDC)
  - an **identity** layer built on top of the OAuth 2.0 framework.
  - Allows 3rd party applications to verify the identity of the end user and to obtain basic user profile information. While OAuth 2.0 is about resource access and sharing, **OIDC is about user authentication**
