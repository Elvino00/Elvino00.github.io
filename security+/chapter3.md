## Cloud Infrastructures

### Shared Responsibility Model
Cloud providers use a [responsibility matrix](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774540120/Responsability_Matrix_dfuzzt.png) to define whether the <ins>provider</ins> or the <ins>customer</ins> is <ins>responsible</ins> for specific <ins>security aspects</ins>. This varies by service type:
-   **SaaS (Software as a Service):** The cloud <ins>provider handles almost everything</ins>, including the operating system and applications.
-   **PaaS (Platform as a Service):** The <ins>provider</ins> manages the underlying infrastructure and <ins>OS</ins>, while the <ins>customer</ins> manages the <ins>application</ins>.
-   **IaaS (Infrastructure as a Service):** The **customer is responsible** for the <ins>operating system</ins> and everything installed on it.
-   **On-premises:** The <ins>customer</ins> is responsible for <ins>every layer</ins> of the technology stack.
-   **Accounts and Identities:** Regardless of the cloud model used, the **customer is always responsible** for managing their own accounts and identities.

### Hybrid and Multi-Cloud Management
Using multiple cloud providers, often referred to as a **hybrid cloud**, increases flexibility but adds significant **complexity**.
-   Providers generally do not communicate directly, meaning settings for authentication, server configurations, and firewalls must often be **manually configured** for each separate provider.
-   **Logging** is difficult to manage because different providers use different terminology and formats for their security logs.
-   Data transferred between different cloud providers often traverses the **public internet**, requiring careful protection of **data in transit**.

### Third-Party Vendors
Organizations frequently use <ins>third-party applications</ins> or devices, such as firewalls, to <ins>secure</ins> their cloud-hosted <ins>apps</ins>.
-   A **vendor risk management policy** is recommended to <ins>maintain security</ins> when using these third-party technologies.
-   **Incident response** processes must be updated to <ins>include</ins> these <ins>third parties</ins>.
-   Continuous **monitoring** is necessary to <ins>ensure</ins> the <ins>security</ins> and <ins>availability</ins> of these systems.

### Infrastructure as Code (IaC)
**Infrastructure as code** allows a cloud environment to be <ins>defined</ins> using <ins>code rather than hardware descriptions</ins>. 
-   It **simplifies** building and modifying infrastructure by allowing **changes** to be made **directly in the code**.
-   Once a "perfect" version of an application instance is <ins>defined in code</ins>, it can be easily **rebuilt on any cloud provider** at any time.

### Serverless Architecture
In a **serverless** environment, the application is broken down into **individual autonomous functions** rather than being hosted on traditional servers.
-   There is **less emphasis on the operating system**, as functions can run in <ins>any</ins> appropriate <ins>OS</ins> environment.
-   Functions are only triggered when <ins>needed</ins>, which can lead to significant **savings in time and money**.
-   Most security for a serverless architecture is managed within the **cloud itself**.

### Microservices vs. Monolithic Architectures
-   **Monolithic Applications:** Traditional applications where all functions—such as the user interface, logic, and login—are contained within **one single executable**. These are often large and require complex change control processes for updates.
-   **Microservices:** Applications are broken into independent services that communicate via **APIs** (Application Programming Interfaces).
-   **Benefits:** This model offers better **scalability**, as individual services can be scaled based on demand, and improved **resilience**, because the rest of the app continues to function even if one microservice fails.
-   **Security:** Microservices allow for **granular security**, where specific security processes are tailored to the function of each service (e.g., one set of rules for authentication and another for database access).

[Monolithic Architecture](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774545878/Monolithic_Architecture_gnezj6.png) vs [Microservices Architecture](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774545884/Microservice_Architecture_u65kqr.png)

## Network Infrastructures

### Network Isolation and Air Gaps
-   **Physical Isolation:** To prevent an attacker from moving laterally between devices, a network can be designed with an **air gap**, meaning devices are <ins>physically separated</ins> and have <ins>no connection between them</ins>.
-   **Use Cases:** Air gaps are used for high-security environments, such as <ins>separating web servers from database servers</ins> or keeping <ins>different customers' data separate</ins> in a managed service provider (MSP) environment.
-   **Connectivity Requirements:** If air-gapped devices must eventually communicate, they require a <ins>direct connection</ins> or must <ins>pass</ins> data <ins>through</ins> a <ins>router</ins> or another switch.

