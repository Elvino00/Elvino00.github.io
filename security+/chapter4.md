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