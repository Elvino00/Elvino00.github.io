## Security Policies

### The Core of Security Policies
-   **CIA Triad:** The primary goal of security administrators is to maintain **Confidentiality, Integrity, and Availability**, which is achieved through documented rules and policies.
-   **Policy Purpose:** Security policies provide guidance on <ins>what</ins> an <ins>organization should be doing and why</ins>. They range from <ins>broad</ins> goals (like data storage requirements) to <ins>detailed</ins> regulations (such as Wi-Fi usage or remote access requirements).
-   **Information Security Policy:** It's a master list of all policies intended to <ins>maintain network uptime and security</ins>. It serves as a mandate for the organization and answers critical questions about <ins>handling security events</ins>, such as virus discoveries or unauthorized access.
-   **Roles and Responsibilities:** Policies define <ins>who is responsible for specific security tasks</ins> and <ins>who should be contacted regarding security concerns</ins>. Documentation alone is insufficient; the organization must actively **enforce** these policies.

### Specific Organizational Policies
-   **Acceptable Use Policy (AUP):** This defines <ins>what is</ins> considered <ins>appropriate use of company technology</ins>, including computers, telephones, and mobile devices. It informs users of their **responsibilities** and protects the organization from **legal liability** in cases of dismissal.
-   **Business Continuity Planning (BCP):** These policies ensure that <ins>business processes can continue even when technology is unavailable</ins>. For example, a retail store might have a policy to process credit card transactions manually via phone if the network goes down. Effective BCP <ins>requires</ins> extensive <ins>documentation and testing before a disaster occurs</ins>.
-   **Disaster Recovery Plan (DRP):** While BCP focuses on continuity, DRP is a formal <ins>set of policies for recovering after a widespread disaster</ins>—whether natural, technical, or human-caused. This includes maintaining a separate recovery location, methods for data recovery, and application restoration.

### Incident Response (IR)
-   **Incident Handling:** Organizations need detailed documentation for responding to security incidents like malware infections, **Distributed Denial of Service (DDoS)** attacks, botnets, or data theft.
-   **Response Roles:** A specialized team is required to handle these situations, involving:
    -   The **Incident Response Team** (trained and tested specialists).
    -   **IT security management** for resource allocation.
    -   **Compliance officers** to ensure mandates are met.
    -   **Technical staff** to solve problems in the trenches.
    -   **User community** to provide information on what occurred.
-   **NIST Standards:** The **NIST Special Publication 800-61 Revision 2** (The Computer Security Incident Handling Guide) outlines a lifecycle including preparation, detection and analysis, containment/eradication/recovery, and post-incident activity.

### Development and Change Management
-   **Software Development Lifecycle (SDLC):** This structure keeps developers focused on moving an application from the idea phase to deployment on schedule and on budget.
    -   **Waterfall:** A linear, sequential process (Requirements -> Development -> Testing -> Deployment -> Maintenance).
    -   **Agile:** A faster, iterative process involving constant designing, testing, and reviewing throughout the cycle.
-   **Change Management:** This process <ins>ensures</ins> that <ins>changes</ins>—such as firewall modifications or router configurations—<ins>do not negatively impact the organization</ins>. A formal process provides documentation on the change's duration, the installation process, and a **fallback procedure** if the change fails.

## Security Standards

In the technology industry, **security standards** provide formal processes and documentation that define requirements to **reduce risk** within an environment. While some organizations create their own unique standards, many rely on established frameworks from organizations like **ISO** (International Organization for Standardization) and **NIST** (National Institute of Standards and Technology).


### Password and Authentication Standards
Organizations use formal policies to define what constitutes a "good" password, typically focusing on **complexity** and **secure storage**. These standards often include:
-   **Authentication Methods:** Requirements may <ins>prohibit local accounts</ins> on devices, instead requiring authentication through a **central database** like LDAP or Active Directory.
-   **Management Procedures:** Standards define how password resets are handled, the frequency of required changes, and which password managers are acceptable for use.

### Access Control Standards
These standards determine **who can access data and when**. 
-   **Policies:** An organization might mandate **mandatory access control (MAC)** over discretionary policies.
-   **Gaining Access:** Standards define the process for <ins>granting access</ins>, which may require management sign-off or the completion of specific training.
-   **Removing Access:** There must be formal procedures for **offboarding** or <ins>removing access</ins> due to security issues, account expiration, or the end of a contract.

### Physical Security Standards
To secure property and personnel, standards are established for:
-   **Identification:** Requiring ID badges for entry and electronic door locks, with different rules for employees, contractors, and guests.
-   **Hardware and Monitoring:** Defining specific types of locks (such as biometrics), the use of motion detection, and ongoing monitoring.
-   **Visitor Safety:** Some organizations may require an **escort** for every visitor at all times.

### Encryption Standards
Because encryption is complex, documented standards are necessary to ensure it is implemented correctly.
-   **Algorithms:** Standards specify which **hashing or encryption algorithms** are required, such as using **salted hashes** for password storage.
-   **States of Data:** Encryption requirements often differ depending on the state of the data—whether it is **data at rest**, **data in transit**, or **data in use**. 

The ultimate goal of these combined standards is to ensure that all information remains **protected and confidential** from outside threats.

## Security Procedures

