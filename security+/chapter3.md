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