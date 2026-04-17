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
-   **Bluetooth:** Referred to as a **Personal Area Network (PAN)**, Bluetooth requires a formal pairing process to prevent unauthorized access to data. Users are cautioned against automatically connecting to unknown Bluetooth devices.