### Segmentation and VLANs
-   **Scalability Issues:** While physical isolation is secure, it <ins>does not scale well</ins> because every new segment or customer would <ins>require</ins> a new <ins>physical switch</ins>.
-   **Virtual Local Area Networks (VLANs):** Switches use VLANs to provide <ins>segmentation</ins> on a single physical device. By assigning specific interfaces to different VLANs, a network admin can achieve the **same effect as having separate physical switches**. This simplifies network design and <ins>reduces the amount of hardware needed</ins>.

### Software Defined Networking (SDN) and Planes of Operation
SDN allows physical networking functions to be <ins>turned into software</ins> that can be used in cloud environments. This is achieved by separating a device's functions into **three planes of operation**:

1.  **Data Plane (Infrastructure Layer):** It's responsible for **forwarding traffic** from one device to another. It handles tasks like <ins>Network Address Translation</ins> (NAT), encryption, and trunking.
2.  **Control Plane:** This plane manages the data plane by maintaining **routing tables**, session tables, and dynamic routing updates. It essentially tells the data plane <ins>how to get data from point A to point B</ins>.
3.  **Management Plane:** This is where **configuration changes** are made. Administrators connect to this plane via SSH, SNMP, or APIs to dictate how the control plane should operate.

### Cloud Infrastructure
-   **Dynamic Deployment:** In cloud-based environments using SDN, infrastructure like **firewalls and load balancers** can be created dynamically with the click of a button.
-   **Traffic Control:** These virtual devices allow for granular control, such as placing a firewall between the internet and a load balancer, or between web servers and database servers, to secure the flow of traffic.


## Infrastructure Considerations

### Availability and Resilience
**Availability** is the expectation that <ins>systems</ins> and resources <ins>are up</ins>, running, and accessible to the right people. Organizations prioritize this by investing in redundant systems and complex monitoring tools to track "uptime," often measured as a percentage (e.g., 99.999%). When outages occur, a key metric for resilience is **Mean Time to Repair (MTTR)**, which measures <ins>how long</ins> it takes to <ins>replace or fix</ins> unavailable <ins>components</ins>. Determining recovery time requires identifying the root cause, such as hardware failure or software bugs. Efficient recovery processes, such as using **image backups** instead of manual OS reinstallation, can significantly <ins>reduce</ins> downtime and costs.

### Cost and Risk Management
Calculating the **cost** of technology is complex and includes initial installation, ongoing maintenance (internal or manufacturer-led), and replacement expenses. Financial planning must also account for **depreciation, capital expenses, operational costs, and tax implications**. To manage the financial risk of security events like ransomware, organizations often use **cybersecurity insurance**. This insurance can help recoup losses from business downtime and cover legal fees resulting from customer-related proceedings.

### Performance and Scalability
-   **Responsiveness:** This refers to <ins>how quickly a service responds to a request</ins>, which is a critical metric for interactive applications. Responsiveness varies based on the specific function being performed and may involve multiple internal steps.
-   **Elasticity and Scalability:** To handle varying usage loads, organizations use **elasticity** to expand or contract an application's resources. **Orchestration** allows for the automated, programmatic building of cloud-based infrastructure on demand. 
-   **Security Monitoring:** As applications scale, <ins>security tools</ins> must be </ins>extended to monitor the entire instance, including all added resources.

### Maintenance and Patching
The **patching process** is essential for <ins>fixing bugs</ins> and providing <ins>security updates</ins>. Organizations typically test patches in a non-production environment before deploying them to prevent breaking existing systems. Systems that are not patched are left vulnerable to exploits. Some **embedded systems** (like HVAC controls or time clocks) are difficult to patch because they lack easy connectivity or manufacturer support; these systems require additional layers of security, such as **firewalls**, to mitigate risk.

### Core Infrastructure: Power and Compute
-   **Power:** Electricity is a fundamental requirement that must be monitored and planned for with the help of licensed electricians. To protect against power loss, organizations use **Uninterruptible Power Supplies (UPS)** or generators.
-   **Compute:** In cloud environments, the "thinking" and data processing are handled by **compute engines**. These components can consist of single or multiple processors and are scaled to meet the specific requirements of an application.

### Operational Planning
Successful deployment requires careful **project management and change control**. Applications are rarely single entities; they consist of many moving parts, including web servers, databases, caching servers, and firewalls. Missing any resource or step during the planning phase can delay the entire implementation.

## Secure Infrastructures

