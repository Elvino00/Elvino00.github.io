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

## Risk Management

**Risk management** is a critical process used by organizations to **identify and manage potential risks** before they escalate into larger problems. As an organization grows, the risks associated with it grow as well, and these threats can originate from either **internal or external sources**.

There are several ways organizations approach and perform risk assessments:

-   **One-time Assessments:** These are often specific to a particular project. Examples include evaluating the risks involved in **acquiring another company** or installing brand-new technology, such as **new software or equipment**.
-   **Ongoing Assessments:** In many organizations, risk assessment is a continuous process. This is commonly seen in the **change control process**, where the potential risk of every single change must be evaluated before it is implemented.
-   **Ad Hoc Assessments:** The term "ad hoc" means "for this purpose only". These assessments are conducted for a **specific, narrow purpose**, such as when a CEO learns about a **new type of attack** and wants to know if the organization is vulnerable. Typically, a committee is formed to study the threat, and once the findings are presented, the committee is disbanded.
-   **Scheduled Assessments:** Some organizations perform assessments on a **regular schedule**, such as every three, six, or twelve months. These can be handled by **internal assessment teams** who maintain ongoing documentation without needing an external third party.
-   **Mandated Assessments:** These are assessments required by specific **regulations or standards**. For instance, the **PCI DSS** (Payment Card Industry Data Security Standard) requires any organization that stores credit card numbers to perform a risk assessment **annually**.

## Risk Analysis

### Qualitative Risk Assessment
Qualitative analysis evaluates risk factors using **broad, descriptive terms** rather than specific numbers. 
-   **Methodology:** It often uses a **traffic light grid** (red, yellow, green) to categorize risks as **low, medium, or high**.
-   **Evaluation Factors:** Assessment involves looking at the **impact** of a risk, the **Annualized Rate of Occurrence (ARO)**, and the **cost of controls** to determine an overall risk level.
-   **Examples:** Common factors analyzed include the use of **legacy Windows clients**, **untrained staff**, or devices operating without **antivirus software**.
-   **Purpose:** This provides a high-level view to <ins>help</ins> organizations <ins>prioritize where to focus</ins> their <ins>efforts</ins> to resolve problems.

### Quantitative Risk Assessment
Quantitative analysis calculates **specific numerical values** to determine the financial impact of risks.
-   **Annualized Rate of Occurrence (ARO):** How often a risk is expected to occur in a single year (e.g., how many laptops are likely to be stolen).
-   **Asset Value (AV):** The total value of an asset to the organization, which includes replacement costs, impact on sales, and potential fines.
-   **Exposure Factor (EF):** The percentage of an asset's value lost during a risk event, ranging from 0.0 to 1.0 (100% loss).
-   **Single-Loss Expectancy (SLE):** The monetary loss from a single event, calculated as **AV x EF**.
-   **Annualized Loss Expectancy (ALE):** The total expected yearly cost of a risk, calculated as **ARO x SLE**.

### Impact and Likelihood
Risk calculations consider several types of impacts. Priority is as follows:
1.  **Life:** This is the **most important concern**, as people cannot be replaced.
2.  **Property:** Impact on buildings and resources.
3.  **Safety:** The impact on the safety of individuals and the company.
4.  **Financial:** The monetary impact calculated through quantitative analysis.

### Risk Appetite and Tolerance
Organizations must decide how much risk they are willing to accept:
-   **Risk Appetite:** The amount of <ins>risk</ins> an organization is <ins>willing to take</ins>, often described by a **posture** such as conservative, neutral, or expansionary.
-   **Risk Tolerance:** A larger variance than appetite; it represents the actual <ins>limit</ins> of <ins>what an organization will allow before acting</ins>. 
    -   *Example:* A highway speed limit of 55 mph represents the risk appetite (the law), but police not ticketing until a driver hits 65 mph represents the risk tolerance.

### Risk Documentation
Project-associated risks are documented in a **risk register**.
-   **Goal:** To <ins>detail</ins> individual <ins>risks</ins> and <ins>provide solutions</ins> to avoid them.
-   **Components:** Each entry includes **Key Risk Indicators (KRI)** (e.g., ill-defined project schedules), an assigned **Risk Owner** responsible for managing the risk, and a **risk threshold** to balance the cost of resolving the risk against the potential cost to the company.

## Risk management strategies

### Risk Management Strategies
-   **Transfer:** This involves **moving the risk under the control of a different party**. A common example of risk transfer is purchasing **cybersecurity insurance**.
-   **Accept:** This is the **most common course of action**, where a company acknowledges the risk and decides what they would like to do with it. 
-   **Avoid:** This strategy involves **completely removing the risk** from the organization, which eliminates the need for further risk management for that specific issue.
-   **Mitigate:** Organizations can **invest in tools or processes to reduce the impact of a risk**. For example, installing a **next-generation firewall** can mitigate risks associated with internet connectivity.

### Managing Policy Conflicts
When a company accepts risk, it may need to address situations where existing security policies cannot be met:
-   **Exemptions:** These are used when a **security policy simply cannot be followed**. An example provided is a piece of manufacturing equipment running Windows that the manufacturer does not support patching for. Management might approve an exemption for that device, provided it remains disconnected from the network.
-   **Exceptions:** An exception is created when there is a **conflict between a policy and operational requirements**. For instance, if a policy requires patching within three days, but a specific patch is found to crash critical software, an exception allows the company to delay the patch until the software is updated to be compatible.

### Risk Reporting
To manage these various issues, organizations use **risk reporting** to track and describe every risk they are monitoring.
-   **Function:** It provides a **list of risks and instructions on how to handle them**.
-   **Audience:** It is a document frequently **referenced by upper management** to inform business decisions, such as what equipment to purchase.
-   **Maintenance:** This is a **living document** that is constantly updated to include **critical and emerging risks**.

