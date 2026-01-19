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
[Creazione Firma Digitale](https://res.cloudinary.com/dnhgctqsu/image/upload/Alice_and_Bob_a8krb8.png)
1. **Hash Creation:** Alice's system creates a hash of the original message ("You're hired, Bob").
2. **Hash Encryption:** The hash is encrypted with Alice's private key. This encrypted hash becomes the digital signature.
3. **Sending:** Alice sends the cleartext message along with the digital signature to Bob.
4. **Decryption and Verification by Bob:** Bob receives the message and uses **Alice's public key** to decrypt the signature and obtain the original hash.
5. **Comparison:** Bob independently generates a new hash from the received message and compares it with the one obtained from Alice's signature.

[Verifica Firma digitale](https://res.cloudinary.com/dnhgctqsu/image/upload/Screenshot_From_2026-01-19_18-42-51_n4uif2.png)

If the two hashes match, Bob has mathematical proof that the message **has not been altered** and that **it must have been sent by Alice**, since only she possesses the private key needed to create that specific signature. This process ensures that neither Alice nor Bob can deny the transaction, guaranteeing non-repudiation.