There are various strategies and technologies used to design and maintain **secure network infrastructures**. While every network is unique based on its organizational goals—such as those in manufacturing versus medical environments—they share common security elements like the use of **firewalls** for network segmentation.

### Security Technologies and Zones
Beyond firewalls, several other devices contribute to a secure computing environment, including **honeypots, jump servers, sensors, and load balancers**. A key concept in secure design is the [security zone](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774881710/Security_Zones_ygw3pf.png), which logically <ins>separates</ins> devices based on their <ins>use</ins> or <ins>access type</ins> rather than just their IP address range.

-   **Zone Types:** Common designations include **trusted vs. untrusted** or **internal vs. external**. Organizations can create more granular zones for specific needs, such as **inside, internet, servers, databases, or screened** zones.
-   **Rule Bases:** These zones make it easier to <ins>maintain</ins> large rule bases</ins> that dictate <ins>how data moves</ins>. For instance, a rule might allow data to flow from a trusted zone to an untrusted zone, or from the internet to a **screened subnet** (screened zone).
-   **Granularity:** Increasing the number of zones allows for more precise security rules, making it harder for attackers to find openings.

### Managing the Attack Surface
The **attack surface** is the combination of all <ins>potential openings</ins> an attacker <ins>might exploit</ins> to <ins>enter a network</ins>. These openings include:
-   **Application code** and **open ports** on a server.
-   The **authentication process**.
-   **Human error**, such as an improperly configured firewall rule.

To minimize the attack surface, organizations should **audit code**, **block unnecessary ports**, and **monitor traffic in real time** to identify who is entering the network and what applications are in use.

### Secure Connectivity
Security must also be integrated into the physical and logical connectivity of the network:
-   **Cabling Protections:** Physical and logical protections should be applied to network cabling and drops in facilities to prevent unauthorized "tapping" into the network.
-   **Encryption:** Because attackers who tap into a network can watch traffic, **application-level encryption** is essential to ensure that captured packets remain unreadable.
-   **Remote Access:** For remote sites or off-site users, additional encryption is used through **IPsec tunnels** or **VPN concentrators** to provide secure connections to the corporate office.

## Intrusion Prevention

An **Intrusion Prevention System (IPS)** is designed to monitor network traffic in **real time** and **immediately block** anything identified as a dangerous exploit, such as known vulnerabilities, buffer overflows, or SQL injections. This differs from an **Intrusion Detection System (IDS)**, which can alert you to these vulnerabilities but **cannot block** the traffic.

There are two primary ways to deploy these systems.

### Active Monitoring (Inline)
In an **active monitoring** [configuration](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774885333/Active_Monitoring_IPS_ul8nhz.png), the IPS is placed **inline**—for example, positioned between a firewall and a core switch—so that all traffic must pass through it. The IPS evaluates the traffic and, if it identifies an attack, **removes it from the network** before it reaches the destination. While this is often the default configuration, it presents challenges if the device fails due to power loss, hardware issues, or software bugs. There are two ways an inline device might handle failure:
-   **Fail-open:** Data continues to flow through the connection even if the device crashes. This keeps the network running, but **security processes will not occur**.
-   **Fail-closed:** The **network connection is severed** if the device fails, meaning no communication can pass through that link.

### Passive Monitoring (Out-of-Band)
Organizations may prefer **passive monitoring** if they are concerned that an inline IPS might cause downtime or mistakenly block legitimate traffic. In this [setup](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774885333/Passive_Monitoring_IPS_kyndof.png), often referred to as an **IDS design**, the IPS is not inline with the normal network communication. Instead, it receives a **copy of the traffic** through one of the following methods:
-   **Port mirror or SPAN** (Switch Port Analyzer): A function built into a switch to duplicate traffic.
-   **Network tap:** A physical device used to break into a connection to copy data.

While passive monitoring ensures that an IPS failure **cannot cause network downtime**, it also means the system has **limited capabilities for blocking traffic** in real time; it can identify and alert on malicious activity, but the traffic will still reach its destination.

## Network Appliances

### Jump Servers
A **jump server** is a <ins>hardened</ins> and secured <ins>device</ins> located inside a private network that is <ins>accessible from the outside</ins>. Its primary purpose is to allow authorized individuals to **connect to and manage internal devices** from an external location. This typically involves a two-step process: an external <ins>client connects to</ins> the <ins>jump server</ins> first, and from there, they can <ins>use protocols</ins> like SSH to <ins>access</ins> and <ins>configure internal servers</ins>. Because it acts as a gateway, it is critical that jump servers are properly secured to prevent unauthorized external actors from gaining access to the rest of the internal network.