## Business impact analysis

The are several key metrics used when planning for and recovering from system outages as part of a business impact analysis and these are:

-   **Recovery Time Objective (RTO):** This is a defined <ins>time frame</ins> for **how long it takes to get a system back up and running** after an outage. For instance, an organization's RTO might be the total time required to get both a web server and a database server operational again.
-   **Recovery Point Objective (RPO):** This refers to a **point in time** that determines <ins>when an organization is considered operational</ins> based on data availability. An example provided is an organization that requires the last 12 months of customer data to be available; the time spent reloading that data from backups until the 12-month threshold is met represents the RPO.
-   **Mean Time to Repair (MTTR):** This is the **average amount of time required to resolve a problem**. This duration encompasses the time needed to diagnose the issue, acquire replacement equipment, install it, and complete the configuration. Organizations can decrease their MTTR by investing more money upfront, such as by maintaining an on-site inventory of equipment or having rapid-response contracts with third-party vendors.
-   **Mean Time Between Failures (MTBF):** This is a **prediction of how long a system will run** before the next outage occurs. It is used for planning and assessing the risk of using specific equipment. MTBF can be calculated by **dividing the total uptime of the equipment by the total number of breakdowns**. Manufacturers may provide these values as predictions, or they can be derived from historical performance data to help predict future issues.

## Third Party risk assessment

### Contracts and Agreements
Risk assessment expectations and **penalties for breaches** should be written directly into the contract with a third party. 
-   **Right to Audit:** This specific clause <ins>ensures all parties understand</ins> that <ins>regular audits will occur</ins> to <ins>review security controls</ins>.
-   **Rules of Engagement (RoE):** When performing penetration tests, this document <ins>sets parameters</ins> including the scope, timing (e.g., after-hours), IP address ranges, emergency contacts, and how sensitive information should be handled.

### Risk Assessment Methods
-   **Penetration Testing:** Unlike a standard vulnerability scan, this involves **actively exploiting vulnerabilities** in systems or applications to <ins>test security</ins>. This can be done by the company itself or a specialized third party to provide unbiased reports.
-   **Audits:** These focus on security controls such as **access management**, offboarding procedures, password storage, and VPN access. While sometimes required for compliance, regular audits are recommended to identify opportunities for security improvement.
-   **Independent Assessments:** Bringing in an outside party provides a different perspective and **broad scope of understanding** gathered from their experience with many other organizations.

### Supply Chain Analysis
Supply Chain Analysis is a process that examines the <ins>entire journey</ins> from raw materials to the final product <ins>to identify security concerns</ins>.

### Evaluation and Selection
-   **Due Diligence:** This is the investigative process of <ins>verifying a company's claims</ins>—such as financial health, customer count, and background checks—<ins>before deciding to do business with them</ins>.
-   **Conflicts of Interest:** Organizations must identify <ins>situations that compromise judgment</ins>, such as a vendor working with a major competitor, employing a relative of an executive, or offering gifts to secure a contract.

### Continued Monitoring
Risk management does not end when a contract is signed; it requires **ongoing monitoring**.
-   **Monitoring Activities:** This includes financial health checks, IT security reviews, and monitoring news or social media for mentions of the partner.
-   **Vendor Questionnaires:** These are used to <ins>gather information on a vendor’s own due diligence</ins>, **disaster recovery plans**, and technical data protection methods. The results from these questionnaires are integrated into a constantly updated risk analysis for that vendor.

## Agreement types

There are several types of formal and informal agreements used when working with third parties and business partners.

### Service Level Agreement (SLA)
A **SLA** is used with service providers to establish **minimum terms for service**, specifically regarding **uptime or availability**. For instance, an agreement with an internet service provider (ISP) might mandate no more than four hours of unscheduled downtime and require a technician to be dispatched if a failure occurs. It ensures both parties understand the exact requirements for service levels.

### Memorandum of Understanding (MOU) and Memorandum of Agreement (MOA)
-   **MOU:** This is an **informal document**, not a signed contract, that provides a **broad overview** of <ins>how two organizations might work together</ins>. It generally outlines broad goals and may include confidentiality statements. 
-   **MOA:** This is one step above an MOU and provides **more detail** regarding the <ins>relationship</ins> and <ins>how companies will work together</ins>. While it may contain some legally binding information, it is **not a contract** and is generally not legally enforceable.

### Master Service Agreement (MSA) and Statement of Work (SOW)
-   **MSA:** A **legal contract** that establishes the <ins>terms between organizations</ins> for an **ongoing relationship**. It provides a **framework** for future work, covering foundation details like billing, payment systems, and general service terms.
-   **SOW:** Used in conjunction with an MSA, the SOW provides a **detailed breakdown of specific services** to be provided. It allows organizations to focus on a particular set of tasks without renegotiating basic contract terms. A typical SOW includes the **scope of the job, location, deliverables schedule, and specific expectations**. It serves as a reference point to verify if the agreed-upon work was actually completed.

### Non-Disclosure Agreement (NDA)
An **NDA** is a formal contract used to ensure that shared information remains **confidential**. It allows parties to discuss trade secrets or business activities freely without worrying about the information reaching others. NDAs can be:
-   **Unilateral (One-way):** Only one party is required to maintain confidentiality.
-   **Bilateral (Mutual):** Both parties must maintain confidentiality.
-   **Multilateral:** More than two parties are involved in the agreement.

### Business Partners Agreement (BPA)
A **BPA** is used for **formal partnerships** and details the **financial arrangements and ownership stakes** of each partner. It outlines how business decisions are made and establishes protocols for when things go wrong, such as **financial issues or disasters** that might shut down the business.