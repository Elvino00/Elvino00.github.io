## Secure Baselines

Secure baselines are a standardized set of **security settings and best practices** that must be applied to all components of an application instance, including the operating system, network devices, and the application itself.

### Sources for Baselines
Creating a baseline from scratch can be overwhelming, but you do not have to do it alone. Foundations for these baselines can be sourced from:
-   **Application Developers:** They can provide baselines regarding <ins>file system permissions</ins> and <ins>configuration settings</ins> within the <ins>application</ins>.
-   **Operating System Manufacturers:** For instance, Microsoft provides security baselines for Windows and Windows Server.
-   **Appliance Manufacturers:** Manufacturers of purpose-built appliances often provide specific security settings.

### Configuration and Tools
Managing these settings can be complex; for example, Windows 10 has over **3,000 Group Policy settings**, though only a subset are dedicated to security. To manage this, various tools and methods are used:
-   **Microsoft Security Compliance Toolkit (SCT):** A tool used to help deploy security baselines for Windows operating systems.
-   **Active Directory Group Policy:** Used to push settings out to devices on a network.
-   **Mobile Device Management (MDM):** Used to push security settings to mobile devices.

### Deployment and Automation
Because baselines are often large and complex, **automated processes** are recommended. Automation allows an organization to easily deploy these settings across hundreds or even thousands of different devices. While many baselines are based on best practices and rarely change, they must be <ins>updated</ins> when:
-   New vulnerabilities are discovered.
-   Applications are updated.
-   A completely new operating system is installed.

### Maintenance and Auditing
Once a baseline is established, it requires ongoing management:
-   **Testing:** You may need to test baselines prior to deployment, especially if baselines from different manufacturers conflict with one another.
-   **Constant Checking:** You must constantly verify that these baselines are still in place and protecting the application.
-   **Remediation:** If an application instance is found to be out of compliance with the baseline, a plan must be put in place to correct it as soon as possible.
-   **Auditing:** After deployment, regular audits are necessary to ensure the baselines remain in effect.

## Hardening Targets

### General Hardening Principles
-   **Hardening Guides:** Since default configurations are rarely secure, you should use <ins>hardening guides</ins> provided by manufacturers or trusted third parties to <ins>identify</ins> which <ins>settings to change</ins>.
-   **Patch Management:** Regularly install security patches for operating systems, applications, and firmware. For efficiency, security administrators should test patches before deploying them.
-   **Software Minimization:** Always remove software that is not being used, as every piece of software represents a potential vulnerability.
-   **Least Privilege:** Configure devices and accounts to have only the minimum access required to perform their functions.

### Hardening Specific Targets
-   **Mobile Devices:** Hardening includes installing security updates and using **data segmentation** to logically separate personal data from company data. Organizations often use a **Mobile Device Manager (MDM)** to monitor these devices and push updates.
-   **Workstations and Servers:** Both require periodic updates and security patches. For servers specifically, it is critical to enforce **password complexity** and minimum length, disable unused accounts, and implement **Endpoint Detection and Response (EDR)** or antivirus software. Access to servers can also be limited via firewall policies.
-   **Network Infrastructure:** For switches, routers, and firewalls, the most common best practice is to **change default credentials**. Authentication should be configured locally or via a central server. Because patches for these purpose-built appliances are rare, they should be treated as high-priority events.
-   **Cloud-Based Systems:** Hardening focuses on securing the **management workstation**, which often has complete access to the cloud environment. Use EDR to monitor for attacks and maintain **backups**, ideally with a separate cloud provider.
-   **Industrial Systems (SCADA/ICS):** These large-scale systems are often secured through **network isolation**, such as an **air-gap**, which ensures they have no access to the internet or the rest of the organization's network.
-   **Embedded Systems and IoT:** These devices (e.g., smartwatches, HVAC, lighting) often have limited access to their internal operating systems. Hardening involves <ins>prioritizing security patches</ins> and placing these devices on **segmented networks** behind firewalls to limit the scope of a potential exploit.
-   **Real-Time Operating Systems (RTOS):** Used in time-sensitive environments like military or automotive equipment, these should be **isolated** from the rest of the network, run with the minimum number of services, and potentially use host-based security technologies.


## Securing Wireless and Mobile

