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


[Tabella SP 800-171 Rev 2](https://res.cloudinary.com/dnhgctqsu/image/upload/Screenshot_From_2026-01-24_19-14-17_exoc0r.png)

### The Analysis and Reporting Process
1. **Comparison**: The analysis begins by comparing existing systems against the baseline to identify weaknesses and determine effective processes to compensate for them

2. **Bridging the Gap**: The analysis must determine the "<ins>path</ins>" to reach the desired state, which often requires time, money, new equipment, and formal Change Control

3. **The Gap Analysis Report**: This final document summarizes all discoveries
It includes:
    - The current status of security objectives
    - A pathway/recommendations for moving forward
    - Visual Prioritization: Reports often use color-coding to show which locations or requirements need the most work:
        - **Red**: Needs significant work (highest priority for improvement)
        - **Yellow**: Midpoint
        - **Green**: Relatively close to meeting the baseline

[Gap Analysis Report](https://res.cloudinary.com/dnhgctqsu/image/upload/v1769278652/tabella_wuznth.png)