### Change Management
Change management is a set of <ins>processes</ins> designed to <ins>prevent downtime</ins>, confusion, and <ins>mistakes when modifications are made to systems</ins>. The process involves several key steps:
-   **Determining Scope and Risk:** Organizations must define the <ins>scope of a change</ins>—such as whether it affects a single file or an entire operating system—and <ins>assess the potential risk</ins> involved.
-   **Planning and Approval:** A formal plan is required to <ins>understand</ins> exactly <ins>what is changing</ins>, followed by approval from the end user. 
-   **Change Control Board (CCB):** Most organizations utilize a CCB to analyze, approve, and schedule proposed changes.
-   **Backout Plan and Documentation:** Every change must include a <ins>backup plan</ins> to revert systems if the process fails. Once completed, the <ins>change must be documented</ins> so others know what was modified.

### Onboarding and Offboarding
Formal procedures are necessary for managing <ins>how employees enter and leave an organization</ins>:
-   **Onboarding:** This involves providing new hires with an <ins>employee handbook and acceptable use policies</ins> that they must sign. Security teams <ins>create accounts</ins> with specific rights and permissions and <ins>provide the necessary hardware</ins>, such as laptops and mobile devices.
-   **Offboarding:** These procedures dictate <ins>what happens to hardware and data when an employee leaves</ins>. A best practice is to **disable accounts rather than deleting them** to ensure that important data or encryption keys are not lost.

### Playbooks and Automation
To handle specific security events, organizations use **playbooks**, which provide <ins>step-by-step instructions</ins> for scenarios like data breaches or ransomware recovery. These steps can be integrated into a **SOAR (Security, Orchestration, Automation, and Response) platform**. SOAR allows for the integration of diverse third-party products, <ins>automating mundane tasks</ins> so security teams can <ins>focus on high-priority work</ins>.

### Continuous Improvement and Monitoring
Security procedures must be constantly <ins>monitored</ins> and <ins>revised</ins> to <ins>adapt</ins> to **new technologies** and **emerging threats**. This may include <ins>tightening change control processes</ins>, creating <ins>more efficient playbooks</ins>, or acquiring new security technologies to <ins>improve the overall security posture</ins>.

### Governance Structures
Organizations manage security through different governance models:
-   **Board and Committees:** A board of <ins>directors</ins> typically <ins>sets broad objectives</ins>, while committees of subject matter <ins>experts</ins> <ins>determine</ins> the best way to <ins>implement</ins> those <ins>goals</ins>.
-   **Public Sector Governance:** <ins>Government organizations</ins> often focus on <ins>legal, administrative, and political issues</ins>, and their meetings are generally open to the public.
-   **Centralized vs. Decentralized:** In a **centralized** model, <ins>one group makes decisions</ins> for the entire organization. In a **decentralized** model, <ins>decision-making is distributed</ins>, often to those who are performing the specific jobs.

## Security Considerations

IT security professionals must remain aware of various **regulations** governing the data they collect, which includes information stored in applications as well as the log files those applications create. Many organizations are subject to **data retention** requirements, such as mandates to store emails for several years and ensure they remain accessible.

Key regulations and legal considerations are:

-   **Sarbanes-Oxley (SOX):** Officially known as the Public Company Accounting Reform and Investor Protection Act of 2002, this focuses on protecting **financial data** and ensuring it is <ins>available to the correct individuals</ins> within an organization.
-   **HIPAA:** The Health Insurance Portability and Accountability Act protects **healthcare information**, covering <ins>how</ins> that <ins>data is stored</ins>,<ins> transferred</ins>, and <ins>disclosed to third parties</ins>.
-   **Legal Holds and Reporting:** IT teams must have formal processes for <ins>reporting illegal activities</ins> and responding to **legal holds**, which ensure data is preserved for future legal proceedings.
-   **Breach Disclosure:** Most jurisdictions require organizations to <ins>disclose security breaches</ins> within a specific timeframe, though these rules vary significantly based on **geography**.

**Geographic and Industry-Specific Considerations**
Cloud computing presents a challenge because data can be stored anywhere in the world, yet some countries have **data residency** laws requiring that data collected from their citizens stay within that country's borders. 

Security needs also vary by industry:
-   **Public Utilities:** Electrical power generation systems often use **air-gapped** networks to strictly control access.
-   **Medicine:** Healthcare environments focus on making data accessible to professionals while keeping it private through **extensive encryption**.

**Organizational Scope**
The scope of an organization also dictates its security focus:
-   **Local/Regional:** Focuses on records and information used to manage specific cities or states.
-   **National:** Involves federal government issues and **national defense**, often requiring more advanced encryption and data protection technologies to maintain high levels of confidentiality.
-   **Global:** These organizations face the most complexity because they must navigate the different **international laws** for data protection and security in every country where they operate.

## Data Roles and Responsibilities

There are key roles and responsibilities related to managing and protecting data within an organization:

-   **Data Owner:** This is typically a **high-level executive** who holds <ins>ultimate responsibility</ins> for a <ins>specific set of data</ins>.
For instance, a Vice President of Sales would own customer relationship data, while a Treasurer would own financial information.
-   **Data Controller:** This role is responsible for **managing how data will be used**. They provide specific instructions to processors on how data handling should occur. An example is a company's payroll department.
-   **Data Processor:** The processor **actually uses or processes the data** based on the instructions provided by the controller. For example, a third-party payroll company acts as a data processor by using bank details and employee information to handle weekly payroll.
-   **Data Custodian or Data Steward:** This individual is responsible for the **security, accuracy, and privacy** of the data. Their duties include:
    -   Ensuring the organization complies with relevant **laws and regulations**.
    -   Assigning **sensitivity labels** to data.
    -   Linking those labels to **access controls** to ensure only authorized users can reach the data.
    -   Determining exactly **which users have access** to which types of data.