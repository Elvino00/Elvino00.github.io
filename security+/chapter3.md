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
A **jump server** is a hardened and secured device located inside a private network that is accessible from the outside. Its primary purpose is to allow authorized individuals to **connect to and manage internal devices** from an external location. This typically involves a two-step process: an external client connects to the jump server first, and from there, they can use protocols like SSH to access and configure internal servers. Because it acts as a gateway, it is critical that jump servers are properly secured to prevent unauthorized external actors from gaining access to the rest of the internal network.

### Proxy Servers
A **proxy server** acts as an intermediary between two devices, making requests on behalf of a user. They provide several benefits and come in various configurations:

-   **Primary Functions:** Proxies can provide **caching**, which saves bandwidth by storing and serving identical requests locally rather than fetching them from the internet every time. They also offer security features like **URL filtering** and **content scanning** to block malicious traffic or exploits.
-   **Configuration Types:**
    -   **Explicit Proxy:** Requires the user to explicitly name the proxy's IP address or name within their application or operating system.
    -   **Transparent Proxy:** Operates invisibly to the end user, automatically intercepting requests without requiring any client-side configuration.
-   **Directional Types:**
    -   **Forward (Internal) Proxy:** Sits inside the network and manages outbound traffic from internal users to the internet. It examines the response from the internet and forwards it to the user only if it is legitimate.
    -   **Reverse Proxy:** Manages inbound traffic from the internet to internal services, such as a web server. It provides additional security by dropping malicious traffic before it reaches the server and can also use caching to reduce the server's load.
-   **Protocol-Specific Proxies:**
    -   **NAT (Network Address Translation):** A simple proxy that converts between internal and external IP addresses on routers.
    -   **Application-Level Proxy:** Understands specific protocols (e.g., HTTP, HTTPS, FTP) to provide more specialized handling.
-   **Open Proxies:** These are available to anyone on the internet and are often used to bypass security controls. However, they pose significant risks because they are managed by unknown third parties who could inject advertisements or **malicious code** into the traffic. Most organizations block access to open proxies to mitigate these risks.

### Load Balancers
A **load balancer** distributes incoming traffic across multiple servers, such as a web server farm, to maintain efficiency and ensure the load remains even.

-   **Fault Tolerance:** If a server fails, the load balancer identifies the failure and quickly redistributes the traffic to the remaining healthy servers.
-   **Operational Modes:** 
    -   **Active-Active:** All servers connected to the load balancer are used simultaneously.
    -   **Active-Passive:** Some servers are active while others remain on standby (passive). If an active server fails, the load balancer automatically switches a standby server to active status.
-   **Advanced Features:**
    -   **TCP Offloading:** The load balancer maintains a single open TCP connection instead of creating new ones for every user request, improving efficiency.
    -   **SSL Offloading:** The load balancer handles the heavy task of encryption and decryption centrally, sending decrypted traffic to the internal servers.
    -   **Content Switching:** The load balancer can identify the type of request and direct it to a specific server optimized for that task.

### Sensors and Collectors
For network management and monitoring, organizations use **sensors** and **collectors**.

-   **Sensors:** These can be built into existing devices like switches and firewalls, or they can be standalone devices. Their job is to gather statistics and data from network traffic, logs, and security systems like IPS.
-   **Collectors:** This is a central database where all sensor data is sent for storage and analysis.
-   **SIEM (Security Information and Event Manager):** A SIEM acts as a powerful collector that consolidates data from diverse devices into a single database. It provides reporting tools that allow administrators to **correlate and compare data** to identify events like failed authentications or port scans across the entire network.