### Proxy Servers
A **proxy server** acts as an <ins>intermediary</ins> between two devices, making requests on behalf of a user. They provide several benefits and come in various configurations:

-   **Primary Functions:** Proxies can provide **caching**, which saves bandwidth by <ins>storing</ins> and <ins>serving</ins> identical <ins>requests locally</ins> rather than fetching them from the internet every time. They also offer security features like **URL filtering** and **content scanning** to block malicious traffic or exploits.
-   **Configuration Types:**
    -   **Explicit Proxy:** Requires the user to explicitly name the proxy's IP address or name within their application or operating system.
    -   **Transparent Proxy:** Operates invisibly to the end user, automatically intercepting requests without requiring any client-side configuration.
-   **Directional Types:**
    -   [Forward (Internal) Proxy](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774950824/Forward_Proxy_ge66f8.png): Sits inside the network and manages outbound traffic from internal users to the internet. It examines the response from the internet and forwards it to the user only if it is legitimate.
    -   [Reverse Proxy](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774950824/Reverse_Proxy_le8gzv.png): Manages inbound traffic from the internet to internal services, such as a web server. It provides additional security by dropping malicious traffic before it reaches the server and can also use caching to reduce the server's load.
-   **Protocol-Specific Proxies:**
    -   **NAT (Network Address Translation):** A simple proxy that converts between internal and external IP addresses on routers.
    -   **Application-Level Proxy:** Understands specific protocols (e.g., HTTP, HTTPS, FTP) to provide more specialized handling.
