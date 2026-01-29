## Security Controls - 1.1

There are many security risk for which we have to be prepared for.
Other than data, also people, physical property and other kind of assets are protected.

In this lesson we'll see how to prevent some security events, minimize their impact and limit the damages that may occur.

### Main control categories:

1. **Technical controls**: These are controls implemented through the use of technical or technological systems. An administrator can enforce them by managing an operating system through policies and procedures that allow or prevent certain functions, or by using software such as firewalls and antivirus software.

2. **Managerial controls**: These involve the creation of official policies and procedures that explain how to properly manage computers, data, and systems within an organization. These controls are often included in official security policy documentation or integrated into daily processes as a standard operating procedure (SOP).


3. **Operational controls**: Unlike technological controls, operational controls rely on the use of people to implement them. Examples include the presence of security guards, organizing awareness programs, or posting posters to promote cybersecurity best practices.

4. **Physical controls**: This category includes controls that limit physical access to a building, room, or specific device. Common examples include fences, locks, and badge readers for access, as well as devices such as fire extinguishers and power generators to ensure business continuity in the event of an emergency.


### Preventive controls
Their primary purpose is to restrict access to a specific resource to prevent an event from occurring.

-  Technical: Firewall rules that prevent access to certain areas of the network.
- Management: Onboarding policies established for new hires.
- Operational: A security booth where someone checks the IDs of those entering.
- Physical: Locks on doors that physically prevent access to a room.


### Deterrent controls
These controls do not necessarily prevent access, but serve to discourage a potential attacker or make them think twice before proceeding with an attack.

- Technical: A splash screen that provides security information and warns that unauthorized access is restricted.
- Management: The threat of administrative sanctions, such as demotion or dismissal, in the event of unauthorized data access.
- Operational: A reception desk at the entrance that welcomes and identifies anyone entering.
- Physical: Warning signs that indicate the consequences of unauthorized access.

### Detective controls (controlli di rilevamento)
These controls are designed to identify and report a breach that has already occurred, often providing log information about the attack.

- Technical: System logs that record all activity in detail.
- Management: Processes for periodically reviewing login reports.
- Operational: Personnel who patrol the property to identify intrusions.
- Physical: Motion sensors that automatically notify anyone who moves into unoccupied areas

### Corrective controls
They intervene after an event has been detected to mitigate its impact, restore systems, or minimize downtime.

- Technical: Restoring a ransomware-infected system using backups
- Management: Creating policies for reporting security issues or unusual activity
- Operational: Contacting law enforcement to manage a legal incident
- Physical: Using a fire extinguisher to put out a fire and prevent it from spreading

### Compensating Controls
These are used when there are no immediate means to resolve a problem, providing alternative means to manage the risk, often on a temporary basis.

- Technical: Blocking traffic via a firewall rule to protect a vulnerable application while waiting for the developer to release a patch.
- Management: Separating duties among different individuals to limit the scope of a potential security issue.
- Operational: Requiring the simultaneous presence of multiple security personnel so that no one person has complete control.
- Physical: Using a generator to compensate for a main power outage


### Directive Controls
These are considered relatively weak controls because they merely instruct people to behave securely.

- Technical: Policies that require users to decide which data is sensitive and to save it only in encrypted folders.

- Management: Compliance policies and procedures to explain proper security processes.

- Operational: Security training courses to educate staff on company policies.

- Physical: A sign on a door that says "Authorized Personnel Only" does not physically prevent access (if the lock is missing), but directs people not to enter.

## CIA Triad - 1.2

The **CIA** triad consists of three main objectives, often represented as the sides of a triangle:

### 1. Confidentiality
The goal is to prevent unauthorized access to private information by ensuring that data is available only to the right people. There are several strategies for ensuring this:
- **Encryption:** A person encrypts the data, and only the recipient can decrypt it to view the original plaintext; anyone intercepting the data in between will be unable to understand its contents.
- **Access Controls:** Restrict access based on role (for example, allowing the marketing department to view presentations but not the company's financial data).
- **Authentication Factors:** Adding additional authentication factors during login increases confidentiality, preventing access by those without the correct credentials.

### 2. Integrity
This ensures that the data received is **exactly the same as that sent**, ensuring that no one has modified it while in transit over the network. The main methods include:
- **Hashing:** The sender creates a hash of the data and sends it along with the message. The recipient performs the same hashing function; if the two values ​​match, integrity is confirmed.
- **Digital Signatures:** These combine hashing with asymmetric cryptography to confirm not only that the data has not changed, but also the sender's identity.
- **Certificates:** Used to identify devices or people, providing additional integrity guarantees during data transfer.
- **Non-repudiation:** This concept, provides definitive proof that the information actually comes from the stated party.

### 3. Availability
This pillar ensures that systems remain operational and that users always have access to the data they need. Availability is maintained with these methods:
- **Fault tolerance:** Design systems with multiple components so that if one fails, the others continue to operate normally.
- **Patching and updates:** Constantly manage and update systems to keep them stable and close security vulnerabilities that could be exploited to cause service disruptions.


## Non repudiation - 1.2
Non-repudiation is a fundamental pillar of cryptography that allows a third party to verify with certainty that information actually comes from the intended sender.

### Foundations: Integrity and Origin
To achieve non-repudiation, cryptography relies on two key concepts:
- **Proof of Integrity**: The guarantee that the data received is exactly the same as the data sent, without any modification, and is therefore accurate and consistent.
- **Proof of Origin (Authentication)**: The verification of the specific person who sent the data, providing a high level of authenticity.

### The Role of Hashing
Integrity is verified through **hashing**, which creates a short text string known as a **fingerprint** (or *message digest*) of the plaintext.
- If even a single character of the original data is changed, the fingerprint will change radically.
- **Practical example:** Let's take the case of Volume 1 of the Project Gutenberg encyclopedia (8.1 MB). If a single character were to change in that sea of ​​data, it would be impossible for a human to notice, but a hashing algorithm would produce a completely different value, immediately signaling that the file has been corrupted or modified.
- **Limitations of hashing:** While the hash confirms integrity (the data has not changed), it alone cannot verify the sender's identity.

### The Digital Signature and the Non-Repudiation Process
Non-repudiation is achieved by adding a digital signature, which uses a private key (known only to the sender) and an associated public key (available to anyone).

Let's take the example of Alice sending a message to Bob:
[Digital Signature Creation](https://res.cloudinary.com/dnhgctqsu/image/upload/Alice_and_Bob_a8krb8.png)
1. **Hash Creation:** Alice's system creates a hash of the original message ("You're hired, Bob").
2. **Hash Encryption:** The hash is encrypted with Alice's private key. This encrypted hash becomes the digital signature.
3. **Sending:** Alice sends the cleartext message along with the digital signature to Bob.
4. **Decryption and Verification by Bob:** Bob receives the message and uses **Alice's public key** to decrypt the signature and obtain the original hash.
5. **Comparison:** Bob independently generates a new hash from the received message and compares it with the one obtained from Alice's signature.

[Digital Signature Verification](https://res.cloudinary.com/dnhgctqsu/image/upload/Screenshot_From_2026-01-19_18-42-51_n4uif2.png)

If the two hashes match, Bob has mathematical proof that the message **has not been altered** and that **it must have been sent by Alice**, since only she possesses the private key needed to create that specific signature. This process ensures that neither Alice nor Bob can deny the transaction, guaranteeing non-repudiation.


## Authentication, Authorization, and Accounting (AAA)

The **AAA framework** is a foundational security concept used to manage access to systems and resources. It consists of three primary components, often preceded by the initial step of **identification**.

###  Core Components of AAA
-   **Identification:** This is the initial step where a user **claims to be a specific identity** on a system, typically by providing a username.
-   **Authentication:** This process **proves that the user is truly who they say they are**. This is achieved by checking the provided username against a secret password or additional authentication factors.
-   **Authorization:** Once identified and authenticated, the system must determine the **type of access** the user is permitted. This ensures that users can only access resources relevant to their department (e.g., shipping and receiving) and are restricted from others (e.g., finance).
-   **Accounting:** Security systems must maintain a **log of activity**. This includes recording the login time, the amount of data sent or received, and the time the user logged out.



###  Practical Application: The AAA Server
In many organizations, authentication data is not stored locally on individual devices like firewalls or VPN concentrators. Instead, it is managed centrally:
-   **Centralized Management:** A dedicated **AAA server** stores usernames, passwords, and authentication factors in a central database.
-   **The Process:** When a user attempts to log into a **VPN concentrator**, the device sends the credentials to the AAA server. The server verifies the match and sends an approval back to the concentrator, which then allows the user to access internal resources.



###  Device Authentication and Certificates
Security professionals must often authorize devices (like company laptops) that may be located anywhere in the world and cannot manually enter a password,.
-   **Digital Certificates:** To verify that a device is company-owned, a **digitally signed certificate** is installed on the machine
-   **Certificate Authority (CA):** A CA is a device or software responsible for **managing and signing certificates** within an environment 
-   **Verification:** During login, the security infrastructure compares the device's certificate (signed by the CA) against the CA's own certificate. If they match, the device is authenticated as a trusted system



### Authorization Models and Scalability
Manually assigning rights and permissions to every individual user does not scale well in large organizations. 
-   **The Problem with Manual Mapping:** If a user in "shipping and receiving" needs access to five different databases and tracking systems, manually configuring these for hundreds of employees is inefficient and error-prone
-   **Abstraction through Groups:** To scale, organizations use **authorization models** (or abstractions) to separate users from the resources they access
-   **Role-Based Access:** Instead of mapping users to resources, users are added to a **group** (e.g., "Shipping and Receiving Group"). Permissions are assigned to the group itself, so any user added to it automatically gains all necessary access to shipping labels, customer data, and tracking reports


## Gap Analysis

A gap analysis is a formal study comparing an organization's current security posture ("**where we are**") against its desired security goals ("**where we would like to be**")

Its **purpose** is to identify what security measures will be required in the future.

Executing this concept requires a complex process that can take several **weeks**/**months**, or even **years** to complete. It requires **extensive** project **planning**, data gathering, and involvement from various people across the organization.

### Establishing Baselines
Before conducting the analysis, an organization must establish a baseline to serve as a target goal

- **Common Standards**:
    - **NIST SP 800-171 Revision 2**: Focused on "Protecting Controlled Unclassified Information in Non-federal Systems and Organizations"

    - **ISO/IEC 27001**: An international standard for Information Security Management Systems

    - **Custom Baselines**: Organizations can also create their own standards based on specific internal needs

### Key Areas of Evaluation
The analysis typically breaks down broad security categories into smaller, manageable segments for evaluation:

- **People**: Evaluates staff based on their formal <ins>IT</ins> security <ins>experience</ins>, the <ins>training</ins> they have <ins>received</ins>, and their specific <ins>knowledge</ins> of the <ins>organization</ins>'s <ins>policies</ins> and <ins>procedures</ins>

- **Processes**: Involves an <ins>evaluation</ins> of <ins>existing IT systems</ins> to see how they align with formal security policy documentation

- **Example (Access Control)**: A broad category like "Access Control" is broken down into specific tasks such as user registration/deregistration, access provisioning, and management of privileged rights


[SP 800-171 Rev 2 Table](https://res.cloudinary.com/dnhgctqsu/image/upload/Screenshot_From_2026-01-24_19-14-17_exoc0r.png)

### The Analysis and Reporting Process
1. **Comparison**: The analysis begins by comparing <ins>existing systems</ins> **against** the <ins>baseline</ins> to <ins>identify weaknesses</ins> and determine <ins>effective processes</ins> to **compensate** for them

2. **Bridging the Gap**: The analysis must determine the "<ins>path</ins>" to reach the <ins>desired state</ins>, which often requires time, money, new equipment, and formal Change Control

3. **The Gap Analysis Report**: This final document summarizes all discoveries
It includes:
    - The <ins>current status</ins> of security objectives
    - A <ins>pathway/recommendations</ins> for moving forward
    - **Visual Prioritization**: Reports often use color-coding to show which <ins>locations</ins> or requirements <ins>need</ins> the most <ins>work</ins>:
        - **Red**: Needs significant work (highest priority for improvement)
        - **Yellow**: Midpoint
        - **Green**: Relatively close to meeting the baseline

[Gap Analysis Report](https://res.cloudinary.com/dnhgctqsu/image/upload/v1769278652/tabella_wuznth.png)


## Zero Trust
In traditional network environments, once a user or device passes through the initial firewall, the internal network is often relatively open, allowing both authorized and unauthorized entities to move between systems without further checks.
**Zero Trust** shifts this paradigm by operating under the principle that **nothing is trusted by default**. Every <ins>user, device, and process</ins> must <ins>prove its identity</ins> and be <ins>authenticated</ins> every time they attempt to <ins>access a specific resource</ins>. 
This environment often employs several security controls, including:
-   **Multifactor authentication (MFA)** during login.
-   **Encryption** for both data at rest and data traversing the network.
-   Additional **system permissions** and **firewalls**.

### Planes of Operation
To implement Zero Trust, security administrators <ins>break down</ins> security <ins>devices</ins> and <ins>processes</ins> into <ins>two</ins> distinct functional <ins>planes of operation</ins>:
-   **The Data Plane:** This is the <ins>part of the device</ins> - whether a physical switch, virtual firewall, or cloud process - that performs the **actual security processing**.
It handles the real-time movement of data, including <ins>forwarding, routing, and Network Address Translation</ins> (NAT).
-   **The Control Plane:** This is where the **management of the data plane** occurs. It is used to <ins>configure policies, routing tables, and rules</ins> that determine <ins>how data is allowed to traverse the network</ins>.

### Identity and Access Control
Zero Trust requires a "smarter" way to evaluate security controls through methods like **adaptive identity**. Instead of relying solely on a user's claims, the system examines multiple variables to confirm identity, such as:
-   **Geographic location and IP address** (e.g., flagging a request if a user is using a Chinese IP to access U.S. resources).
-   **Organizational relationship**, such as whether the individual is a full-time employee or a contractor.
-   **Connection type** and the specific device being used.

These data points are integrated into a **policy-driven access control** system that decides the level of authentication required. Additionally, organizations categorize network traffic into **security zones** (such as "Trusted," "Untrusted," "Internal," or "External") to set rules on which zones are allowed to communicate with one another.

[Zero trust across planes](https://res.cloudinary.com/dnhgctqsu/image/upload/v1769360627/Screenshot_From_2026-01-25_18-02-03_xnnms9.png)

### Key Architectural Components
The Zero Trust model relies on a specific hierarchy of components to evaluate and enforce security decisions:
-   **Policy Enforcement Point (PEP):** Acting as a **gatekeeper**, the PEP is the location where all network traffic must pass. It does not make the final decision but gathers information about the traffic and provides it to the decision-making components.
-   **Policy Decision Point (PDP):** This consists of two main parts:
    -   **Policy Engine:** This examines the request against **predefined security policies** to decide if access should be granted, denied, or revoked.
    -   **Policy Administrator:** Once a decision is made, the administrator provides the necessary **access tokens or credentials** back to the PEP.

### The Zero Trust Workflow
In a complete Zero Trust model, a subject (user or system) from an **untrusted zone** attempts to communicate across the **data plane**. The traffic hits the **Policy Enforcement Point**, which sends the request to the **Policy Administrator** and **Policy Engine**. If the Policy Engine determines the traffic is allowed based on its evaluation, the decision is passed back through the administrator to the enforcement point, which finally grants access to the **trusted zone** and the requested enterprise resource.


## Physical Security

IT security professionals must be proficient in **physical security** in addition to digital security. Here are some physical security methods and technologies used to protect facilities.

### Structural Barriers
-   **Barricades and Ballards:** These are used to **channel people** through specific <ins>access points</ins> and prevent <ins>vehicles</ins> from entering <ins>restricted areas</ins>. They can also serve as a **security notice** to indicate a <ins>high-security zone</ins>. Beyond concrete barriers, features like water and bridges can also function as barricades.
-   **Fencing:** Fences are obvious physical controls that can be **transparent or opaque**. To increase security, fences should be robust and may include additions like **razor wire** or increased height to prevent intruders from climbing over.

### Entry and Identification Controls
-   **Access Control Vestibules:** This is a specialized <ins>room</ins> one must pass <ins>through</ins> to enter a building. They can be configured in various ways—such as having <ins>doors that cannot be unlocked simultaneously</ins> — to control the flow of individuals or small groups. These are common in high-security areas like **data centers** and often require <ins>card</ins> or **biometric readers** for <ins>authentication</ins>.
-   **Identification Badges:** <ins>Employees</ins> are often required to <ins>wear</ins> visible <ins>ID badges</ins> containing their <ins>picture</ins> and <ins>name</ins>. These badges are frequently integrated with **electronic locks**, allowing the organization to <ins>log</ins> every time an individual <ins>enters a room</ins> into a central database.
-   **Security Guards:** Human guards provide a physical presence to <ins>validate employees and guests</ins>. Using two or more guards simultaneously provides **two-person integrity**, ensuring that one individual <ins>cannot circumvent security policies</ins> without another person providing checks and balances.

### Surveillance and Lighting
-   **Cameras (CCTV):** Closed-circuit television systems are used to <ins>monitor</ins> locations more efficiently than manual oversight. Modern cameras are "intelligent," featuring **motion detection**, **facial recognition**, and the ability to **read license tags**.
-   **Lighting:** Proper illumination is a primary <ins>deterrent</ins> because unauthorized individuals prefer to move out of view. Lighting is also critical for camera performance, specifically for **facial recognition** in areas like parking lots.

### Detection Technologies
There are several types of sensors used to detect movement or presence:
-   **Infrared (IR):** IR technology detects radiation and is used in cameras to see in the dark or in **motion detectors**.
-   **Pressure Sensors:** These detect changes in force when someone moves across a specific area.
-   **Microwave Technologies:** These are used to detect movement over **much larger areas** than infrared sensors can cover.
-   **Ultrasonic Detection:** This technology uses **reflected sound waves** to detect motion and can provide collision detection in loading zones or parking lots.

## Deception and Disruption
IT security professionals can use **deception and disruption** techniques to attract, study, and track attackers who attempt to gain access to systems.

### Honeypots
A **honeypot** is a system designed specifically to attract attackers and keep them engaged so that security professionals can observe the techniques and automation they use. 
-   **Purpose:** These systems act as a <ins>virtual world</ins> that is entirely <ins>separate</ins> from actual production processes. By monitoring a honeypot, you can identify what <ins>types</ins> of automated <ins>processes</ins> or specific <ins>systems</ins> the attackers are <ins>targeting</ins>.
-   **The "Race":** There is a continuous race between defenders and attackers; as <ins>attackers</ins> become better at <ins>identifying traps</ins>, <ins>defenders</ins> must increase the <ins>complexity and intelligence</ins> of honeypots to make them appear more <ins>realistic</ins>.
-   **Creation:** Security professionals can build these using various commercial or open-source software packages.

### Honey Nets
When multiple virtualized <ins>honeypots</ins> are <ins>combined</ins> into a <ins>larger infrastructure</ins>, it is called a **honey net**. 
-   **Components:** A honey net can include various network elements such as **workstations, servers, routers, and firewalls** to mimic a real-world environment.
-   **Effectiveness:** This larger-scale infrastructure is much more believable to an attacker and is intended to keep them occupied for a significant amount of time. 

For more information on these technologies, look [here](www.projecthoneypot.org).

### Honey Files
Deception can also be implemented at the file level through **honey files**.
-   **Nature:** These are files containing fake information that appear sensitive or important, such as a file named **"password.txt"**.
-   **Monitoring:** Since these files have no place in a normal production network, any attempt to access or open them should trigger **alerts or alarms** sent to a management station, signaling that someone is unauthorizedly browsing the system.

### Honey Tokens
**Honey tokens** are pieces of traceable, falsified data used to identify issues with data leaks or public distribution.
-   **Functionality:** If a honey token is copied and distributed, its unique nature allows security professionals to know exactly where it <ins>originated</ins>.
-   **Examples of Honey Tokens:**
    -   **API Credentials:** <ins>Fake credentials</ins> placed on a public cloud share to see <ins>who</ins> attempts to <ins>use them</ins>.
    -   **Email Addresses:** <ins>Fake addresses</ins> that are monitored to see if they <ins>appear elsewhere</ins> on the <ins>internet</ins>, which can help <ins>identify</ins> who is <ins>attacking</ins> the network.
    -   **Other Data Types:** Honey tokens can take many forms, including **database records, browser cookies, or even specific pixels on a web page**. If this data is posted elsewhere online, it provides actionable intelligence about the <ins>source</ins> of the <ins>breach</ins>.


## Change Management

Change management is a critical <ins>formal process</ins> used in corporate environments to <ins>ensure</ins> that <ins>updates</ins> to <ins>applications</ins>, operating systems, <ins>or infrastructures</ins> like routers and firewalls are <ins>implemented properly</ins> without causing widespread disruption. Unlike home environments where a change might only affect one computer, a <ins>single change</ins> in a large organization can <ins>impact thousands of systems</ins>.


### The Purpose of Change Control
-   **Security and Stability:** Regularly updating systems is vital because <ins>unpatched systems</ins> are <ins>less secure</ins>. Formal processes **prevent the problems** that arise if everyone made changes at will, such as **application inconsistencies** or **failures**.
-   **Availability:** The primary goals are to **maintain system uptime**, ensure all parties are informed to **avoid confusion**, and **prevent human error** during implementation.

### The Typical Change Control Process
1.  **Documentation:** The process begins by filling out a formal <ins>Change Control form</ins>. This includes documenting the **reason for the change**, the **scope** (which systems are affected), and the **intended schedule** (date and time).
2.  **Risk Analysis:** A Change Control Board or committee analyzes the risks. They must **balance** the **risk** of *making* the **change** (potential for failure during busy periods) against the **risk** of *not* making the **change** (such as leaving a security vulnerability unpatched).
3.  **Approval:** The board uses the provided documentation to decide whether to <ins>allow</ins> or <ins>disallow</ins> the <ins>change</ins>.
4.  **Verification:** Once implemented, users and owners must <ins>test</ins> the <ins>systems</ins> to confirm the change was successful and did not cause new problems.

### Roles and Responsibilities
-   **Owners:** The <ins>owner</ins> of the application or data usually <ins>initiates</ins> the <ins>request</ins> and <ins>manages</ins> the <ins>process</ins> but does not typically perform the technical change themselves. They are <ins>responsible</ins> for final <ins>testing</ins> and <ins>verification</ins>.
-   **IT Team:** The IT department generally <ins>handles</ins> the actual <ins>technical implementation</ins> of the change.
-   **Stakeholders:** These are <ins>individuals</ins> or departments impacted by the <ins>change</ins>. Identifying them can be complex; for example, a change to shipping label software might impact accounting (for reports), customer delivery times, and even revenue recognition visible to the CEO.

### Risk Management and Testing
-   **Types of Risk:** Risks include the fix not working, the update breaking other systems, operating system failure, or **data corruption**. 
-   **Sandboxing:** To mitigate risk, changes should be tested in a **sandbox environment**, a "technological safe space" that duplicates the production environment so mistakes do not affect users.
-   **Backout Plans:** Every change must have a documented **backout or rollback procedure** to revert the system to its original state if the change fails. It is highly recommended to have a **full and complete backup** of the system before any change is attempted.

### Scheduling and Implementation
-   **Maintenance Windows:** Finding time to implement changes is often the hardest part. IT teams frequently work during "off-hours," such as weekends, holidays, or early mornings, to minimize user disruption.
-   **Change Freezes:** Some organizations, such as retail companies, may implement a **total freeze on changes** during their busiest times of year (e.g. between Thanksgiving and New Year).

### Governance
Change management should be a part of an organization's **Standard Operating Procedures (SOPs)**. These procedures are typically documented on a company intranet so they are accessible to everyone, ensuring no one makes unauthorized changes to the network. The process is also expected to be updated over time to improve efficiency and meet company requirements.

## Technical Change Management
While making changes to a few devices at home is simple, performing updates in an environment with hundreds or thousands of devices is a complex process.

### Access Control Lists
A common technical change involves managing **allow lists** and **deny lists** to control which applications can run:
-   **Allow lists** are highly <ins>restrictive</ins>, permitting only specifically named applications to run while blocking everything else.
-   **Deny lists** are more <ins>flexible</ins>, allowing all applications to run except those explicitly identified as dangerous or malicious, such as code identified by antivirus software.

### Change Scope and Policy
Every change approved by a Change Control Board has a **specifically documented scope**. Technicians are generally <ins>limited</ins> to making <ins>only</ins> the <ins>changes listed</ins>; for instance, a window for printer driver updates does not authorize changes to other applications. However, if the primary goal requires a minor, unlisted modification (like editing a configuration file), company policies may allow the technician to expand the scope to ensure the update succeeds.

### Managing Downtime and Availability
To minimize impact, significant changes are usually scheduled for **non-production hours**. 
-   **24/7 Environments:** In organizations that never shut down, technicians often use a **primary and secondary system** approach. They update the primary system while users are on the secondary, then switch over seamlessly. 
-   **Fallback and Communication:** This dual-system setup allows for an easy **fallback** to the original configuration if problems arise. It is critical to communicate these windows to users via emails or centralized **Change Control calendars**.

### Implementation and Verification
The implementation of a change often requires **rebooting the operating system**, power cycling the hardware, or restarting a specific service or **daemon** (in Linux). Beyond applying the update, this process <ins>verifies</ins> if the <ins>system</ins> can properly <ins>recover</ins> and <ins>react</ins> during a real power outage.

### Challenges: Legacy Systems and Dependencies
-   **Legacy Applications:** These are <ins>old</ins>, often <ins>unsupported systems</ins> that organizations are <ins>afraid</ins> to <ins>change</ins> because **no one understands them**. By <ins>documenting</ins> these systems, technicians can <ins>bring</ins> them into the <ins>normal support cycle</ins> and become experts in their operation.
-   **Dependencies:** Changes are often complicated by dependencies, where one service cannot be updated until another is. For example, you might need to update firewall firmware before you can update the firewall management software.

### Documentation and Version Control
Because changes occur constantly, existing documentation quickly becomes obsolete. Technicians must update **network diagrams, IP addresses, and procedures** as part of the change process. **Version Control** is used to track specific changes to code, configurations, patches, and registries. This allows the organization to know exactly what was changed and provides a mechanism to revert to a previous version if the update fails.