### Wireless Network Management and Visualization
A critical part of maintaining a wireless network is performing **site surveys** to understand performance and see how neighboring networks might be affecting your signal.
-   **Site Surveys:** These should be performed at **regular intervals** to identify both internal and external access points (APs) and determine the best channels for your network.
-   **Heat Maps:** [These tools](https://res.cloudinary.com/dnhgctqsu/image/upload/q_auto/f_auto/v1776442106/image_2026-04-17_180824758_lgzq8d.png) help visualize <ins>signal strength</ins> throughout a workplace; strong signals are typically shown in yellow or red, while weaker signals are blue. 
-   **Survey Tools:** Software like **NetSpot** or built-in OS utilities can provide metrics such as SSIDs, BSSIDs, channel information, and frequency bands.
-   **Spectrum Analyzers:** These specialized tools are used to identify <ins>interference</ins> from any device, not just access points, that might be using the same frequencies.

### Mobile Device Management (MDM) and Policies
Organizations often use a **Mobile Device Manager (MDM)** to centrally administer mobile devices, whether they are company-owned or personal.
-   **Functionality:** Administrators can use an MDM to roll out applications, disable device features (like cameras) in specific locations, and enforce security policies such as **screen locks and PIN requirements**.
-   **Segmentation:** MDMs allow for <ins>partitioning</ins> a device so that <ins>business data</ins> remains <ins>separate</ins> and protected <ins>from</ins> a <ins>user’s personal information</ins>. This also allows administrators to delete business data without affecting the user's personal files.
-   **Device Lifecycle:** Policies must be in place for when devices are sold or traded in to <ins>ensure data is properly deleted</ins> and <ins>new devices are integrated into the MDM</ins>.

### Deployment Models
There are three primary models for how devices are provided to and used by employees:
-   **BYOD (Bring Your Own Device):** Employees use their personal phones for work. While convenient, these devices <ins>must meet company requirements</ins> to be managed by the MDM to ensure both personal privacy and corporate security.
-   **COPE (Corporate Owned, Personally Enabled):** The company purchases the device and assigns it to the employee, often allowing it to be used for both work and personal purposes.
-   **CYOD (Choose Your Own Device):** A variation of the corporate-owned model where the organization provides a list of approved devices for the user to choose from.

### Security Challenges and Threats
Mobile and wireless technologies introduce several specific security risks:
-   **Physical and Data Risks:** Because mobile devices are small and highly portable, they are easy to hide and can contain massive amounts of data that could be anywhere in the world.
-   **Cellular and Wi-Fi Vulnerabilities:** On 4G and 5G networks, there are concerns regarding traffic monitoring and location tracking. On Wi-Fi, especially in public places like hotels, encryption (such as a **VPN**) is essential to prevent **on-path attacks** or unauthorized traffic monitoring. 
-   **Interference:** Attackers in the same area can cause frequency interference, leading to a **denial of service (DoS) attack**.
-   **Bluetooth:** Referred to as a **Personal Area Network (PAN)**, Bluetooth requires a formal pairing process to prevent unauthorized access to data. Users should be avoid connecting automatically to unknown Bluetooth devices.

## Wireless Security Settings

### Wireless Security Fundamentals
Wireless networks face the inherent risk of attackers listening to communication sent over the air. To mitigate this, private networks typically **encrypt all traffic** so that captured packets remain unreadable. Additionally, wireless protocols must ensure **integrity**, verifying that data received is exactly what was sent, which is often managed through a **Message Integrity Check (MIC)**.

### WPA2 vs. WPA3
-   **WPA2 Vulnerabilities:** WPA2 uses a **four-way handshake** during initial connections. Attackers can capture the hash associated with this handshake and use **GPU processing or cloud-based cracking** to perform an offline **brute force attack** to derive the pre-shared key.
-   **WPA3 Improvements:** WPA3 replaces the four-way handshake with **Simultaneous Authentication of Equals (SAE)**, also known as the **Dragonfly handshake**. SAE uses a derivation of the **[Diffie-Hellman key exchange](https://res.cloudinary.com/dnhgctqsu/image/upload/q_auto/f_auto/v1776590571/DiffieHellman_ggh6a3.png)** to create session keys on the end devices rather than sending hashes across the network, effectively eliminating the risk of brute force attacks.
-   **Encryption in WPA3:** WPA3 introduces **GCMP (Galois Counter Mode Protocol)**, a stronger block cipher mode that includes both data confidentiality and a built-in message integrity check. 
-   **Individualized Security:** In WPA3, every user on the network receives a **different session key**, meaning users cannot see each other's traffic even if they use the same pre-shared key.

### Authentication Methods
Authentication ensures only authorized users can access the network. There are three primary configurations:
-   **Open System:** No authentication or security is used.
-   **Personal (WPA-PSK):** Commonly used at home, where everyone uses the same **pre-shared key** (password).
-   **Enterprise (WPA3-802.1X):** Used in workplaces to provide separate credentials for every individual, often involving a username and password.

### The AAA Framework and 802.1X
Enterprise security often utilizes a **centralized authentication server**, frequently referred to as a **AAA server**, running protocols like **RADIUS, LDAP, or TACACS**. This framework consists of:
-   **Authentication:** Verifying the user's identity, typically via a username and secret password.
-   **Authorization:** Determining which resources the individual is allowed to access once they are on the network.
-   **Accounting:** Tracking metrics such as login/logout times and the amount of data transferred.

**802.1X**, also known as **Network Access Control (NAC)**, is used for both wireless and wired networks to prevent access until credentials are provided. It commonly uses the **Extensible Authentication Protocol (EAP)**, a flexible framework that allows manufacturers to customize the authentication process.

### The 802.1X Authentication Process
This process involves three distinct roles:
1.  **Supplicant:** The user or device attempting to join the network.
2.  **Authenticator:** The device the user first connects to, such as a switch or wireless access point.
3.  **Authentication Server:** The backend AAA server that validates the credentials.

When a connection is attempted, the authenticator blocks access and prompts the supplicant for credentials. The supplicant sends an **EAP response**, which the authenticator passes to the authentication server. Once the server validates the login information, it instructs the authenticator to allow the supplicant onto the network.

## Application Security

IT professionals must maintain a critical **balance between the speed of application development and the security of the final product** to prevent vulnerabilities like buffer overflows and SQL injections. If these issues are not identified during quality assurance testing, researchers or attackers may find and exploit them.

Some methods for securing applications are:

-   **Input Validation:** This involves <ins>analyzing</ins> all <ins>data entering an application</ins>—whether through forms, fields, or freeform text—to <ins>ensure it matches an expected format</ins>, such as the specific length and characters of a zip code. If the input is incorrect, the application should prompt the user for a correction.
-   **Fuzzing:** This is an **automated testing process** where "fuzzers" provide random types of data to input fields to see if the application performs unexpectedly, which indicates a need for stronger input validation.
-   **Secure Cookies:** Cookies are data files used for <ins>tracking and session management</ins> that can be easily <ins>read by third parties</ins>. Because of this, developers should **avoid storing sensitive information** in them and use a **secure attribute** to ensure they are only transferred over encrypted HTTPS connections.
-   **Static Application Security Testing (SAST):** AKA "static code analysis", uses automated analyzers to scan code for "glaring problems" like database injections. However, SAST is not perfect; it can produce **false positives** and may miss implementation-specific vulnerabilities, such as poorly applied cryptography.
-   **Code Signing:** To verify that an application truly originates from a specific developer and has not been altered, developers use **digital signatures and asymmetric encryption**. The operating system checks this signature during installation and alerts the user if the validation fails.
-   **Sandboxing:** This technique isolates an application so it only has access to necessary data. During development, **digital sandboxes** protect the production network from new code. In production, sandboxing limits an application's scope; for instance, a mobile browser might be permitted to see bookmarks but prevented from accessing a user's camera roll.
-   **Monitoring and Logging:** Building monitoring into applications creates **extensive logs** that help identify attacks like SQL injections or unusual behavior, such as unexpected file transfers and spikes in client access.

## Asset Management

### The Purchasing Process
Organizations follow a **formal purchasing process** for acquiring goods and services from third parties. This typically begins with an end user identifying a need and working with IT and purchasing departments to analyze budgets. The process involves **negotiations with suppliers** regarding pricing, licensing terms, and contract details. Once goods are delivered, the organization pays an **invoice** based on agreed-upon terms, such as immediate payment or a 30 to 60-day window.

### Asset Tracking and Inventory
When tangible products are received, they are entered into a **central asset tracking system** to manage them throughout their entire lifecycle.
-   **Ownership:** The system identifies who has control of the asset; for example, a specific laptop is assigned to a specific user's name.
-   **Classification:** Assets are designated by type (laptop, mobile device, etc.) and categorized as either **hardware or software**.
-   **Tax Implications:** Tracking these categories is vital for taxes. Hardware is a **capital expenditure** that may depreciate, whereas software is generally an **operating expense**.
-   **Help Desk Support:** Asset systems help the help desk by <ins>automatically populating support tickets</ins> with a device's make and model.
-   **Enumeration:** The system can track a device as a single entity or <ins>enumerate its internal components</ins>, such as the CPU, memory, and storage drives.
-   **Asset Tags:** Physical tags or barcodes are often attached to devices to assist with identification and serve as a **security feature** if the device is lost or stolen.

### Decommissioning and Data Sanitization
When a device is ready for reuse or disposal, organizations must ensure sensitive data is removed.
-   **Sanitization:** Depending on the next step, an organization might delete sensitive files for internal reuse or use a **secure delete utility** to ensure data can never be recovered.
-   **Physical Destruction:** To guarantee data is gone, drives can be shredded, pulverized, or destroyed manually with a drill or hammer.
-   **Degaussing and Incineration:** Degaussing uses a strong electromagnetic field to delete data and render hard drives unusable, while incineration physically destroys the drive entirely.
-   **Third-Party Services:** For large volumes of devices, organizations often hire third parties who must provide a **certificate of destruction** as formal confirmation that the data is inaccessible.

### Data Retention
In addition to destroying data, organizations must often **retain data** due to legal mandates or best practices.
-   **Mandates:** Regulations may require specific types of data, such as emails or financial records, to be kept for a set number of years.
-   **Policies:** Retention policies cover original sources, copies, and backups.
-   **Operational Benefits:** Retaining data is a best practice for **disaster recovery** and protecting against accidental deletion. Different types of data will require different retention procedures and lengths of time.

## Vulnerability Scanning

### Network Vulnerability Scanning
**Vulnerability scans** are used to determine if a system is potentially <ins>susceptible to an attack</ins> without actually performing the attack itself. This distinguishes them from penetration tests, which do involve active exploitation. A basic example is a **port scan**, which identifies open ports that an attacker might leverage.

Key aspects of these scans include:
-   **Internal and External Scanning:** While scans are often associated with external threats, they should also be performed internally to guard against **insider attacks**.
-   **Data Accuracy:** Scanners provide a large amount of data, but not all of it is accurate. Results must be manually reviewed to identify **false positives**.
-   **Severity Levels:** Reports typically categorize findings by severity, such as **critical, high, medium, low, or informational**. Examples of critical findings include weak SSH host keys due to library bugs or the presence of unsupported, unpatchable operating systems.
-   **Remediation:** Once vulnerabilities are verified, they should be addressed through a formal **change control process** to apply necessary patches.

### Application Security Testing
There are two primary ways application developers check their code for vulnerabilities:

1.  **Static Application Security Testing (SAST):** This involves software reviewing the application’s **source code**. 
    -   **Strengths:** It can identify issues like buffer overflows and database injections.
    -   **Weaknesses:** It often fails to detect implementation errors related to **authentication or cryptography**. Like network scans, SAST results must be <ins>checked for false positives</ins>.

2.  **Dynamic Analysis (Fuzzing):** Also known as fault injecting or robustness testing, this method involves sending **random input** into a running application to see if it crashes or produces unexpected errors. 
    -   **Automation:** Because it requires thousands of iterations, it is almost always an **automated process**.
    -   **Tools:** The Carnegie Mellon Computer Emergency Response Team (CERT) provides a tool called the **Basic Fuzzing Framework (BFF)** for this purpose.

### Software Package Verification
When installing new software, it is vital to **verify the package's contents** to ensure it can be trusted. It's recommend to:
-   **Verify the Source:** Ensure the package comes directly from the manufacturer rather than a third party, which might have added malware.
-   **Lab Testing:** If the contents of a package are uncertain, it should be tested in a **lab environment** before being deployed into production.

## Threat Intelligence

Being an IT security professional means **staying up to date with the latest threats** and the **threat actors** behind them to understand where attacks originate. This intelligence is used to make informed security decisions, such as identifying the need for additional security tools or specific training. Within an organization, researchers use this data to understand risks, while the IT department focuses on protecting against identified threats.

There are several categories of threat intelligence.

### Open-Source Intelligence (OSINT)
OSINT is information **available to anyone** who knows where to look. Some sources include:
-   **The Internet:** Discussion groups (including those hosted by hacking groups), social media posts, and information shared by other researchers.
-   **Government Sources:** Public hearings, reports, and websites, as almost everything produced by the government is open-source and available to the public.
-   **Commercial Data:** Publicly available financial reports or databases containing project details and associated risks.

### Proprietary and Third-Party Services
There are companies built around compiling threat intelligence for a fee. The primary advantage of these services is their ability to **analyze threats across many different organizations simultaneously**. By monitoring the broader threat landscape, they can identify attack trends and **alert your organization** before a threat actually arrives. These companies use a mix of public sources, private data, and sometimes previously classified information that has been made public.

### Collaborative Alliances
Organizations often work together to share intelligence about threats on their own networks. A primary example is the **Cyber Threat Alliance (CTA)**. Members of the CTA gather threat details and put them into a **standard format** for distribution. The alliance validates and scores these submissions to determine a **severity level**, allowing all members to decide how to best use that intelligence for their own network protection.

### The Dark Web
The dark web is an **overlay network** that requires specialized software to access. It serves as a source for detailed threat intelligence because it allows professionals to:
-   **Monitor hacking groups** and their current activities.
-   Identify the specific **tools and techniques** being used to attack organizations.
-   Observe "stores" where stolen information, such as **credit card data**, is sold.
-   Check forums and posts to see if their own **organization's name** is being mentioned in relation to an attack.


## Penetration Testing

**Penetration testing** (or pen testing) is the process of **simulating an attack** on an organization's own systems to see if access can be gained through actual exploits.

### Planning and Rules of Engagement
Before a test begins, it is critical to establish the **Rules of Engagement (RoE)**. This is a formal, written document that ensures everyone understands the following aspects:
-   **Scope:** Specifically which <ins>systems</ins> are <ins>allowed to be tested</ins> ("**in scope**") and which <ins>must not be touched</ins> ("**out of scope**") to ensure production systems remain functional.
-   **Timing:** <ins>When</ins> the tests are allowed to occur, such as only after business hours (e.g., after 6:00 PM) to avoid disrupting operations.
-   **Type of Test:** Whether the test is an on-site <ins>physical breach</ins>, an <ins>internal test</ins>, or an <ins>external test</ins> from outside the facility.
-   **Logistics:** Specific IP address ranges for testing, emergency contacts, and procedures for handling sensitive information discovered during the test.

It's possible to have a standardized overview of the process by looking at the **NIST Technical Guide to Information Security Testing and Assessment** (document 800-115).

### Execution and Risks
The primary objective of a pen test is to **exploit known vulnerabilities** to gain system access. However, exploiting these vulnerabilities can cause **system or service failure**. For example, using a **buffer overflow** to achieve privilege escalation might cause an operating system to crash or become unstable.

Commonly used testing methods include:
-   **Technical Exploits:** Database injections and buffer overflows.
-   **Password Attacks:** Brute force attacks.
-   **Social Engineering:** Attacks that may be conducted entirely over the phone.

### Post-Exploitation Activities
Once a system is successfully compromised, the tester moves into a larger process involving:
-   **Lateral Movement:** Moving from the initial compromised device to <ins>other devices</ins> within the <ins>network</ins>.
-   **Persistence:** Ensuring they can access the system again later. This is often done by creating a **backdoor**, such as adding a new account or changing default passwords, because the original vulnerability might be closed by a software patch.
-   **Pivoting:** Using the first compromised system as a **relay or proxy** (a "pivot point") to bypass firewalls and reach other internal systems.

### Vulnerability Disclosure and Bug Bounties
New vulnerabilities are constantly made public through **CVE (Common Vulnerabilities and Exposures) lists**. The process of disclosure typically follows these steps:
1.  A researcher identifies a vulnerability and notifies the developer.
2.  The developer creates, tests, and publishes a patch.
3.  The vulnerability and its mitigation are then made public.

This process can take weeks or months. To encourage this responsible disclosure, many developers offer **bug bounties**, which are financial rewards for researchers who find and report vulnerabilities to them rather than exposing them publicly immediately.


## Analyzing vulnerabilities

### Identifying False Positives and False Negatives
When reviewing log files or vulnerability reports, it is common to encounter **false positives**, which is information indicating a vulnerability exists when <ins>it actually does not</ins>. It is important to note that vulnerabilities labeled as "low" or "informational" are still valid and should not be dismissed as false positives. Instead, a **false negative** occurs when a vulnerability exists on a system but the scanning software fails to detect it. False negatives are considered much worse than false positives because they leave an organization unaware of a hole that an attacker could exploit. To minimize these issues, it is essential to **update signatures** before performing any scan.

### Vulnerability Scoring and Databases
Vulnerabilities are typically categorized by **severity** (such as critical, high, or low) to help organizations address the most dangerous issues first. Several resources help standardize this process:
-   **CVSS (Common Vulnerability Scoring System):** This system assigns a score between 0 and 10, with 10 being the most critical. Because scoring systems evolve, vulnerabilities may have <ins>multiple scores from different versions</ins>, such as CVSS 2.0 and CVSS 3.x.
-   **NVD (National Vulnerability Database):** Located at [nvd.nist.gov](https://nvd.nist.gov), this database provides CVSS scores and is synchronized with the main CVE list.
-   **CVE (Common Vulnerabilities and Exposures):** Found at [cve.org](https://www.cve.org), this database provides standardized identifiers for vulnerabilities.
-   **Manufacturer Databases:** Many companies, like Microsoft, maintain their own security bulletins and vulnerability databases for their specific products.

### Types of Vulnerability Scans
Scanners can identify vulnerabilities across various platforms:
-   **Application Scans:** These look for holes in <ins>desktop</ins> or <ins>mobile applications</ins>, such as a known bypass vulnerability in WhatsApp desktop.
-   **Web Application Scans:** These target <ins>web-based applications on servers</ins>, such as incorrect access control in a content management system.
-   **Network Device Scans:** These find issues in <ins>firewalls</ins>,<ins>switches</ins>, and <ins>routers</ins>, such as vulnerabilities found in D-Link software.

### Quantifying Risk and Impact
To prioritize fixes, organizations must understand the **exposure factor**, often represented as a percentage. For instance, if a vulnerability could cause a service to be unavailable 50% of the time, it has a 50% exposure factor. If it could completely disable a service and has no patch, it might be considered a 100% exposure factor.

**Context** is also vital for prioritization:
-   **Environment:** A system on a public cloud accessible to the internet has a much higher priority than an isolated system in a test lab.
-   **Business Impact:** Organizations consider whether an application is critical, revenue-generating, or internally versus externally facing.
-   **Ease of Exploit:** Vulnerabilities that are relatively easy to exploit are typically given the highest priority.

### Patching and Risk Tolerance
Because it is impossible to patch every device simultaneously, organizations must determine their **risk tolerance**—the amount of risk they are willing to accept by leaving a vulnerability unpatched while they perform necessary testing. While testing is required to ensure a patch doesn't break the environment, the organization remains vulnerable during that time. If a vulnerability affects many systems and is easy to exploit, the organization will likely have a **low risk tolerance** and may rush the testing process to patch as quickly as possible.

## Vulnerability Remediation

### Patching and Risk Transfer
In most cases, vulnerabilities are mitigated by installing **security patches**, which are typically released on a **standard schedule** (weekly or monthly). However, for severe vulnerabilities or **zero-day exploits**, manufacturers may provide unscheduled patches to immediately address active threats. Organizations must constantly test these updates before deploying them to production environments. When technical remediation isn't enough, some organizations use **cybersecurity insurance** to transfer risk, covering revenue losses, data recovery costs, or legal fees resulting from an attack. These policies generally do not cover intentional acts or direct fund transfers, but they have become more common due to the prevalence of **ransomware**.

### Segmentation and Air Gapping
To limit the scope of a potential attack, organizations use **segmentation** to isolate devices on their own networks or **VLANs**. While this may not stop an initial breach, <ins>it prevents attackers from moving laterally</ins> through the rest of the network. If a patch cannot be installed because it causes software conflicts, a vulnerable segment might be completely **air gapped**, meaning it is moved to a physically separate network with no connectivity to other systems. **Next-generation firewalls** are often used to monitor traffic between segments, allowing administrators to identify and log specific application traffic.

### Compensating Controls and Service Management
If a system cannot be patched and no internal firewall is available, other **compensating controls** can be used. These include:
-   **Disabling the vulnerable service:** This prevents exploitation but makes the service unavailable to users.
-   **Revoking access:** Administrators can stop all users from accessing a specific application.
-   **Edge firewall policies:** Restricting outside access to internal services.
-   **Access Control Lists (ACLs):** Implementing security rules on routers or installing software-based firewalls on the application servers themselves.

### Exemptions and the Decision Process
Sometimes, a security or change control committee may grant a formal **exemption** for a vulnerability, deciding not to patch it to maintain **service uptime and availability**. This decision is based on a collective risk assessment; for example, a vulnerability that requires **local access** to a server locked in a secure data center might be deemed a "reasonable security risk". These exemptions are rarely made by one person and require a group to weigh the risks against operational needs.

### Verification and Reporting
After patches are deployed, it is a best practice to perform a **vulnerability scan** to confirm the patch was installed properly and to find any systems that were missed. Verification can also involve checking the feedback from the patching system or performing **manual audits** by logging into systems directly. For large organizations with thousands of devices, a **reporting system** is essential to monitor:
-   The total number of identified vulnerabilities.
-   The ratio of patched vs. unpatched systems.
-   New threat notifications and patch deployment errors.
-   Current exceptions and exemptions.

## Security Monitoring

Security monitoring is a continuous process required because attackers are <ins>constantly attempting to gain access</ins> to systems and services. To maintain a strong security posture, organizations use **dashboards** to view real-time activity and verify that all network activity is <ins>legitimate</ins>.

### Key Areas of Monitoring
Effective monitoring involves several critical points across the infrastructure:
-   **Authentications and Logins:** Tracking who is logging in and from where is vital; for instance, seeing authentications from a country where the organization has no employees is a major cause for concern.
-   **Systems and Services:** Monitoring includes checking running services, activity levels, backup completion status, and software versions to determine if **patching** is necessary.
-   **Applications:** It is important to monitor application availability and the amount of traffic being transferred, as sudden spikes in data transfer can indicate an attacker is attempting to **exfiltrate data**.
-   **Infrastructure:** This involves tracking remote access, such as VPN connections, to distinguish between employees, vendors, and guests. Firewalls and intrusion prevention systems (IPS) also provide warnings through spikes in attack activity.

### Consolidating Data with SIEM
Monitoring diverse systems is challenging because they use different log formats. A **Security Information and Event Manager (SIEM)** solves this by consolidating log files from firewalls, switches, servers, and routers into one central database. This consolidation allows for:
-   **Reporting and Correlation:** Organizations can compare and correlate data across different systems, such as linking a VPN login to the specific information accessed on the network.
-   **Baselines and Alerts:** By measuring normal data transfer levels, a SIEM can trigger an alert if those numbers are exceeded.

### Vulnerability Scanning and Reporting
Because mobile devices like laptops and tablets are constantly in motion, tracking vulnerabilities is difficult. Organizations use software to constantly scan devices for operating system versions, drivers, and installed applications. 
-   **Actionable Reports:** These scans generate reports that <ins>identify devices out of compliance</ins> with security patches and outline the <ins>actions needed</ins> to <ins>fix them</ins>. 
-   **Ad Hoc Reporting:** This is used for "what if" analysis, such as determining <ins>how many systems will be vulnerable</ins> once an operating system reaches its **end of life**.

### Detection and Response
The reality of security is that it takes an average of **nine months** for a company to identify and contain a breach. Attackers often stay hidden in a network for long periods, making long-term backup strategies and data collection mandates essential. 
-   **Real-Time Alerts:** Immediate notifications (via SMS or email) should be generated for unusual activity, such as brute force attacks or large data transfers out of a data center.
-   **Quarantine:** A common reaction to a high-priority alarm is to **quarantine** the affected system to prevent the attacker from moving to other devices on the network.
-   **Tuning:** Monitoring requires a balancing act to minimize **false positives** (inaccurate alerts) and **false negatives** (missed events). Proper tuning ensures that alerts are accurate and allow for immediate decision-making.

## Security Tools

### SCAP and Automation
To address the issue of different security tools using different terminology for the same vulnerabilities, the industry uses the **Security Content Automation Protocol (SCAP)**. Maintained by **NIST**, SCAP provides a common language for firewalls, IPS, and scanners to communicate. This standardization allows for **automated patching** and vulnerability removal without human intervention, which is essential for managing thousands of devices across multiple operating systems.

### Security Benchmarks and Compliance
**Security benchmarks** are sets of best practices used to configure systems as securely as possible right out of the box. The **Center for Internet Security (CIS)** provides an extensive library of these benchmarks for operating systems, applications, and mobile devices. To ensure ongoing compliance, organizations use two types of checks:
-   **Agent-based:** Software is permanently installed and always running to monitor compliance, but it requires ongoing maintenance.
-   **Agentless:** This check runs in the system's memory during events like a VPN login and removes itself once finished, requiring no permanent installation or maintenance.

### Logging and Monitoring Tools
Several tools are used to consolidate and analyze network data:
-   **SIEM (Security Information and Event Manager):** This tool centralizes log files into a database for **reporting and correlation**. It allows administrators to see how different events (like a VPN login and a firewall block) relate and provides data for **forensics reports** to understand past security events.
-   **SNMP (Simple Network Management Protocol):** This protocol is used to monitor and manage network devices. SNMP objects like network switches, routers, and other devices are listed in a **Management Information Base (MIB)** using **Object Identifiers (OIDs)**. It typically works via **polling** over UDP port 161. It also supports **SNMP traps**, which proactively send alarms to a management station over UDP port 162 when specific thresholds are met.
-   **NetFlow:** Used to monitor traffic flows and application-level statistics. Probes collect data via port mirroring (SPAN) or physical taps and send it to a **NetFlow collector** to generate reports on the "top 10" conversations and endpoints.

### Security and Data Protection Software
-   **Antivirus and Anti-malware:** These tools identify malicious code like Trojans, worms, and ransomware. In modern usage, these two terms are largely interchangeable.
-   **DLP (Data Loss Prevention):** DLP <ins>monitors and blocks the transfer of sensitive data</ins>, such as Social Security numbers or credit card info, in real-time. It can be deployed on endpoints, as network appliances, or in the cloud.
-   **Vulnerability Scanners:** These are minimally invasive tools that <ins>identify potential vulnerabilities</ins> and perform <ins>port scans</ins> without exploiting them. They should be run regularly from both internal and external perspectives to find critical issues like unsupported operating systems.

## Firewalls

**Network-based firewalls** are appliances that sit inline in a network to <ins>allow</ins> or <ins>disallow traffic</ins> based on security decisions. While traditional firewalls make these decisions based on **port numbers**, modern **Next-Generation Firewalls (NGFW)** can analyze traffic to recognize the specific **application** being used. NGFWs are also known as application layer gateways, stateful multi-layer inspection devices, or deep packet inspection devices.

### Firewall Capabilities and Routing
Beyond basic security, firewalls often provide additional services:
-   **VPN Services:** They can act as **VPN endpoints or concentrators** for point-to-point connections or remote access.
-   **Routing:** Many function as **Layer 3 devices (routers)** at the network's ingress/egress point, performing **Network Address Translation (NAT)** and dynamic routing.
-   **Application Awareness:** Traditional firewalls focus on ports (e.g., TCP 22 for SSH, TCP 80/443 for Web, UDP 53 for DNS, or UDP 123 for NTP), whereas NGFWs identify the traffic as the actual application regardless of the port.

### Rule Bases and Access Control Lists (ACLs)
Firewall policies, also called **Access Control Lists (ACLs)**, evaluate traffic against a list of rules. 
-   **Evaluation Order:** Rules are processed from **top to bottom**. Because the firewall stops at the first match, **specific rules** should be placed at the top, while broad rules go at the bottom.
-   **Implicit Deny:** Most firewalls include an "implicit deny" at the end of the rule base, meaning any traffic that does not match a specific rule is **automatically dropped**.
-   **Rule Parameters:** A rule can include the source/destination IP, port numbers (services), the associated user, the application, or web categories.

### Network Placement and Screened Subnets
Firewalls are typically placed at the **ingress/egress point** between the internet and the internal network. To protect sensitive data, organizations often use a **screened subnet** (formerly known as a DMZ). This subnet hosts services that must be accessed from the internet, preventing external users from reaching the internal network where confidential data resides.

### Intrusion Prevention Systems (IPS)
Modern NGFWs often include an **Intrusion Prevention System (IPS)**. 
-   **Detection Methods:** An IPS monitors traffic in real-time using **signatures** to recognize specific malware (like the Conficker worm) or by identifying **anomalies** (such as database injections) even if a signature does not exist.
-   **Management:** IPS rule bases contain thousands of signatures that can be **grouped** to make broad security decisions, such as blocking all traffic associated with database injections.
-   **Tuning:** Administrators must customize these rules to find a balance between high security and avoiding **false positives**. Rules can specifically target threats like malware or worms attempting to log in via protocols like FTP.

## Web Filtering

### Core Functions and Management
-   **Purpose:** Filters can allow or disallow access based on the <ins>data inside web pages</ins>, rather than just the application itself. They are used to block "known-bad" sites containing viruses or malware and, in home environments, are often referred to as **parental controls**.
-   **Allow and Block Lists:** Administrators can manage access by adding individual **Uniform Resource Locators (URLs)** or **Fully Qualified Domain Names (FQDNs)** to allow or block lists. 
-   **Category-Based Filtering:** Because individual lists are hard to manage, URLs are often grouped into **categories** (e.g., gambling, hacking, travel, or education). Organizations can then apply rules to these categories, such as allowing educational sites while blocking gambling sites or logging alerts for "home and garden" visits.
-   **Reputation Filtering:** Some filters evaluate a site's **perceived risk**. Sites are assigned ratings (e.g., trustworthy, suspicious, or high-risk) through automated scans or manual assignment, allowing for granular control based on a site's reputation.

### Deployment Methods
There are several ways content filtering is implemented:
-   **Next-Generation Firewalls (NGFW):** Many firewalls now include URL filtering, Intrusion Prevention Systems (IPS), and standard firewall rules in a single device.
-   **Agent-Based Filtering:** For mobile or remote workers who are not behind a corporate firewall, agents are installed directly on their devices. These agents are managed centrally and make filtering decisions locally on the user's system.
-   **Proxies:** A **proxy** sits between the user and the external network, making requests on the user's behalf.
    -   **Forward Proxies:** Internal proxies that receive a user's request, fetch the data, check it for malware or URL violations, and then pass it to the user.
    -   **Explicit vs. Transparent:** An **explicit proxy** requires manual configuration in the application, while a **transparent proxy** works without the user's knowledge or special client configuration.
    -   **Additional Features:** Proxies can provide **caching** (saving local copies of pages to speed up future requests) and **access control** based on IP addresses or credentials.
-   **DNS Filtering:** This method uses the **Domain Name System (DNS)** to block access. If a user tries to access a malicious site, the DNS server—updated with real-time threat intelligence—refuses to provide the correct IP address, preventing the connection. A key benefit is that it can also block malicious software from communicating with **command and control servers**, even if that software isn't using a web browser.

## Operating System Security

### Windows: Active Directory and Group Policy
**Active Directory** serves as a central, redundant database that <ins>catalogs all components of a network</ins>, including computers, devices, user accounts, file shares, printers, and security groups. This central resource allows administrators to:
-   **Manage authentication:** Users log in to devices and resources using credentials defined within the database.
-   **Assign access permissions:** Permissions can be assigned to individual users or entire groups.
-   **Handle account management:** Functions such as adding accounts, modifying passwords, and removing accounts are performed here.

**Group Policy** is a <ins>set of security policies</ins> overlaid on the computers and users within Active Directory. Managed through the **Group Policy Management Editor**, it allows for the configuration of:
-   **Login scripts** that run when a user connects to the network.
-   **Network configurations**, such as Quality of Service (QoS).
-   **Security parameters** that all network users and devices must follow.

Together, Active Directory and Group Policy provide a comprehensive control mechanism for managing network configuration and security policies.

### Linux: DAC, MAC, and SELinux
By default, the Linux operating system uses **Discretionary Access Control (DAC)**, which allows users to assign rights and permissions to resources at their own discretion. However, highly secure environments often require **Mandatory Access Control (MAC)**, where a central administrator assigns all rights and permissions.

**Security-Enhanced Linux (SELinux)** is an open-source tool that can be installed on many Linux distributions to enable MAC. Key benefits include:
-   **Least Privilege:** SELinux ensures users have only the permissions necessary for their specific job.
-   **Containment:** If a security breach or malicious code occurs, its scope is limited, preventing it from affecting the entire device.

## Secure Protocols

### The Risk of Insecure Protocols
Many common protocols send data "in the clear," meaning the information is not encrypted and can be easily read if intercepted. Examples of **insecure protocols** include:
-   **Telnet**
-   **FTP** (File Transfer Protocol)
-   **SMTP** and **IMAP/POP3** (Email)
-   **HTTP** (Web browsing)

### Secure Alternatives
To protect data, you should always aim to use secure versions of these protocols that utilize **encryption**. The source recommends the following transitions:
-   Instead of Telnet, use **SSH (Secure Shell)**.
-   Instead of HTTP, use **HTTPS**.
-   Instead of IMAP, use **IMAPS**.
-   Instead of FTP, use **SFTP**.

### Identifying and Verifying Traffic
One way to identify if a protocol is secure is by its **port number**, though this is not a guarantee. 
-   **Port 80** is typically used for **HTTP** (insecure).
-   **Port 443** is typically used for **HTTPS** (secure).

Because port numbers alone do not guarantee security, it's suggested to perform a **packet capture**. If the data inside the packet is readable, the protocol is insecure; if it is encrypted, only the headers should be visible while the data remains protected.

### Network-Level Encryption
If an application does not support encryption, you can encrypt all traffic at the network level:
-   **Wireless Security:** Using **WPA3** on a wireless access point ensures all data sent over the air is encrypted, unlike an "open" access point where traffic is sent in the clear.
-   **VPN (Virtual Private Network):** A VPN creates an **encrypted tunnel** between a device and a VPN concentrator. While this protects all traffic sent over that specific link, it may require additional software or a subscription to a third-party service.

## Email Security

Original email protocols lack built-in security checks, making it easy for attackers to **spoof** messages. Spoofing occurs when an email appears to be from a <ins>trusted</ins> friend, family member, or organization, but <ins>did not actually originate from them</ins>. To counter this, organizations implement additional security features through their DNS servers.

### Mail Gateways
A **mail gateway** acts as a "gatekeeper" for an organization's email. It intercepts all incoming messages to determine if they are legitimate or should be sent to a spam folder. These gateways can be managed on-premises within a **screened subnet** or provided as a third-party cloud service.

### DNS Security Records
To verify the legitimacy of a sender, domain owners use three primary types of DNS text (TXT) records:

-   **SPF (Sender Policy Framework):** This record defines <ins>which</ins> specific <ins>email servers</ins> are <ins>authorized</ins> to **send mail** on behalf of a domain. When a mail gateway receives an email, it queries the sender’s DNS to see if the originating server is <ins>listed</ins> in the SPF record.
-   **DKIM (DomainKeys Identified Mail):** This mechanism adds a **digital signature** to the transport process between mail servers. The signature is not typically visible in the message itself but is found in the email headers. The receiving server uses a **public key** found in the sender's DNS TXT record to validate the signature and confirm the email's origin.
-   **DMARC (Domain-based Message Authentication, Reporting, and Conformance):** DMARC serves as an extension of SPF and DKIM. It <ins>provides instructions</ins> to the <ins>receiving</ins> mail server on what to do if an email <ins>fails</ins> SPF or DKIM validation. Domain owners can choose to have failed messages **accepted, quarantined (sent to spam), or rejected**.

### Reporting and Monitoring
DMARC also includes a reporting feature that allows domain owners to receive **compliance reports**. These reports aggregate statistics on how many messages validated properly and how many were identified as potential spoofing attempts. This data helps domain owners understand the disposition of their email traffic across the internet.