-   [Open Proxies](https://res.cloudinary.com/dnhgctqsu/image/upload/v1774950824/Open_Proxy_n2g6i9.png): These are available to anyone on the internet and are often used to bypass security controls. However, they pose significant risks because they are managed by unknown third parties who could inject advertisements or **malicious code** into the traffic. Most organizations block access to open proxies to mitigate these risks.

### Load Balancers
A **load balancer** <ins>distributes</ins> incoming <ins>traffic</ins> across multiple servers, such as a web server farm, to maintain efficiency and <ins>ensure</ins> the <ins>load</ins> remains <ins>even</ins>.

-   **Fault Tolerance:** If a server <ins>fails</ins>, the load balancer identifies the failure and quickly <ins>redistributes</ins> the <ins>traffic</ins> to the remaining <ins>healthy servers</ins>.
-   **Operational Modes:** 
    -   **Active-Active:** All servers connected to the load balancer are used simultaneously.
    -   **Active-Passive:** Some servers are active while others remain on standby (passive). If an active server fails, the load balancer automatically switches a standby server to active status.
-   **Advanced Features:**
    -   **TCP Offloading:** The load balancer maintains a <ins>single open TCP connection</ins> instead of creating new ones for every user request, improving efficiency.
    -   **SSL Offloading:** The load balancer <ins>handles</ins> the heavy task of <ins>encryption and decryption centrally</ins>, sending decrypted traffic to the internal servers.
    -   **Content Switching:** The load balancer can <ins>identify</ins> the <ins>type</ins> of <ins>request</ins> and <ins>direct</ins> it to a <ins>specific server</ins> optimized for that task.

### Sensors and Collectors
For network management and monitoring, organizations use **sensors** and **collectors**.

-   **Sensors:** These can be built into existing devices like switches and firewalls, or they can be standalone devices. Their job is to gather statistics and data from network traffic, logs, and security systems like IPS.
-   **Collectors:** This is a central database where all sensor data is sent for storage and analysis.
-   **SIEM (Security Information and Event Manager):** A SIEM acts as a powerful collector that consolidates data from diverse devices into a single database. It provides reporting tools that allow administrators to **correlate and compare data** to identify events like failed authentications or port scans across the entire network.

## Port Security

Security measures can be applied to individual interfaces on a network switch or connections to a wireless access point. This type of security is highly effective because it requires **authentication** before any user or device can access network resources. While common in wireless environments, it is also implemented on traditional wired switches.

The technological framework behind port security includes:
-   **EAP (Extensible Authentication Protocol):** A framework for authentication that works across many different network types and manufacturers.
-   **802.1X:** An IEEE standard often integrated with EAP to manage the authentication process. It is also known as **NAC (Network Access Control)** or **Port-based Network Access Control**. This standard ensures that if a device plugs into a switch interface, it cannot access the network until it has successfully authenticated.

The authentication process involves **three primary components**:
1.  **Supplicant:** The end-user device or client trying to gain access.
2.  **Authenticator:** The switch or wireless access point that the supplicant connects to.
3.  **Authentication Server:** A backend database that contains login credentials, such as **RADIUS, LDAP, TACACS+, or Kerberos** (often managed through an Active Directory database).

[This video](https://www.youtube.com/watch?v=QhLQ6J4satw&list=PLG49S3nxzAnl4QDVqK-hOnoqcSKEIDDuv&index=66&t=120s) explains the authentication workflow:
-   When a supplicant first connects, the authenticator **blocks all network access** until authentication is complete.
-   The authenticator initiates the process by sending an **EAP request** for credentials to the supplicant.
-   The supplicant provides an **EAP response** identifying itself, which the authenticator passes to the authentication server.
-   If the server is accepting logins, it asks for additional details (like a username and password) via the authenticator.
-   The supplicant provides the required credentials to the authenticator, which then forwards them to the authentication server for verification.
-   If the credentials match the database, the server sends a **successful login reply**, and the authenticator grants the user **access to the network**.


## Firewall Types

### General Purpose and Functionality
Firewalls are used in homes, offices, and within operating systems to **control the flow of traffic between two points**. They are essential in large environments for managing thousands of users and can be used to **restrict website access**, provide parental controls, or host additional security like **antivirus and anti-malware**.

### Network-Based Firewalls
These are purpose-built appliances used to manage network flows. They can operate at different levels of the OSI model:
-   **Traditional Firewalls:** These typically control traffic based on **OSI Layer 4**, using TCP or UDP port numbers.
-   **Layer 3 Integration:** Many firewalls also operate as **routers**, providing **network address translation (NAT)** and other routing protocols at the edge of the network.

### Unified Threat Management (UTM)
UTM devices are older **all-in-one security appliances** that bundle multiple services into a single device. Their features include:
-   **Filtering and Inspection:** URL filtering, content inspection, and **spam filtering** to block unwanted emails.
-   **Security and Connectivity:** Malware identification, **IDS/IPS** (Intrusion Detection/Prevention Systems), and acting as a **VPN concentrator**.
-   **Network Management:** They can provide wide area network (WAN) connectivity, routing, switching, and **bandwidth shaping** for quality of service.
-   **Drawbacks:** Because they handle so many tasks and often only operate at **Layer 4**, they can suffer from **performance issues** if too many capabilities are enabled at once.

### Next-Generation Firewalls (NGFW)
NGFWs are modern devices that operate at **OSI Layer 7 (the application layer)**. 
-   **Deep Packet Inspection:** They use **full packet decoding** to see who is sending traffic and what application content is inside, rather than just looking at port numbers.
-   **Granular Control:** Because they are application-aware, they can allow specific actions within an app—for example, allowing someone to **view Twitter but not post to it**, or allowing Microsoft SQL Server traffic regardless of the port used.
-   **Integrated Security:** They often include **URL categorization** (e.g., blocking all gambling sites) and can act as an **intrusion prevention system** by blocking known vulnerabilities.

### Web Application Firewalls (WAF)
A WAF is a specialized category of firewall designed to **analyze input into web-based applications** using HTTP or HTTPS.
-   **Attack Prevention:** They are specifically used to identify and block web-based attacks such as **SQL injections** and **cross-site scripting**.
-   **Compliance:** They are often mandated by security standards like the **Payment Card Industry Data Security Standard (PCI DSS)** to protect credit card-based applications.
-   **Monitoring:** WAF logs can track the time, date, source IP, country, and the specific security policy that blocked a malicious attempt.

## Secure Communications

### Virtual Private Networks (VPNs)
A VPN provides a secure form of communication by **encrypting private data** and sending it across a public network like the internet.
-   **VPN Concentrators:** These are purpose-built devices designed to be the endpoint for encrypted links. They can be standalone hardware appliances, integrated into next-generation firewalls, or software-based solutions.
-   **The Encryption Process:** To protect data, the original packet and its IP header are encrypted and wrapped (tunneled) within an **IPsec header** and **IPsec trailer**. A new IP header is then added to route the packet to the VPN concentrator. Upon arrival, the concentrator strips these headers, decrypts the original information, and sends it into the corporate network. For better understanding watch [this Professor Messer's video](https://www.youtube.com/watch?v=uU3e_ntg-3g&list=PLG49S3nxzAnl4QDVqK-hOnoqcSKEIDDuv&index=67&t=112).
-   **SSL/TLS VPNs (Remote Access):** Often used by individual devices like laptops, [these VPNs](https://res.cloudinary.com/dnhgctqsu/image/upload/q_auto/f_auto/v1775039957/SSL_VPN_kpbism.png) typically run over **TCP port 443**. Because they use the same port as encrypted web traffic, they easily pass through most firewalls. They can be installed as software, built into the operating system, or even run directly inside a web browser. Some are configured as **"always on"** meaning they connect automatically when the device starts up. 
-   **Site-to-Site VPNs:** [These](https://res.cloudinary.com/dnhgctqsu/image/upload/q_auto/f_auto/v1775039957/Site-to-site_IPsec_VPN_e1dtz7.png) connect entire remote locations to a corporate network. In this setup, firewalls at each location act as the VPN endpoints, meaning individual devices do not need any special software to communicate securely.

### SD-WAN (Software Defined Wide Area Network)
SD-WAN is designed to address the challenges of connecting to **cloud-based applications**. 
-   **Efficiency:** Traditional networks were centralized, requiring all remote traffic to hop through a main data center before reaching the cloud, which was inefficient.
-   **Dynamic Connectivity:** SD-WAN allows for more flexible, dynamic networks that can connect users directly to web-based applications and various cloud services from wherever they are.

### SASE (Secure Access Service Edge)
[SASE](https://res.cloudinary.com/dnhgctqsu/image/upload/q_auto/f_auto/v1775039957/Secure_Access_Service_Edge_SASE_dses6o.png) is a cloud-delivered framework that converges essential networking and security functions into a unified platform.
-   **Cloud-Based Security:** Instead of security living in a physical data center, SASE places security technologies in the cloud, near the services being used. 
-   **Unified Access:** Users (whether in an office, at home, or mobile) use a SASE client to connect to the cloud, allowing them to jump securely to any needed cloud-based service.

### Implementation in Organizations
Organizations often use these technologies together depending on their needs. For instance, they might use **SSL VPNs** for mobile users, **IPsec site-to-site VPNs** for branch offices, **SD-WAN** for efficient cloud connectivity, and **SASE** to provide security across the entire infrastructure.


## Data Typed and Classifications

### Regulated and Sensitive Data Types
Data is often subject to specific rules and protections based on its type:
-   **Regulated Data:** This includes information where a third party sets the rules for protection, such as **credit card data**, which must comply with the Payment Card Industry (PCI) standards. Government laws also dictate how data is stored and for how long.
-   **Trade Secrets and Intellectual Property:** Trade secrets are unique processes <ins>known only to an organization</ins> and <ins>require high security</ins>. **Intellectual property** is protected through copyrights and trademarks, even though it is often visible to the public.
-   **Legal and Financial Information:** Legal records often balance public transparency (like court records) with the need to protect **personally identifiable information (PII)**. Financial details, both internal corporate data and personal bank account information, are classified as <ins>sensitive</ins> and should remain <ins>private</ins>.
-   **Healthcare Information (PHI):** Protected Health Information includes health status, medical records, and healthcare-related payments, all of which are specific to an individual and must be kept secure.

### Data Readability and Accessibility
Data can be presented in various ways:
-   **Human Readable:** Data that humans can easily understand, such as documents or spreadsheets.
-   **Non-Human Readable:** Encoded data, like **barcodes** or images, that computers process but humans cannot easily recognize.
-   **Combinations:** Some formats use both, such as a barcode that includes numbers at the bottom for human interpretation.

### Classifications and Sensitivity Levels
To manage security, organizations assign **sensitivity levels** and classifications to their data:
-   **Public or Unclassified:** Information that anyone is permitted to view.
-   **Sensitive:** A broad category often including intellectual property, PII, and PHI.
-   **Confidential:** More sensitive data that requires additional access rights to view.
-   **Private, Classified, or Restricted:** Data requiring specific permissions or even a **non-disclosure agreement (NDA)** for access.
-   **Critical:** Data that must always be available. Organizations must create specific procedures to ensure the **uptime and availability** of this information.

For highly sensitive information, organizations may implement **restricted network areas** or specific permissions to ensure only authorized individuals can access the data. These classifications allow for different levels of access and control based on the data's importance and potential risk.