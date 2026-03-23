## Threat Actors

**Threat actors** are entities that cause events <ins>affecting the security</ins> of others. These are often called "malicious actors" because their <ins>actions</ins> typically have <ins>negative security effects</ins>. Understanding <ins>who</ins> a threat actor is can help an organization understand the "why" and the ultimate <ins>goal</ins> behind an attack.

Threat actors are characterized by several attributes:

-   **Location:** They can be **internal** (working within the organization) or **external** (outside trying to gain access).
-   **Resources and Funding:** This ranges from very <ins>limited funds</ins> to the <ins>extensive financial backing</ins> of a government.
-   **Level of Sophistication:** This describes their <ins>skill level</ins>, ranging from <ins>unskilled individuals</ins> using basic scripts to <ins>highly sophisticated developers</ins> who build their own tools.
-   **Motivation:** Reasons for attacks include data exfiltration, espionage, service disruption, financial gain, philosophical/political reasons, or even revenge.

Threat actors are categorized into several specific types:

### Nation State
-   **Attributes:** External, with extensive resources and a very high level of sophistication.
-   **Motivation:** National security, data exfiltration, or political/philosophical goals. They may seek to disrupt services (utilities, military, or finances) or even provoke war.
-   **Key Concept:** Their attacks are often called **Advanced Persistent Threats (APTs)** due to their constant and sophisticated nature. An example of a multi-government attack is the **Stuxnet worm**, designed by the U.S. and Israel to destroy nuclear centrifuges.

### Unskilled Attacker
-   **Attributes:** Can be external or internal; they have very limited resources and low sophistication.
-   **Behavior:** They typically run pre-made scripts without understanding how they work—if a script fails, they cannot modify it.
-   **Motivation:** Often motivated by the attack itself, though they may also seek to disrupt services or exfiltrate data for political/philosophical reasons.

### Hacktivist (Hacker Activist)
-   **Attributes:** Usually external, but may seek internal employment to become a threat; they possess high technical sophistication but often have limited finances.
-   **Motivation:** Driven by political or philosophical reasons.
-   **Actions:** They focus on website defacement, denial of service, or leaking private documents to the public.

### Insider Threat
-   **Attributes:** Internal to the organization with a medium level of sophistication.
-   **Advantage:** They excel because they know exactly where data is located and how to circumvent existing security controls.
-   **Motivation:** Often financial gain or revenge. The source emphasizes the importance of vetting during the hiring process to prevent these threats.

### Organized Crime
-   **Attributes:** Usually external, highly sophisticated, and well-funded.
-   **Motivation:** Almost exclusively financial gain and profit.
-   **Structure:** They often operate like a corporation, with specialists for hacking, managing exploits, selling stolen data, and even providing "customer support" for ransomware victims.

### Shadow IT
-   **Attributes:** Internal groups or departments that work around the official IT department's rules.
-   **Behavior:** They use their own budgets or credit cards to set up cloud services or infrastructure without IT oversight, bypassing change control and security policies.
-   **Risk:** They often lack a background in IT and security, meaning they may not perform backups or implement necessary security controls, putting the organization at high risk.

[Table of threats](https://res.cloudinary.com/dnhgctqsu/image/upload/v1770722686/Table_of_threats_om7w0m.png)


## Threat Vectors

A **threat vector** (or attack vector) is the specific **method an attacker uses to gain access** to a system. Attackers spend their time discovering or creating new vectors, targeting both well-known and unknown vulnerabilities. Common threat vectors are categorized as follows:

### Messaging and Social Engineering
-   **Messaging Systems:** Because of their ubiquity, messaging systems like **email, SMS (text messages), and instant messages (IM/DM)** are common entry points.
-   **Phishing:** Attackers communicate directly with users to entice them to click malicious links, often leading to **spoofed websites** (like fake bank logins) to steal credentials or install malware.
-   **Techniques:** Vectors include sending **malicious invoices** for services never rendered or **cryptocurrency scams** designed to steal wallet access. A common real-world example is a text message claiming a package delivery was suspended to trick users into clicking a link.

### Image and File-based Vectors
-   **SVG Images:** Scalable Vector Graphics are **XML files** that can have **malicious HTML or JavaScript code** embedded within them. When a browser renders the image, it may also execute the embedded code, potentially leading to **cross-site scripting (XSS) attacks**.
-   **PDFs and Office Documents:** Files like **Adobe PDFs** can hold hidden objects and scripts. **Microsoft Office macros** are another vector; while often useful, they can be written to gather and exfiltrate personal information.
-   **Compressed Files:** Attackers use **ZIP or RAR files** to obfuscate malware, hiding it among hundreds of other files within the archive.
-   **Browser Extensions:** Malicious add-ins or extensions can put an entire system at risk once installed.

### Voice and Removable Media
-   **Vishing and VoIP:** **Voice phishing (vishing)** involves calling victims to steal credit card or personal data. Attackers also use **Spam over IP** (automated spam calls) and **war dialing** to find unpublished phone numbers that may grant system access.
-   **USB Drives:** A single cheap USB drive can circumvent expensive firewalls. Attackers may leave infected drives in a company's **parking lot**, hoping an employee will plug it in. This is especially effective against **air-gapped networks**.
-   **HID Emulation:** Specially modified USB drives can appear to a computer as a **keyboard**, allowing them to automatically type malicious commands.

### Software and System Vulnerabilities
-   **Unpatched Software:** Attackers take advantage of known vulnerabilities in software that has not been updated. **Unknown (zero-day) vulnerabilities** give attackers an even greater advantage.
-   **Agentless and Web Applications:** In web-based applications, infecting a **central server** can potentially compromise all connecting clients.
-   **Unsupported Systems:** Legacy or **"end-of-life" systems** that no longer receive security patches are high-risk. These are often **"shadow IT"**—older computers running under desks that the IT department may not even know exist.

### Network and Configuration Vectors
-   **Wireless and Bluetooth:** Using outdated protocols like **WEP or WPA** (instead of WPA3) makes networks vulnerable. Attackers also look for **rogue access points** or use **Bluetooth** for reconnaissance and entry.
-   **Open Ports and Misconfigurations:** Every open port (like Port 80 for web servers) is a potential entry point. **Misconfiguring** complex applications or leaving unnecessary services running increases the attack surface.
-   **Default Credentials:** Many devices come with **default usernames and passwords** (e.g. admin/admin) that are easily found on public websites.

### Supply Chain Vectors
-   **Manufacturing and Third Parties:** Malicious code or hardware can be added to equipment during or after manufacturing. 
-   **Service Providers:** If an attacker compromises a **Managed Service Provider (MSP)**, they gain access to all the MSP's clients. 
-   **Contractors:** A famous example occurred in 2013 when attackers used an **HVAC contractor's** credentials to jump into Target's network and steal credit card numbers.
-   **Counterfeit Hardware:** Fake networking equipment, such as **counterfeit Cisco switches**, can contain pre-installed malicious software.

## Phishing 
Phishing is a form of **social engineering** that uses various communication methods to deceive individuals into believing a <ins>fake situation</ins> is <ins>real</ins> in order to <ins>steal</ins> private <ins>information</ins>.

### Core Concepts and Goals
-   **Purpose:** The primary objective is to trick users into providing sensitive data, such as **usernames, passwords**, and personal information.
-   **Consequences:** If an attacker gains access to an email account, they can search for financial information, use the account to send more phishing emails, or use the **"reset password"** feature on other sites (like PayPal) to take over additional accounts. Furthermore, clicking a phishing link can result in the download of **malware** that infects the system.

### Common Delivery Methods
-   **Email Phishing:** This is a common method where attackers <ins>pretend</ins> to be a <ins>legitimate</ins> service to lure users into <ins>clicking links</ins> or <ins>entering credentials</ins> on a <ins>fake login page</ins>.
-   **Vishing (Voice Phishing):** Phishing conducted over the **phone**. Attackers may <ins>spoof caller ID</ins> to appear as a bank or a company like Visa, often claiming there is an issue with a payment to <ins>obtain credit card details</ins>.
-   **Smishing (SMS Phishing):** Phishing delivered via **text message (SMS)**. A common example is a <ins>fake notification</ins> from the USPS <ins>claiming</ins> a <ins>package delivery</ins> has been suspended due to an incorrect address.

### Red Flags and Indicators
There are several ways to identify a phishing attempt:
-   **Suspicious Links:** Links in messages often point to a different location than what is expected for a trusted site.
-   **Visual Inconsistencies:** Fake login pages may have "something not quite right," such as **spacing issues or incorrect fonts**.
-   **Incongruent Senders:** The sender's email address might not match the service they claim to represent (e.g. a Rackspace alert sent from an iCloud address).
-   **Urgency and Threats:** Attackers often use **deadlines** or threats—such as telling a user they will be blocked from sending or receiving emails—to pressure them into acting quickly.

### Attacker Techniques
-   **Spoofing:** Attackers may <ins>spoof</ins> a <ins>legitimate email address</ins> or use one that is <ins>very similar</ins> to the <ins>real</ins> one.
-   **Typo Squatting:** This involves using a **misspelled domain name** to misdirect or hijack users who make a typing error.
-   **Pretexting:** This is when an attacker **invents a story** or creates a "drama" to trap a victim into providing information. Examples include pretending to call about a failed automated payment for electrical services.
-   **Other Scams:** There are also fake check scams and phone verification code scams.


## Impersonation
**Impersonation** is a tactic where an attacker pretends to be someone else to build trust and manipulate a victim into providing sensitive information.

### Common Pretexts and Tactics
Attackers often use specific "stories" or pretexts to sound legitimate:
-   **Technical Support:** Claiming to be from "Microsoft Windows" for an urgent computer checkup or from a company's **internal help desk** to resolve system problems.
-   **Authority Figures:** Posing as high-ranking officials, such as a **Vice President of Finance** or a manufacturing head, hoping the victim will comply with requests without thinking.
-   **Government/Financial Agencies:** Using intimidating language about "enforcement actions" from the **US Treasury** or offering fake incentives like **0% interest rates** on credit cards.
-   **Technical Jargon:** Using complex terms or technical details to distract the victim and make the call seem professional.

### Goals of Impersonation
The primary objective is often **eliciting information**, such as credit card numbers, Social Security numbers (SSNs), and bank details. This is frequently done through **vishing** (voice phishing), where attackers create elaborate stories—such as a "problem with a payment"—to justify needing sensitive data.

### Identity Fraud
When attackers successfully steal personal information, they can commit **identity fraud** by:
-   **Opening accounts:** Creating new credit card accounts in the victim's name but using the attacker's address to receive the cards.
-   **Financial theft:** Opening bank accounts to store illegal funds or applying for **loans** under the victim's name, which the attacker then spends.
-   **Tax fraud:** Filing tax forms as the victim to intercept their **tax refund**.

### Prevention Strategies
To protect against these attacks, it's recommend to follow these steps:
-   **Do not volunteer information:** Real technical support teams do not need your **password** to fix your system.
-   **Protect personal details:** Avoid giving out your address, SSN, or birthday over the phone or email.
-   **Verify the caller:** If a call seems suspicious, do not take it at face value. Instead, use a **publicly listed phone number** to call the organization back and verify the person's identity.
-   **Standardize verification:** Organizations should make verification a normal, required process for any request involving sensitive or financial data.

## Watering Hole Attack

A **watering hole attack** is a security threat where an attacker, instead of trying to breach a target organization directly, gains <ins>access</ins> to a <ins>third-party system</ins> that the organization’s employees are <ins>known to visit</ins>. This strategy is often used when employees are well-trained enough to avoid common pitfalls like plugging in unknown USB keys or clicking suspicious email links.

### How the Attack Works
-   **Research:** The attacker must first research the target organization to identify which third-party <ins>websites</ins> its <ins>employees visit frequently</ins>, such as a local coffee shop or sandwich shop website.
-   **Exploitation:** The attacker looks for <ins>vulnerabilities</ins> on that third-party site or uses <ins>social engineering</ins> (like sending malicious email attachments to the third party) to gain access to its web server.
-   **"Poisoning the Well":** Once the attacker has access, they "<ins>poison</ins>" the site by adding malicious content, such as **JavaScript files**, and then simply wait for the target to visit. 
-   **Specific Targeting:** These attacks can be highly selective. In some cases, attackers only serve malicious code to specific **IP addresses** associated with their targets, while all other visitors see a completely normal, safe version of the website.

### Real-World Example
In January 2017, a major watering hole attack targeted the Polish Financial Supervision Authority, the national banking and stock commission of Mexico, and a state-owned bank in Uruguay. The attackers used malicious JavaScript but specifically targeted only IP addresses associated with particular financial organizations. While many sites were infected, the ultimate success of the attackers in gaining the access they wanted remains unknown.

### Prevention: Defense in Depth
Because there is no single solution to prevent these attacks, organizations must use a **layered defense** or **"defense in depth"**. This approach ensures that if one layer fails, another may catch the threat. Key layers include:
-   **Antivirus Software:** In the 2017 Polish attack, Symantec antivirus was able to recognize the malicious code and stop it from executing on individual computers.
-   **Firewalls and Intrusion Prevention Systems (IPS):** These are often bundled together; while a firewall might allow the initial traffic through, an IPS can recognize if the content of that traffic is malicious.
-   **Combined Security:** Utilizing multiple layers—antivirus, firewalls, and IPS—significantly increases the odds of recognizing and blocking malicious software from these attacks.


## Other Social Engineering attacks

There are other social engineering techniques, focused primarily on misinformation, disinformation and brand impersonation.

### Misinformation and Disinformation
One effective technique involves spreading **factually incorrect information** to divide or confuse groups of people. This is frequently seen in **influence campaigns** on social media, which often target political or social issues. These campaigns may be orchestrated by **third-party governments or nation-states** to persuade people to believe falsehoods or to distract from damaging truths.

The process of spreading this information typically follows these steps:
-   **Creation of Fake Accounts:** Attackers create numerous accounts representing fake users, all controlled by the same person.
-   **Initial Posting:** Content is posted online using one of these fake accounts.
-   **Amplification:** The attacker uses their other fake accounts to **like, share, or follow** the post. This triggers social media **algorithms** to recognize the post as popular and present it to even more people.
-   **Mass Media Involvement:** Once the misinformation reaches a high level of popularity through actual users sharing it, **mass media** may recognize the trend and create their own stories about it, further legitimizing the false information.

### Brand Impersonation
Another technique involves exploiting recognizable **brand names** like Coca-Cola or McDonald's. Attackers create hundreds or thousands of websites using these brand names, which are then **indexed by search engines** like Google. 

When a user searches for a legitimate brand, they may be **redirected to one of these impersonated sites**. These sites often use tactics such as:
-   **Malicious Pop-ups:** Users may see messages offering special deals or prompting them to **download software**.
-   **Malware Infection:** The downloaded software is typically illegitimate and contains **malware**.
-   **Data Theft and Tracking:** Once a computer is infected, the malware may display ads, track the user's browsing habits, or **exfiltrate data** to the attacker.

## Memory Injections

Software and malware cannot execute on a computer unless they are **loaded from a disk into memory** and processed by the CPU. Memory contains various components necessary for these operations, including **Dynamic Link Libraries (DLLs)**, threads, buffers, and memory management functions. 

### Methods of Operation
Malware typically has two choices for how it runs in memory:
-   **Standalone Process:** It can run as its own independent process.
-   **Process Injection:** It can find an existing, legitimate process and **inject itself** between that process's starting and ending memory addresses.

### Advantages of Injection
Injecting into an existing process provides several benefits to an attacker:
-   **Evasion:** It allows the malware to **avoid detection** by anti-malware software that is specifically looking for known malicious processes.
-   **Privilege Escalation:** The malware inherits the **same rights and permissions** as the process it has injected into. This is an easy way for attackers to gain higher levels of access than they would normally have on the system.

### DLL Injection Mechanism
One of the most common forms of this technique is **DLL (Dynamic Link Library) injection**. This process involves several steps:
1.  **Storage:** The attacker first installs a **malicious DLL** onto a storage drive that the target system can access.
2.  **Linking:** The attacker places a **path or a link** to that malicious DLL inside the target process.
3.  **Execution:** As the legitimate process executes, it eventually reaches the point where it references that path. It then pulls the malicious DLL from the disk and **loads it into memory**, at which point the malware begins running on the system.

[DLL Injection Mechanism](https://res.cloudinary.com/dnhgctqsu/image/upload/v1771262041/Dll_Injection_Mechanism_vsfw48.png)


## Buffer Overflow

A **buffer overflow attack** occurs when an attacker writes more data into a specific area of memory than it is designed to hold, causing the extra information to **overflow into adjacent memory areas**.

### How Buffer Overflows Work
-   **Bounds Checking:** Under normal circumstances, application developers use **bounds checking** to ensure that data being written to a section of memory does not exceed its allocated size (for example, ensuring only 8 bytes are written into an 8-byte space). 
-   **Exploitation:** Attackers search for parts of an application where bounds checking is absent to modify the application's intended design. 
-   **Difficulty and Risk:** This is not a simple vulnerability to exploit. If the overflow is handled incorrectly, it can cause the entire **system or application to crash**. Attackers specifically look for **repeatable** overflows that allow them to perform functions advantageous to them.

### Example: Gaining Administrative Rights
Here's an example of how a buffer overflow can be used to gain **elevated permissions**:

[Esempio Buffer Overflow](https://res.cloudinary.com/dnhgctqsu/image/upload/v1771324903/Buffer_overflow_tttkbv.png)

1.  **Memory Setup:** There are two variables in memory: **Variable A** (8 bytes, initially empty) and **Variable B** (2 bytes, current value 1979).
2.  **Permissions Logic:** In this application, Variable B controls user rights. A value below 2,000 grants guest/user rights, but a value **over 24,000** grants **administrative rights**. 
3.  **The Attack:** Variable B cannot normally be changed from within the application. However, an attacker finds a vulnerability in Variable A. They attempt to store the 9-letter word **"excessive"** into the 8-byte space of Variable A.
4.  **The Overflow:** The first eight characters fill Variable A. The ninth character ("e") overflows into the first byte of Variable B. 
5.  **The Result:** This overflow changes the value of Variable B from 1979 to **25,856**. Because this value is over 24,000, the attacker successfully gains **administrative rights and permissions** without needing any actual credentials.

## Race Condition
A **Race condition** occurs when an application <ins>fails</ins> to <ins>account</ins> for two or more events happening at nearly the <ins>same time</ins>. This lack of synchronization can lead to **unexpected outcomes** when processes operate simultaneously.

### Time-Of-Check to Time-Of-Use (TOCTOU)
A common type of race condition is known as a **TOCTOU attack**. This happens when an application checks a system to <ins>retrieve</ins> a stored value and then <ins>performs</ins> a function with that value later. The vulnerability exists because **another process may change that value** in the window of time between the initial check and the actual use of the information.

### Practical Example: Banking Logic Flaw

[Race Condition Example](https://res.cloudinary.com/dnhgctqsu/image/upload/v1771330238/Race_condition_example_fq1zj0.png)

Let's take the example of two users (User 1 and User 2) transferring money between Account A and Account B, both starting with \$100.
-   **The Flaw:** The application is designed to update deposits immediately, but **withdrawals are not immediately updated** in the ledger.
-   **The Sequence:** Both users deposit \$50 into Account B, which updates correctly to \$200. User 1 then withdraws \$50 from Account A; from their perspective, Account A now has \$50. 
-   **The Race Condition:** User 2 also withdraws \$50 from Account A. Because the first withdrawal was not immediately reflected for all users, User 2's transaction incorrectly uses the \$50 balance as a starting point rather than the true balance.
-   **The Result:** The final balance for Account A is \$50 when it **should actually be \$0**.

### Real-World Incidents
-   **Mars Rover Spirit (2004):** A race condition involving the rover's file system triggered a safety mechanism that caused a **reboot loop**. The rover would recognize a fatal error, reboot to fix it, and immediately encounter the same error again. Developers were eventually able to send code to the rover to **bypass the error** and restore functionality.
-   **Tesla Model 3 (2023):** During the Pwn2Own competition, researchers used a **TOCTOU attack** via Bluetooth to exploit the car's infotainment system. This allowed them to **elevate their privileges to "root user,"** earning them a \$100,000 prize and the vehicle itself.

## Malicious Updates

While security professionals emphasize <ins>keeping</ins> operating systems and applications <ins>patched</ins> to <ins>avoid</ins> vulnerabilities, there is a risk that attackers can embed malicious code within these updates.

### Best Practices for Safe Updates
To mitigate the risks of installing malicious software during the update process, there are several best practices:
-   **Maintain Backups:** Always have a **system backup** before making changes. This allows you to revert to a previous configuration if the update causes problems.
-   **Use Trusted Sources:** Ensure that updates are coming from sources you commonly use or those officially associated with the software.
-   **Download from Developers:** For the highest level of trust, download patches **directly from the application developer’s website** rather than third-party sites.
-   **Verify Digital Signatures:** Many operating systems will only install software that has been **digitally signed** by the developer (e.g Microsoft, Google, or Adobe). The OS validates this signature to ensure the update is legitimate.
-   **Utilize Built-in Update Processes:** Many applications have internal update mechanisms that automatically perform security checks and verify digital signatures, offering a high level of trust.

### Identifying Red Flags
Users should be cautious of how an update message is delivered:
-   **Trustworthy Messages:** An update prompt that appears when you first start your browser is generally considered more reliable.
-   **Suspicious Messages:** Be skeptical of update prompts that appear after clicking a search engine link or as **random pop-ups** during a normal web-browsing session.

### The SolarWinds Case Study
The sources highlight that even trusted processes are not a 100% guarantee of safety, as seen in the **SolarWinds** incident reported in December 2020. 
-   **The Breach:** Attackers gained access to SolarWinds' development systems and embedded malicious code into the **Orion** application.
-   **Distribution:** Because the malicious code was rolled into a legitimate update, it was **digitally signed** by the company and automatically distributed to users.
-   **Impact:** This allowed attackers to gain "full rein" over the systems of hundreds of large companies and government agencies, using the Orion system as a jumping-off point to reach other unsecured systems. Although such attacks are rare, they demonstrate how a trusted distribution process can be exploited to spread malware to thousands of systems simultaneously.


## Operating system vulnerabilities

An **operating system (OS) patched** to the latest version is a fundamental requirement for security professionals because OSs are foundational platforms used by everyone, making them primary targets for attackers.


-   **Complexity and Vulnerabilities:** Modern operating systems are incredibly complex; for example, Windows 11 contains tens of millions of lines of code. This high volume of code increases the likelihood of security vulnerabilities appearing. Many vulnerabilities likely exist in current systems that have not yet been discovered by researchers or attackers.
-   **The Patching Cycle:** Once a vulnerability is discovered and reported, manufacturers create updates. Microsoft specifically uses **"Patch Tuesday"**—the second Tuesday of every month—to release sets of security patches. These patches address various issues, such as **Elevation of Privilege**, **Security Feature Bypass**, and **Remote Code Execution**.
-   **The Risk of Delay:** When a vulnerability is announced, attackers often attempt to **reverse engineer** the update to create attack code. Systems must be patched as quickly as possible to stay ahead of these subsequent attacks.
-   **Best Practices for Deployment:**
    -   **Backups:** Always ensure you have a backup before performing a patch so you can revert to a "known good" configuration if something goes wrong.
    -   **Testing:** In large environments with hundreds or thousands of devices, patches should be **tested** before being deployed to production to ensure they do not break other system functions.
    -   **Reboots:** Some patches, particularly those affecting the core of the operating system, require a **system reboot** to be fully applied.


## SQL Injection

A **code injection attack** occurs when an attacker inputs their own code into an application's input fields. This is a common vulnerability that arises when developers fail to implement proper checks to prevent unwanted data from being processed. While there are many types of code injections, such as HTML and XML, **SQL injection (SQLi)** is one of the most significant.

### What is SQL Injection?
SQL stands for **Structured Query Language**, the primary method for applications to interact with databases. In a normal transaction, the application takes user input and uses it to query the database—for example, searching for a specific username like "Professor". A **SQL injection** allows an attacker to <ins>insert</ins> their own <ins>requests</ins> into that query, altering its intended purpose.

### How the Attack Works
-   **Ease of Use:** This vulnerability is often easy to exploit because it can be done directly through a **web browser** using existing input fields. It does not require specialized software or tricking a user into clicking a link.
-   **The "1=1" Method:** A common technique involves adding code like `OR 1=1` to a query. Because the statement "1 equals 1" is always true, the database may bypass original security filters and return every record in the table.
-   **Example Case:** Using a vulnerable application called **WebGoat**, an attacker can bypass a login requiring a name and a transaction authentication number. By injecting `' OR '1'='1'`, the attacker can retrieve all department information instead of just their own.

### Impact and Risks
A successful SQL injection can give an attacker **complete control** over the database. The potential consequences include:
-   **Viewing** all sensitive data stored in the database.
-   **Deleting** entire datasets.
-   **Modifying** information.
-   **Shutting down** the database so it becomes inaccessible to others.

## Cross-site Scripting (XSS)

**Cross-site Scripting (XSS)** is one of the most common vulnerabilities for web-based applications, exploiting the trust a browser has for different websites.

### How XSS Works

XSS vulnerabilities typically involve **JavaScript**, a popular scripting language that most users have enabled in their browsers. In a high-level exploit:
-   An attacker sends a **link** containing a **malicious script** to a victim via email, text, or other methods.
-   When the victim clicks the link, they are taken to a **legitimate, trusted website**, but the malicious script runs alongside the connection.
-   Behind the scenes, the script sends **private data**—such as cookie information and session details—directly to the attacker.
-   By obtaining this session information, the attacker can gain the **same access** to the website as the victim.

[How XSS Attack Works](https://res.cloudinary.com/dnhgctqsu/image/upload/v1772020725/XSS_Attack_iw8gya.png)

### Types of XSS Attacks
The source describes two primary categories of XSS:

-   **Non-persistent (Reflected) Attack:** This occurs when a website allows scripts to run inside **user input blocks**, such as search engines or credit card fields. For example, if a "credit card number" field does not check for scripts, an attacker can embed JavaScript there to display or steal session IDs when a user clicks "Purchase". In this scenario, the attacker sends the malicious code to the user, who then executes it against a third-party site.
-   **Persistent (Stored) Attack:** In this version, the attacker stores the malicious payload on a **third-party site**, such as a social media platform. Because the script is stored on the site itself, **everyone who visits that page** will have the malicious code run in their local browser. These attacks can spread rapidly if the script is designed to automatically share itself to the visitors' own social feeds.

### Real-World Example: Subaru (2017)
Security researcher Aaron Guzman identified an XSS vulnerability on **Subaru’s website** used for vehicle management. 
-   **The Issue:** Subaru used login tokens that **never expired**, allowing for permanent access once a token was obtained.
-   **The Attack:** An attacker could use XSS to steal a victim's token via a malicious link.
-   **The Consequence:** With that token, an attacker could perform service requests on the victim's vehicle or even add their own email address to other accounts to manage those vehicles as well. 
-   **Resolution:** Subaru resolved these vulnerabilities after being informed by the researcher.

### Prevention and Protection
There are several ways for both users and developers to defend against XSS:

-   **For Users:** 
    -   **Avoid clicking links** from untrusted third parties in emails or messages; instead, type trusted domain names directly into the browser.
    -   Keep browsers and applications **updated to the latest versions** to receive patches for known vulnerabilities.
    -   Consider **disabling or limiting JavaScript** via browser plugins, though this may limit the functionality of some websites.
-   **For Developers:** 
    -   Ensure all **application inputs are checked** and validated to prevent users from adding their own scripts to input fields.


## Hardware Vulnerabilities

There are security risks associated with **networked hardware devices**, particularly those where the internal operating system (often called **firmware**) is not accessible to the user. Because these devices — ranging from office clock-in systems and air conditioners to home appliances like stoves and refrigerators — are <ins>connected</ins> to the network, they represent potential <ins>security vulnerabilities</ins>.

### Firmware and Manufacturer Challenges
A primary concern is that **firmware can only be managed or updated by the manufacturer**. Unlike standard operating systems like Windows or macOS, which typically release patches within a month, hardware manufacturers may <ins>not prioritize IT security</ins>. For example, the sources note that Trane was notified of vulnerabilities in its Comfortlink II thermostats in April 2014, but did not release a patch until April 2015, with a second following in January 2016.

### Product Lifecycle: EOL vs. EOSL
There are two key dates in a product's lifecycle:
-   **End of Life (EOL):** The manufacturer **stops selling** the product. While this is a warning that support will eventually end, security patches and updates may still be available during this phase.
-   **End of Service Life (EOSL):** The manufacturer **no longer provides security patches**. At this point, the device becomes a significant risk. While some manufacturers offer expensive high-end support options to continue service, most users should replace the device as soon as it hits EOSL.

### Legacy Systems and Mitigation
Organizations often struggle with **legacy devices**—older systems, applications, or middleware that have reached EOL or EOSL but are still in use. These systems may be **critical to organizational goals**, making them difficult to turn off or replace immediately. 

When a legacy device cannot be easily phased out, **mitigation strategies** can be implemented to protect it, such as:
-   **Firewall rules** to limit who can connect to the device.
-   **IPS signatures** specifically designed for older operating systems.
-   Developing a clear **path to replacement** while these security measures are in place.

## Virtualization Vulnerabilities

In modern cloud infrastructures, virtual machines can be built and torn down almost instantly and in large numbers. This constant churn makes it difficult to maintain a consistent **security posture** compared to managing traditional, static devices.
-   **Diverse Configurations:** VMs often have unique configurations involving different numbers of operational CPUs, varying memory, and storage capacities. Despite these differences, they run standard operating systems (OSes) like Windows or Linux and require the same **security best practices** as physical hardware.
-   **Shared Vulnerabilities:** Virtual environments remain susceptible to common security issues, including **local privilege escalation**, **command injection**, and **information disclosure**.

### VM Escape
A **VM escape** occurs when an attacker manages to move from one guest virtual machine to another on the same hypervisor.
-   **Security Risk:** While VMs are designed to be self-contained, an escape allows an attacker to bypass isolation. Since a single hypervisor might manage hundreds of VMs, a successful escape provides access to an enormous amount of data across many systems simultaneously.
-   **Real-World Example:** At the **2017 Pwn2Own competition**, researchers demonstrated a VM escape. They used a bug in the JavaScript engine of Microsoft Edge to escape a browser sandbox, exploited a Windows 10 kernel vulnerability to gain guest OS access, and finally used a hardware simulation bug in VMware to jump to another VM on the same hypervisor. This demonstration allowed the vendor to create and roll out a patch before the exploit could be widely used.

### Resource Reuse and Hypervisor Management
The **hypervisor** acts as the manager between physical hardware and the virtual world, allocating resources like CPU, memory, and storage.
-   **Over-allocation:** Hypervisors often <ins>allocate</ins> more virtual <ins>resources</ins> than are physically <ins>available</ins> (e.g., allocating 6GB of RAM across three VMs on a host that only has 4GB of physical RAM), relying on the fact that not all VMs will need all resources at once.
-   **Memory Sharing Issues:** Because resources are shared, a bug in the hypervisor’s memory management can lead to **resource reuse** issues. If the hypervisor does not properly restrict information sharing, it is possible for one VM to write to a memory area that another VM can then read. Keeping the hypervisor code updated is essential to preventing this type of unauthorized data access.


## Cloud-specific vulnerabilities

There are several critical cloud-specific vulnerabilities and security challenges organizations to face when moving applications and data to the cloud.

### Security Best Practices and Statistics
While organizations have rapidly embraced the cloud for applications and sensitive data, they often fail to follow security best practices. Specifically, it is estimated that **76% of organizations do not use multifactor authentication (MFA)** to log into their central cloud consoles. Furthermore, up to **63% of the code currently in the cloud is unpatched**, with many of these vulnerabilities carrying a **Common Vulnerability Scoring System (CVSS) score of 7 or higher**.

### Public Accessibility and Denial of Service
Because applications in a public cloud are designed to be accessible to anyone, they are inherently vulnerable to connection attempts from anywhere in the world. This accessibility makes them targets for **Denial of Service (DoS)** or **Distributed Denial of Service (DDoS)** attacks, where multiple devices simultaneously attempt to disable an application.

### Authentication and Configuration Issues
Proper configuration of the application and its surrounding security is vital. Weak or **misconfigured authentication processes** can result in significant data breaches by allowing unauthorized users access without proper credentials. A common misconfiguration is **directory traversal**, which allows users to manually navigate into unauthorized folders or subdirectories on a web server.

### Unpatched Systems and Software Vulnerabilities
Unpatched operating systems and applications are major risks that can lead to **remote code execution (RCE)**, allowing an attacker to run any application they choose on a cloud-based system. Notable examples of easily exploited application vulnerabilities include **Log4j** and **Spring Cloud Function**, which can allow an attacker to gain full control of the underlying system and potentially pivot to other systems within the same cloud.

### Application-Level Attacks
Attackers also exploit weaknesses in application code and memory management:
-   **Input Validation Failures:** If developers do not properly validate input fields, attackers may use **cross-site scripting (XSS)** to gain access.
-   **Out-of-Bounds Write:** This occurs when an attacker writes information into unauthorized sections of memory, which can cause a **system crash** or facilitate **remote code execution**.
-   **Code Injection:** Attackers may use techniques like **SQL injection** to gain direct access to sensitive data stored in cloud databases.

## Supply Chain Vulnerabilities

The supply chain is the entire process of moving a product from raw materials to the final consumer. Security concerns exist at every step, including processing, manufacturing, distribution, and consumption, as attackers can inject malicious code or gain unauthorized access at any point.

### Third-Party Service Providers
Outsourcing services to third parties introduces <ins>significant risk</ins> because the organization must <ins>rely</ins> on the <ins>provider's security posture</ins>. If a provider has access to your systems or sensitive data, a breach of their network can lead directly to a breach of yours.
-   **Breadth of Risk:** Providers can include IT services, utilities, office cleaning, payroll, accounting, and cloud infrastructure.
-   **Security Audits:** It is common for organizations to include the right to perform **ongoing security audits** in their contracts with service providers to verify their security processes.
-   **The Target Breach (2013):** A major example occurred when over 40 million credit cards were stolen from Target. The breach began with an HVAC (heating and air conditioning) vendor that was infected with malware via email. Because Target’s HVAC systems and cash register systems were on the **same unsegmented network**, attackers gained access to every cash register in every store. The breach went undetected for months.

### Hardware Vulnerabilities
Hardware such as routers, switches, and firewalls can be compromised before they are even installed.
-   **Verification:** Organizations should use a small list of **trusted vendors** rather than buying from unknown sources online. Policies should be in place to treat new hardware as **untrusted out of the box**.
-   **Counterfeit Hardware:** In 2022, the Department of Homeland Security arrested a reseller who sold over $1 billion in **counterfeit Cisco products**,. These devices, mostly manufactured in China, looked like legitimate products but were prone to breaking or even catching fire. Because these devices sit at the core of network infrastructure, they are ideal for gathering information.

### Software Vulnerabilities
Software updates and installations require a high level of trust, which can be exploited by attackers.
-   **Digital Signatures:** One way to verify software is through **digital signatures**, which most operating systems validate during installation to ensure the file hasn't been tampered with.
-   **Automated Updates:** These pose a unique challenge because the user is often not involved in the process, requiring total trust in the provider.
-   **SolarWinds Orion Breach (2020):** This was a massive supply chain exploit where attackers gained access to SolarWinds' internal infrastructure and injected malicious code into their software updates. Because the software was **digitally signed** by SolarWinds, 18,000 customers—including Fortune 500 companies and US federal agencies like the Pentagon and Treasury—installed the malicious update without suspicion. The breach was not detected for approximately six months.

## Misconfiguration Vulnerabilities

Misconfiguration vulnerabilities can lead to <ins>data exposure</ins> and <ins>unauthorized access</ins>. The key areas of concern include unsecured data repositories, administrative account weaknesses, the use of insecure protocols, default credentials, and firewall misconfigurations.

### Unsecured Data and Cloud Storage
One common vulnerability is leaving sensitive information in **open areas of the internet**, such as unsecured cloud services. Attackers frequently use this for **reconnaissance**, searching for data that owners forgot to secure so they can download and disseminate it.
A notable example occurred in June 2017, when **14 million Verizon records** were left exposed in an open Amazon S3 repository without passwords or security. While a researcher found these records before an attacker could, it highlights the risk of data being made public without the owner's intention.

### Unsecured Administrative Accounts
**Privileged accounts**, such as "root" in Linux or "administrator" in Windows, present a significant security challenge. While operating systems often try to prevent creating these accounts without passwords, administrators frequently assign **easy-to-guess passwords** like "123456" or "ninja," making them susceptible to **brute force attacks**. To mitigate this, best practices include:
-   **Disabling direct login** for administrative accounts.
-   Logging in with a **normal user account** and using elevated access (such as **su**, **sudo**, or **Run as administrator**) only when necessary.
-   **Limiting the number of accounts** with root or administrator access to reduce the attack surface.

### Insecure Protocols and Cleartext Data
Encryption is ineffective if data is sent using **insecure protocols** that do not support it. Protocols like **Telnet, FTP, SMTP, IMAP, and HTTP** send traffic across the network "**in the clear**," meaning anyone performing a **packet capture** (using tools like Wireshark) can read everything, including browser versions, cookies, and URLs.
-   **Secure alternatives** should be used, such as **SSH, SFTP, and HTTPS**.
-   The "**Wall of Sheep**" at the DEFCON security conference demonstrates the danger by displaying email addresses and partial passwords harvested from attendees using insecure wireless protocols like POP3 or HTTP.

### Default Credentials and the Mirai Botnet
Many devices, particularly **Internet of Things (IoT)** devices like cameras and routers, come with **default usernames and passwords**. Some devices do not even prompt the user to change these credentials upon the first login. The **Mirai botnet**, which is now open-source software, specifically targets these devices by scanning for over **60 default configurations** to gain access and recruit them into the botnet.

### Open Ports and Firewall Misconfigurations
Every time an inbound service is enabled, a **port number** is opened, providing a point of access into a server. It is critical to **limit the number of open ports** to reduce potential entry points for attackers. 
-   **Firewalls** are used to manage this access, but their rule sets are often large and complex. 
-   **Complexity** can lead to mistakes where an administrator accidentally provides access to a device or port that should remain restricted.
-   **Periodic audits** of firewall rule bases are recommended to ensure the network remains secure and that unnecessary ports are closed.

## Mobile Devices Vulnerabilities

Mobile devices present unique security challenges because they are **small, easily hidden, and constantly in motion**, making them difficult to manage and track. These devices contain **sensitive personal and organizational information** and are vulnerable to remote access because they are constantly connected to the internet.


### OS-Level Vulnerabilities: Jailbreaking and Rooting
-   **Definition:** Bypassing a device's built-in security by replacing the original operating system or firmware with a third-party version is known as **rooting** on Android devices and **jailbreaking** on Apple iOS devices.
-   **Purpose:** Users typically do this to enable new features or circumvent security restrictions that exist on the original OS.
-   **Security Risk:** If an employee replaces their device's OS, they effectively **bypass all security controls** implemented through a Mobile Device Manager (MDM).

### Application Vulnerabilities
-   **Malicious Apps:** A single malicious application can expose all data on a device to an attacker.
-   **Sideloading:** This refers to the practice of **installing applications from outside authorized sources**, such as a company's global application library or a local app store. 
-   **Connection to Rooting:** Once a device has been rooted or jailbroken, a user is generally able to sideload any application they choose, which significantly increases the risk of installing malicious code.

### Policy and Management
-   **MDM Restrictions:** Mobile Device Managers are used to restrict the types of applications that can be installed and define the authorized sources for those installations.
-   **Administrative Controls:** Organizations typically have specific policies, such as **Acceptable Use Policies (AUPs)** or employee handbooks, that forbid the installation of unauthorized software or operating systems.
-   **Consequences:** Because bypassing these security controls is a serious risk, employees who violate these policies may be subject to dismissal.

## Zero-Day vulnerabilities

Most applications and operating systems currently in use likely contain **undiscovered security vulnerabilities**. These vulnerabilities are eventually discovered by either security researchers, who share the information with developers, or attackers, who seek to exploit them. 

An attacker’s goal is to find these holes first so they can take advantage of them before a **patch** is created to stop them. Because attackers do not share this information with software vendors, the vendors remain unaware that a problem exists. 

### Zero-Day Attacks and Mitigation
A **zero-day attack** occurs when attackers begin exploiting a vulnerability for which no patch or mitigation currently exists. From the vendor's perspective, the vulnerability has not yet been discovered, making it extremely difficult to protect a system against it. Once the security community identifies a new type of attack, there is a "flurry of work" to quickly create a patch. Until that patch is released, the attacker can continue to exploit the vulnerability.

To stay informed about these threats, visit the [Common Vulnerabilities and Exposures (CVE) website](http://cve.mitre.org).

### Real-World Examples (2023)
Several major zero-day attacks were documented in early 2023:
-   **Google Chrome (April 2023):** A zero-day attack involving **memory corruption** and a **sandbox escape**.
-   **Microsoft (May 2023):** An attack where **self-signed code** ran during the UEFI boot process, which should be prevented by secure boot.
-   **Apple iOS and iPadOS (May 2023):** Three separate zero-day attacks were patched, covering **sandbox escape**, **disclosure of sensitive information**, and **arbitrary code execution**.

Many of these exploits were actively being used "in the wild" before patches were created by Google, Microsoft, and Apple to close the security holes.

## Malware Introduction

**Malware** is a broad term describing any software designed to perform malicious actions on a system. This includes gathering keystrokes, displaying profit-generating advertisements, or infecting systems to encrypt data.

### Malware Categories
-   **Viruses and Worms:** Programs that infect systems; worms specifically can automatically propagate between systems by exploiting known vulnerabilities.
-   **Ransomware:** Software that encrypts storage drives and demands payment for recovery.
-   **Trojan Horses:** Software that appears to perform a legitimate function but actually installs malware.
-   **Other Categories:** Rootkits, keyloggers, spyware, bloatware, and logic bombs.

### How Malware Operates
Malware types often work in tandem rather than as isolated events. For instance, a worm might exploit a vulnerability to install itself and then download a **remote access backdoor**, allowing an attacker to manually install additional malicious tools. 

Common methods of infection include:
-   **User Action:** Clicking links in email messages or interacting with website pop-ups.
-   **Drive-by Downloads:** Malicious software that is automatically downloaded to a system without the user clicking anything.
-   **System Vulnerabilities:** Exploiting undiscovered or unpatched flaws in applications and operating systems.

### Motivation: The Value of Data
The primary reason malware exists is that data is highly valuable to attackers. For individuals, this includes family archives, photos, and important documents. For organizations, attackers target planning documents, employee personal information, and financial details. Attackers exploit this value either by selling the data or by forcing the owner to pay for its recovery.

### Ransomware and Recovery
**Ransomware** has become a significant business model for attackers. It typically <ins>encrypts</ins> personal files — such as movies and documents — while <ins>leaving the operating system functional</ins> so the victim can read the ransom demands. Attackers usually demand **cryptocurrency** in exchange for a decryption key. 

Here are some best practices to protect yourself against these threats:
-   **Offline Backups:** Maintaining "known good" backups stored offline ensures that if a system is infected, the ransomware cannot reach and encrypt the backup as well.
-   **Regular Updates:** Keeping the operating system and all applications updated to the latest versions closes security vulnerabilities that malware might exploit.
-   **Anti-malware Software:** Using antivirus tools that identify malicious code through **signatures** is essential, though these signatures must be kept up to date to recognize the newest threats.


## Viruses and worms

### Computer Viruses
A computer virus is a type of malware designed to <ins>replicate itself</ins> from one computer to another, much like a biological virus. Key characteristics include:

-   **Requirement for Intervention:** A virus typically requires some form of **human intervention**, such as clicking a malicious link or running an executable file.
-   **Behavior:** Once active, a virus can <ins>move through</ins> a computer's <ins>file system</ins> or attempt to <ins>access</ins> other <ins>systems</ins> across a <ins>network</ins>. While many cause noticeable downtime or outages, some operate quietly in the background without the user’s knowledge.
-   **Common Types:**
    -   **Application/Executable:** The standard type that runs when a user interacts with a link or file.
    -   **Boot Sector:** These reside in the system's boot sector and run automatically every time the computer starts up.
    -   **Scripts and Macros:** Malicious code written in scripting languages or macro languages (like those in Microsoft Office) to exploit vulnerabilities in applications or the operating system.
-   **Fileless Viruses:** This specific type is designed to **avoid detection** by never writing code to the computer's storage drive. Instead, it operates entirely within the system's **memory**. 
    -   **Infection Process:** Typically starts with a user clicking a link that leads to a website exploiting a vulnerability (e.g., in Java or Windows). 
    -   **Persistence:** It may use tools like PowerShell to download and run further scripts. To survive a system reboot, it often adds an "autostart" entry to the Windows registry so it can re-infect the memory upon startup.


[Fileless virus infection process](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773247661/Fileless_virus_infection_process_ioknyt.png)

### Computer Worms
Worms are a distinct category of malware characterized by their ability to **self-replicate** without any user intervention.

-   **Speed and Efficiency:** Because they do not need a human to click anything, worms can spread extremely quickly, moving across networks at the speed of the network itself. 
-   **Network Impact:** They move freely between networked systems and can attack at any time.
-   **Defense Mechanisms:** Technologies like network-based and personal **firewalls**, as well as **Intrusion Prevention Systems (IPS)**, are critical for stopping worms. These systems use signatures to identify and block the worm's traffic.
-   **Example (WannaCry):** A well-known example is the **WannaCry worm**, which automatically propagated across networks. It utilized the "EternalBlue" exploit to install backdoors and then deployed **ransomware** to encrypt user files and demand payment.

[Worm infection process](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773247755/Worm_infection_process_rwxntf.png)

### Protection Methods
There are some ways to defend against these threats:
-   **Antivirus Software:** Many operating systems include antivirus that monitors for known malicious executables.
-   **Signature Updates:** It is vital to keep antivirus "signature files" updated so the software can recognize the latest identified threats.
-   **Firewalls and IPS:** These are specifically effective against the automated propagation of worms.

## Spyware and bloatware

Let's focus on two types of unwanted software: **spyware** and **bloatware**.

### Spyware
**Spyware** is a type of malware that **monitors all activity** on your system. It is typically installed through peer-to-peer software, fake security programs, or malicious email links. 

-   **Malicious Actions:** Spyware can display unwanted advertising, **steal personal information**, or commit affiliate fraud to earn money from your online purchases. It monitors browsing habits and may include a **keylogger** to capture everything you type, including **usernames and passwords**, which are then sent to an attacker's server.
-   **Persistence and Defense:** This code often embeds itself deep within the operating system, making it **difficult to uninstall**. To protect against it, you should:
    -   Use **anti-malware or anti-virus software** to stop spyware from executing.
    -   Research software before installation and only use **trusted sources**.
    -   Maintain a **known good backup** to recover your system if infected.
    -   Utilize specialized third-party tools like **Malwarebytes** to identify and remove malicious code.

### Bloatware
**Bloatware** refers to the **unnecessary applications** pre-installed on new computers or mobile devices by the hardware manufacturer. Manufacturers are generally paid to include these "extra" apps, which can include games, security tools, and other utilities not part of the core operating system.

-   **Security and Performance Concerns:** Bloatware is problematic because it consumes **storage space** and may run automatically at startup, reducing the **efficiency of the operating system**. Crucially, these apps may contain **vulnerabilities** (known or unknown), creating a security risk on a brand-new device.
-   **Removal Methods:** While some bloatware can be manually removed through the operating system's standard **Uninstall** feature or the app's own uninstaller, some do not provide an obvious way to be removed. In cases where standard methods fail, specialized **third-party uninstallers** can be used to force the removal of the code.

## Other type of malwares

### Keyloggers

**Keyloggers** are a type of malware designed to capture **every keystroke** a user makes, allowing attackers to steal sensitive data like **usernames, passwords, credit card information**, and financial details. Attackers target keyboard input because, unlike network traffic or stored files, the process of typing is **not encrypted**. Keylogging software typically stays resident on a system, records keystrokes to a file, and sends that file to the attacker periodically. Advanced keyloggers can also capture **clipboard data, screenshots, instant messages**, and search engine queries. An example is the **DarkComet Remote Access Trojan (RAT)**, which can log specific actions like the use of the space bar or delete key to reconstruct exactly what the user typed.

### Logic bombs

A **logic bomb** is malicious software that waits for a **specific event or time** to occur before "detonating" and performing actions like rebooting the system or erasing data. Triggers can include a specific date or a particular user logging into the system. Because logic bombs are often custom-created for a specific goal, they generally lack **antivirus signatures**, making them extremely difficult to identify. A real-world example occurred in **South Korea in 2013**, where a logic bomb triggered at a specific time, deleting storage and the **master boot record** of systems at banks and broadcasting companies. This attack even affected **ATMs**, leaving them unable to find an operating system after rebooting. To mitigate this risk, organizations should monitor for changes to core system files and ensure users only have the **minimum necessary permissions**, rather than universal administrator rights.

### Rootkits

**Rootkits** are named after the Unix "root" superuser and typically hide themselves within the **operating system kernel**. Because they become part of the OS itself, they are effectively **invisible** to traditional antivirus or anti-malware software and will not appear in standard task or process lists. While some rootkits run as traditional processes and can be identified by anti-malware, those in the kernel have full control of the computer. If a system is infected, specific **standalone removal tools** may be required for mitigation. To prevent rootkits from running, systems use **Secure Boot** (part of the UEFI BIOS), which confirms the operating system's signature hasn't changed before allowing the system to boot.

## Physical Attacks

**Physical attacks** are security concerns that occur at the physical level, independent of the operating system version or digital vulnerabilities being used. These attacks are critical because having physical access to a system often translates to having **full control** over it, allowing an attacker to <ins>circumvent</ins> the <ins>operating system</ins> entirely.

There are different types of physical attacks:

-   **Brute Force:** While often associated with passwords, brute force in a physical context involves <ins>forcing open</ins> locked doors or windows to <ins>gain access</ins> to a building or data center. It's suggested to assess the physical security of an infrastructure to determine how difficult it would be for an attacker to gain access this way.
-   **RFID Cloning:** Attackers can use inexpensive duplicators (often costing less than $50) to clone RFID-based access badges or key fobs. This process is very fast, taking only seconds, and can be done discreetly in public places, such as by brushing up against someone on a train. 
    -   **Mitigation:** The use of **multi-factor authentication (MFA)**—such as requiring a PIN or biometrics in addition to the badge—is recommended to prevent access even if a card is successfully duplicated.
-   **Environmental Attacks:** If an attacker cannot access a system directly, they may attack the environment surrounding it. Examples include:
    -   **Power Disruption:** Turning off a data center's power, which can sometimes be done from outside the building.
    -   **HVAC Manipulation:** Gaining access to HVAC (Heating, Ventilation, and Air Conditioning) control systems to turn off cooling. This causes equipment to overheat and automatically shut down.
    -   **Fire Suppression:** Manipulating fire suppression systems to cause a denial of service.

## Denial of service (DoS) Attacks

A **Denial of Service (DoS)** occurs when an attacker intentionally <ins>forces</ins> a service to <ins>fail</ins>, often by <ins>overloading it</ins> so legitimate users cannot gain access or by <ins>exploiting known software vulnerabilities</ins> or design failures. Beyond software exploits, a DoS can be as simple as removing power from a system.

There are different forms and causes of these service failures.

### Intentional and Unintentional Causes
-   **Competitive Advantage:** Organizations may target third parties to gain a competitive edge or use a DoS as a "smokescreen" to distract from other security exploits occurring elsewhere.
-   **Accidental DoS:** Self-inflicted outages can occur through networking mistakes, such as plugging two switches together to create a **loop** without running spanning tree. 
-   **Resource Exhaustion:** Simply downloading a large file (like a Linux distribution) over a small bandwidth connection can consume all available resources for production applications.
-   **Environmental Factors:** Physical infrastructure failures, such as a water line breaking above a data center, can also result in a denial of service.

### Distributed Denial of Service (DDoS)
A **DDoS** attack uses multiple devices scattered globally to overwhelm a target's bandwidth or resources. 
-   **Botnets:** Attackers use malware to create "botnets"—networks of "robot" computers under their control. A single command from a central facility can trigger millions of devices to attack a target simultaneously.
-   **Asymmetric Threat:** This is considered an asymmetric threat because an attacker with relatively few resources can bring down much larger organizations. For example, the **Zeus botnet** controlled over 3.6 million computers at its peak.

### Amplification and Reflection Attacks
Attackers often use **amplification** to make their attacks more efficient by turning small amounts of data into very large amounts.
-   **Protocol Exploitation:** This method takes advantage of common internet protocols like **NTP, ICMP, and DNS**, where a request typically results in a much larger response.
-   **DNS Amplification Example:** An attacker can send a DNS query of only 15 characters (requesting all information for a domain) that results in a response of approximately 1,300 characters—an amplification of about **86 times**.
-   **The Process:** The attacker sends commands to a botnet to query **open DNS resolvers**. These queries use a **spoofed IP address**, so the massive amplified responses are directed at the victim's web server instead of the attacker, effectively overwhelming the target.

## DNS Attacks

There are various methods attackers use to manipulate the **Domain Name System (DNS)** to redirect users to malicious websites.

### DNS Poisoning Attacks
DNS poisoning involves <ins>redirecting</ins> a <ins>user</ins> from a <ins>legitimate</ins> IP address to one <ins>controlled</ins> by <ins>an attacker</ins>. This can be achieved through several methods:

-   **Modifying DNS Servers:** Attackers may attempt to <ins>change</ins> the <ins>configuration</ins> of a DNS server itself by identifying vulnerabilities or obtaining administrative credentials. While effective for redirecting all users of that server, these systems are generally well-protected and difficult to breach.
-   **Modifying Local Host Files:** A more accessible target is the local "host" file on a client's computer. Since a computer checks its local file for domain resolution before querying a DNS server, an attacker with elevated rights can modify this file to redirect the user.
-   **On-path (Man-in-the-Middle) Attacks:** An attacker can intercept a DNS query in real-time and reply with a malicious IP address before the legitimate server can respond.
-   **Domain Registration Hijacking:** Attackers may target the domain registerer account using social engineering, brute force, or leaked credentials. Gaining access allows them to change the DNS settings for the entire domain.
    -   **Real-world Example:** In October 2016, attackers hijacked 36 domains belonging to a major Brazilian bank for six hours. This allowed them to collect usernames and passwords from a customer base of over 5 million people.

### URL Hijacking (Typosquatting and Brandjacking)
This technique relies on users making mistakes when typing a web address into their browser. Attackers register similar-looking domain names to achieve various goals, such as generating ad revenue, redirecting traffic to competitors, harvesting login credentials, or distributing malware and ransomware. 

Common variations include:
-   **Misspellings:** Using a slightly different spelling, such as "professormessor.com" instead of the legitimate "professormesser.com".
-   **Omitted Letters:** Leaving out a character, such as forgetting the final "s" in a domain name.
-   **Added Letters:** Including extra characters, such as "professormessers.com".
-   **Top-Level Domain (TLD) Swapping:** Using the same name but a different extension, such as .org instead of .com.

### Prevention and Protection
To protect against these attacks, it is recommended to **carefully inspect URLs** before visiting them to ensure they are correct and to **avoid clicking links** within emails.


## Wireless Attacks

There are two primary types of wireless attacks that function as **Denial of Service (DoS)**: wireless deauthentication attacks and radio frequency (RF) jamming.

### Wireless Deauthentication Attacks
This attack occurs when a user is suddenly and repeatedly disconnected from a wireless network without warning or error messages.

-   **Mechanism:** The attack exploits **management frames**, which are messages sent behind the scenes between a device and an access point to manage connections. In earlier versions of the 802.11 specification, these management frames were sent "in the clear" without encryption.
-   **Execution:** An attacker can capture these unencrypted frames to identify details like the **SSID** (network name), supported rates, and the **MAC addresses** (hardware addresses) of both the access point and the victim's device. By using utilities like `airodump-ng` to identify targets and `aireplay-ng` to send spoofed deauthentication frames, an attacker can force a specific device off the network. As long as these frames are continuously sent, the device cannot reconnect.
-   **Prevention:** The IEEE 802.11 committee addressed this by updating the specification, starting with **802.11ac**. In these newer standards, management frames such as "disassociate" and "deauthenticate" are **encrypted by default**. However, some frames like beacons and probes still appear in the clear because they must be sent before encryption can be established.

### Radio Frequency (RF) Jamming
Unlike a deauthentication attack that can target a single device, RF jamming is a DoS attack that affects **everyone** communicating over the targeted wireless frequencies.

-   **Mechanism:** The attacker sends interfering wireless signals to decrease the **signal-to-noise ratio**. If the "noise" becomes louder than the actual data signals from the access point, devices cannot hear or transmit traffic.
-   **Types of Jamming:**
    -   **Unintentional:** Jamming can happen accidentally from household items like **microwave ovens** (affecting 2.4 GHz networks) or **fluorescent lights**.
    -   **Intentional:** Attackers may send constant information, random data, or a flood of legitimate frames to create noise.
    -   **Reactive Jamming:** This is a more sophisticated method where the attacker only sends a jam signal when they detect someone trying to communicate, making the problem harder to troubleshoot.
-   **Localization (Fox Hunting):** Because an attacker must be physically near the access point to jam it, they can be located through a process called a **"fox hunt"**. This involves using a **directional antenna** to find where the signal is strongest and an **attenuator** to lower the signal strength as the "hunter" gets closer, allowing them to triangulate and locate the source of the interference.

## On-path Attack

An **on-path attack** (formerly known as a **man-in-the-middle attack**) occurs when an attacker positions themselves <ins>between two devices to monitor</ins> and potentially <ins>modify their communication</ins> in real time. These attacks are typically **invisible** to the victims, who remain unaware that their traffic is being intercepted.

There are two specific types of on-path attacks.

### ARP Poisoning
This attack occurs on a **local IP subnet** and exploits the Address Resolution Protocol (ARP), which lacks built-in security, encryption, or authentication.

-   **Standard Process:** Normally, a device broadcasts a [request](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773572864/ARP_Poisoning_Image_1_zw4pv7.png) to find the MAC address associated with an IP address (like a router). Once [received](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773572995/ARP_Poisoning_Image_2_rjzm10.png), the device saves this information in a local **ARP cache** to use for future communication.
-   **The Attack:** An attacker [sends a fake ARP response](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773573153/ARP_Poisoning_Image_3_boydqx.png) to a victim’s device, claiming their own MAC address belongs to the target IP (e.g., the router). Because ARP does not verify these messages, the victim’s device [overwrites its cache](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773573251/ARP_Poisoning_Image_4_hflkyd.png) with the attacker's information.
-   **Consequences:** Once the cache is "poisoned," all traffic intended for the router is sent to the attacker instead. The attacker can then:
    -   **Monitor** the traffic.
    -   **Modify** the information being sent.
    -   **Terminate** the connection entirely.

### On-path Browser Attack
Also known as a **man-in-the-browser attack**, this version takes place on the victim's own device rather than across the network.

-   **Mechanism:** Malware or a Trojan is installed on the device and configured as a **proxy**. This allows the attacker to redirect traffic before it is sent to the network and after it is received.
-   **Bypassing Encryption:** Because the malware resides on the same device as the victim, it can see information "in the clear" even if the network traffic itself is **encrypted**.
-   **Impact:** The malware typically waits for the victim to log into sensitive sites, such as a bank. It captures credentials (usernames and passwords) and can even initiate **hidden sessions** to transfer money or data without the victim's knowledge.


## Replay Attack

A **replay attack** occurs when an attacker <ins>captures information</ins> sent between a client and a server and subsequently reuses that information to <ins>impersonate</ins> the victim. While the replay itself is not an "on-path" attack, attackers frequently use on-path methods to gather the necessary data.

There are two primary forms of replay attacks, the methods used to execute them, and how to prevent them.

### Common Types of Replay Attacks
-   **Pass the Hash:** During a normal authentication process, an attacker captures the victim's username and hashed password. By replaying these credentials to the server, the attacker can successfully authenticate and gain access while posing as the original client.
-   **Session Hijacking (Side jacking):** Attackers target **browser cookies**, which store session IDs and tracking information. If an attacker gains access to a valid session ID, they can connect to a web server without needing any login credentials, effectively taking over the victim's active session.

### Methods and Tools for Data Collection
To perform these attacks, an attacker must first obtain sensitive traffic or files using various techniques:
-   **Network Redirection/Monitoring:** This includes using physical network taps, **ARP poisoning** to redirect traffic, or packet capture software like **Wireshark** and **Kismet**.
-   **Malware and Exploits:** Attackers may place malware on a victim's computer or use **cross-site scripting (XSS)** to steal session details and send them to the attacker's system.
-   **Header and Cookie Manipulation:** Tools such as **Tamper**, **Firesheep**, and **Scapy** allow attackers to view or modify headers and cookie information.

### Prevention and Mitigation
There are some strategies to defend against these attacks:
-   **Encryption:** The most effective defense is to **encrypt all traffic end-to-end** using **HTTPS**. If end-to-end encryption isn't possible, using a **VPN** provides encryption for at least the first part of the data's journey.
-   **Salting and Hash Management:** Adding a unique "salt" to passwords ensures that a different hash is generated every time authentication occurs. Additionally, servers can be configured to **reject the same hash twice in a row**.
-   **Browser Security:** Users can use browser extensions that force HTTPS connections and prevent data from being sent in the clear.

## Malicious Code

There are various methods the attackers can use to gain access to systems by using **malicious code**. While some attacks rely on non-technical methods like **social engineering**, **default credentials**, or **misconfigurations**, malicious code requires a higher level of technical expertise.

### Forms and Delivery of Malicious Code
Malicious code can be delivered and executed through several different methods, including:
-   **Executables** and **scripts** running on a system.
-   **Macro viruses** and **Trojan horses**.
-   Exploiting vulnerabilities like **SMB (Server Message Block) version 1**, which was used in the **WannaCry ransomware** attacks to allow **arbitrary code execution** and gain access to the operating system.
-   **Cross-site scripting (XSS)**, such as the 22 lines of malicious **JavaScript** placed on the British Airways website to steal credit card information from approximately 380,000 victims.
-   **SQL injection**, which was used to breach the **Estonian Central Health Database** and access the health information of the entire country's citizens.

### Defense Strategies
There are many ways malicious code can be used so, a **strong, multi-layered defense** is advised :
-   **Anti-malware software**: Used to block malicious executables, scripts, and macro viruses.
-   **Firewalls**: Implemented to block known malicious traffic from passing through the network.
-   **Continuous updates and patches**: Essential for closing security vulnerabilities that attackers might exploit.
-   **User training**: Educating users on **secure computing habits**, such as not sharing information over the phone or clicking unknown links in emails, to prevent successful social engineering and malware delivery.

## Application attacks

### Injection Attacks
An **injection attack** occurs when an attacker adds malicious code to input sent to a server or client. These attacks succeed when an application fails to perform proper input validation. While **SQL injection** is the most common type, others include **HTML, XML, and LDAP** injections.

### Buffer Overflows
A **buffer overflow** happens when an attacker inputs more information than a variable's reserved memory area can hold, causing the data to spill over into adjacent memory buffers. This is enabled by a lack of input checks within the application. Although these attacks often simply crash an application, a consistent and repeatable buffer overflow can be a very powerful exploit.

### Replay Attacks
In a **replay attack**, an attacker captures information (such as **username/password hashes or session IDs**) from a network or a victim's computer and "replays" it to a server to gain unauthorized access. Attackers may gather this data via network taps, ARP poisoning, malware, or by combining it with an **on-path attack**.

### Privilege Escalation
This attack involves exploiting a bug or vulnerability to gain higher-level permissions than originally granted. 
-   **Vertical Privilege Escalation:** Attempting to gain administrator or "system" level access.
-   **Horizontal Privilege Escalation:** Moving from one standard user's access level to another (e.g., from User A to User B).

**Prevention methods** include patching vulnerabilities, updating antivirus signatures, and using **Data Execution Prevention (DEP)** to limit where executables can run in memory. Additionally, operating systems can **randomize data storage locations** in memory to make vulnerabilities harder to find.

### Cross-Site Request Forgery (CSRF/XSRF)
Commonly called "**sea surf**," "session riding," or a "one-click attack," this exploit takes advantage of the trust a web server has in a user’s browser. Because browsers often load content from multiple servers (like YouTube or Instagram) without re-authentication, an attacker can trick a logged-in user into clicking a malicious link. This causes the browser to <ins>send unauthorized requests</ins>—such as transferring bank funds—to a server that already trusts the user's session. Applications can defend against this using **cryptographic tokens** for each transaction.

### Directory Traversal
Often resulting from a web server **misconfiguration**, a directory traversal allows an attacker to read or write files outside the designated web directory. Attackers use the `../` **command** in a URL request to move backward through the file system to access restricted areas, such as the Windows system directory.

## Cryptographic Attacks

In most cryptography, the **key** is the critical factor that determines whether data is secure. When attackers cannot access the key, they instead <ins>attack</ins> the <ins>cryptography itself</ins> by looking for <ins>weaknesses</ins> in <ins>protocols</ins> and algorithms</ins>. Because these algorithms are typically public, they can be scrutinized for workarounds; those that withstand this testing over time are considered trustworthy. If an algorithm is secure, attackers often pivot to targeting its **implementation**, which is frequently the weakest link.

### Algorithm Attacks: The Birthday Attack
One primary attack against algorithms is the **birthday attack**, which is based on the statistical probability of matches within a set. 
-   **The Probability:** In a room of 23 people, there is a 50% chance that two people share a birthday; with 30 people, that chance rises to 70%.
-   **Hash Collisions:** In cryptography, this concept is applied to find a **hash collision**, where two different plaintexts result in the exact same hash.
-   **Discovery and Prevention:** Collisions are typically found through **brute-force** processes, where an attacker tries every possible plaintext to find duplicates. Using a **very large hash output size** makes it significantly more difficult for an attacker to find a duplicate.

### Case Study: MD5 (Message Digest Algorithm 5)
The MD5 algorithm is a notable example of a failed cryptographic standard. Although published in 1992, researchers discovered collisions by 1996. By 2008, researchers successfully used MD5 collisions to create a fraudulent, yet seemingly legitimate, digital certificate from a **Certificate Authority (CA)**. Because MD5 could produce identical hashes for plaintexts with minor differences, the industry transitioned to more secure hashing algorithms.

### Implementation Attacks: Downgrade Attacks and SSL Stripping
A **downgrade attack** occurs when the <ins>implementation</ins> of a secure algorithm is <ins>flawed</ins>, allowing an attacker to force two devices into using weaker encryption or no encryption at all. 

**SSL Stripping** is a common form of downgrade attack that functions as an **on-path attack**.

[SSL Stripping](https://res.cloudinary.com/dnhgctqsu/image/upload/v1773920868/SSL_Stripping_ngtmp2.png)

The process works as follows:
-   **Interception:** An attacker sits in the middle of the communication between a visitor and a web server.
-   **The Request:** When a visitor makes an initial HTTP request, the attacker acts as a **proxy**, passing the request to the server but intercepting the server’s attempt to redirect the user to the secure **HTTPS** version of the site.
-   **The Split Connection:** The attacker establishes a secure HTTPS connection with the web server while maintaining an unencrypted **HTTP** connection with the victim.
-   **Data Theft:** Because the victim is communicating in the clear, the attacker can read sensitive information, such as **usernames and passwords**, and use them to log in to the server on the victim's behalf.
-   **Ongoing Monitoring:** All subsequent communication between the visitor and the server is captured, viewed, or potentially modified by the attacker.

## Password Attacks

Storing credentials in a **non-encrypted form**, known as **plain text** or "in the clear," is a significant security risk. If an attacker gains access to a file or database containing plain-text passwords, they can take advantage of that information immediately. If an application uses this method, it's advised to either **discontinue its use** or have the developer rewrite it to store passwords as **hashes**.

**Hashing** takes a variable-length input (the password) and represents it as a **fixed-length string** of text, often called a "message digest" or a "fingerprint". Key characteristics of hashing include:
-   **Unique Outputs:** Different inputs produce very different outputs; even a single-character change in a password results in a completely different hash.
-   **Non-Reversibility:** It is impossible to **reverse-engineer** a password from its hash.
-   **Security:** Hashes stored in an operating system or file do not contain the original plain-text password.

### Password Spraying Attacks
Because many systems implement **account lockouts** after several failed login attempts, attackers use **spraying attacks** to avoid detection. In a spraying attack, an attacker tries the most **common passwords** (such as "123456," "password," or "qwerty") against a large number of different accounts. By only trying a few common passwords per account, they can often find weak credentials without triggering lockouts, alarms, or security reports.

### Brute Force Attacks
A **brute force attack** is a more intensive method where an attacker tries every possible iteration of letters, numbers, and special characters until the right password is found. 
-   **Process:** The attacker takes a guess, hashes it, and compares that hash to the one stored in the password file. They repeat this until they find a match.
-   **Time-Consuming:** This process can take a significant amount of time if the passwords are long and the hashing algorithm is strong.

### Online vs. Offline Attacks
-   **Online Attacks:** These occur when an attacker attempts to log in to a live system. They are typically very **slow** because the attacker can only make a few requests a day to avoid locking out the account.
-   **Offline Attacks:** This is the preferred method for most attackers. The attacker **downloads the file** containing hashed passwords and usernames. Once offline, they can use their own **computational resources** to perform as many brute-force attempts as they want without any risk of being locked out. As long as they have enough time and hardware, they can eventually find matches for the stored hashes.


## Indicators of compromise

**Indicators of Compromise (IOCs)** are pieces of evidence that suggest a system has been breached or accessed by an unauthorized party. An IOC describes a situation where there is **high confidence that a compromise has occurred**.

### Network and File Anomalies
-   **Unusual Traffic Patterns:** This includes an **unusually large amount of traffic** on a particular network or an **uptick in traffic from international sites** when the majority of traffic is typically domestic.
-   **File Modifications:** Changes in the **hash values** of files indicate they have been modified. Additionally, files being read much more frequently than normal can be an indicator.
-   **DNS Changes:** If **DNS information** on servers has been modified, it may indicate someone is trying to manipulate where network traffic is directed.

### Authentication and Account Issues
-   **Account Lockouts:** An account being locked due to **too many failed login attempts**—especially if the user did not make those attempts—is a telling indicator. 
-   **Disabled Accounts:** Accounts being **administratively disabled** without a corresponding organizational task may be part of an attacker's plan to impersonate the user and trick a help desk into resetting a password.
-   **Impossible Logins:** This refers to instances where a single user account is logged in from **two different locations simultaneously**. A specific example is a user logging in from Omaha, Nebraska, and then appearing in Australia just minutes later; these geographical anomalies are easily identifiable in authentication logs.

### System and Security Software Interference
-   **Disabled Updates:** Viruses and malware often **disable antivirus updates and security patches** to prevent the vulnerability they used from being closed, allowing them to remain on the system longer.
-   **Restricted Access:** An inability to connect to security websites or download security patches is a strong indicator of compromise.

### Resource Consumption and Unavailability
-   **Unexpected Resource Spikes:** Attackers transferring files or data often create a **spike in traffic**, particularly at unusual times, such as 3:00 in the morning.
-   **Service Disruptions:** A server may become inaccessible because an attacker **caused it to crash** while trying to exploit a vulnerability.
-   **Data Encryption:** If data is suddenly **encrypted and unavailable**, the system may be infected with **ransomware**.

### Log Irregularities
-   **Out-of-Cycle Logging:** This occurs when logs show activity—such as **security patches or applications being installed**—at times when they are not scheduled.
-   **Missing or Deleted Logs:** Attackers often **delete log information** to hide their presence. It's recommended setting up notifications for missing logs to detect this activity.

### Data Exfiltration
-   **Public Exposure of Private Data:** A very clear indicator is when sensitive organizational data **suddenly appears on the internet**. 
-   **Extortion Tactics:** In some ransomware cases, attackers **exfiltrate data before encrypting it**, later threatening to release the private information publicly if a payment is not made. Researchers often have to sift through this publicly leaked data to identify the original owner.

## Segmentation and Access Control

**Network segmentation** and **Access control** methods are used to enhance security and performance.

### Network Segmentation
Network segmentation involves <ins>breaking</ins> a <ins>network</ins> into <ins>smaller pieces</ins> to <ins>limit</ins> the <ins>scope of security events</ins>. It can be implemented in three primary ways:
-   **Physical segmentation:** Physically separating hardware devices.
-   **Logical segmentation:** Using technologies like **VLANs** (Virtual Local Area Networks) on network switches.
-   **Virtual segmentation:** Utilizing virtual machine or cloud-based architectures.

Reasons for segmentation include:
-   **Performance:** Dedicating a single subnet to a high-bandwidth application ensures it runs efficiently without being affected by other network traffic.
-   **Security Strategy:** Creating rules to <ins>prevent direct communication</ins> between users and sensitive resources, such as requiring users to <ins>go through an application server</ins> to reach a database.
-   **Compliance:** Meeting mandates like **PCI DSS** (Payment Card Industry Data Security Standard), which may require credit card information to be kept completely separate from the rest of the network.

### Access Control Lists (ACLs)
An **ACL** is a mechanism used to <ins>allow</ins> or <ins>disallow traffic</ins> through networks, operating systems, or other technologies.
-   **Control Criteria:** Traffic can be controlled based on source/destination IP addresses, port numbers, time of day, or specific user identities.
-   **Granularity:** ACLs allow for very specific rules, such as limiting a user to certain TCP ports on a specific network range.
-   **Operating Systems:** ACLs are also used within OSs to manage permissions for files, folders, and user groups.
-   **Configuration Warning:** When building ACLs, administrators must be careful not to create rules that accidentally lock them out of the system.

### Application Allow Lists and Deny Lists
Organizations use application filtering to ensure only legitimate software runs while blocking malicious software like Trojans and viruses. There are two main philosophies for this:
-   **Allow List:** A restricted approach where **nothing runs** unless it is specifically approved.
-   **Deny List:** A more flexible approach where **everything runs** except for items specifically identified as "bad," such as how antivirus software identifies known viruses.

Windows-specific controls for applications include
-   **Application Hash:** Identifying an app by a unique hash; if the application changes, the hash no longer matches and the rule will not apply.
-   **Digital Signatures:** Allowing apps based on trusted certificates from specific organizations like Microsoft or Google.
-   **Path-based Rules:** Allowing or disallowing applications based on the specific directory or area of the drive they are running from.
-   **Network Zones:** Setting rules that allow certain applications to work only when the device is on a specific network zone, such as a private versus a public network.

## Mitigation Techniques

**Mitigation** is the process of **reducing the impact** of a potential or active security event.

### Patching and Vulnerability Management
-   **Proactive Security:** <ins>Patching</ins> known vulnerabilities is a <ins>primary method</ins> to <ins>stop attacks</ins> before they occur, often making systems more stable in the process.
-   **Deployment Methods:** While home operating systems often **patch automatically**, large organizations usually have IT departments **test patches** for stability before pushing them out to the network. 
-  **Emergency Patches:** Organizations may <ins>deploy</ins> patches <ins>outside</ins> of regular <ins>schedules</ins> if a <ins>significant</ins> vulnerability is being <ins>actively exploited</ins>.

### Encryption
Encryption is used to <ins>limit</ins> the amount of <ins>data</ins> an attacker can <ins>access</ins>.
-   **File-Level Encryption:** This allows for the encryption of specific files or folders, such as **Windows EFS (Encrypting File System)**.
-   **Full Disk Encryption (FDE):** This <ins>protects</ins> the <ins>entire storage</ins> volume, including the OS and user files, which is critical for devices leaving a building. Examples include **BitLocker** for Windows and **FileVault** for Mac OS.
-   **Application-Level Encryption:** Some applications encrypt data internally, independent of the operating system's encryption status.

### Monitoring and Logging
-   **Continuous Identification:** Constant monitoring through <ins>sensors</ins> or built-in technologies in <ins>routers, switches, and firewalls</ins> is necessary to <ins>identify security events</ins>.
-   **Log Consolidation:** Because logs are often spread across many systems, organizations use a **SIEM (Security Information and Event Manager)** to consolidate data into a single source for reporting and monitoring.

### Least Privilege
-   **Access Control:** This best practice limits user rights and permissions strictly to what is required for their specific job role.
-   **Permission Elevation:** Users should ideally not run with administrative permissions; instead, they should **elevate permissions temporarily** only when needed. This limits the scope of a potential data breach or malware infection.

### Posture Assessment
-   **Configuration Enforcement:** Systems connecting to a network undergo a <ins>posture assessment</ins> to ensure they meet <ins>security standards</ins>.
-   **Verification Checks:** These assessments check for the latest OS versions, patches, up-to-date antivirus/EDR signatures, local firewall configurations, and trusted certificates.
-   **Quarantine:** If a system fails the assessment, it may be placed in a **quarantine or private VLAN** until it is brought up to date.

### Decommissioning
-   **Data Removal:** When equipment reaches the <ins>end of</ins> its <ins>life</ins>, <ins>sensitive information must be removed</ins> from storage devices like SSDs and hard drives.
-   **Disposal Options:** While drives can be formatted and recycled for internal use, **physical destruction** is recommended for drives containing sensitive data to ensure it can never be accessed.


## Hardening Techniques

**Hardening techniques** involve implementing best practices to make devices <ins>more resilient</ins> against attacks.

### Operating System and Account Hardening
-   **Security Updates:** One of the most critical steps is <ins>consistently applying security patches and updates</ins> for the operating system and installed applications.
-   **Password Policies:** Systems should enforce rules for **password length and complexity**, such as requiring at least eight characters and a mix of uppercase, lowercase, numbers, and special characters.
-   **Principle of Least Privilege:** User accounts should have <ins>limited access</ins>; not every user should be an administrator, and individuals should only have the specific rights necessary to perform their jobs.
-   **Access Control:** Access can be restricted by limiting it to specific **IP address ranges**, denying anyone outside those ranges.

### Data and Network Security
-   **Encryption:** To protect data, you can use **Encrypting File System (EFS)** for specific files or **Full Disk Encryption (FDE)**—such as Windows BitLocker or macOS FileVault—to secure entire drives.
-   **Communication Security:** Network traffic should be encrypted using **Virtual Private Networks (VPNs)** or application-level encryption like **HTTPS**.
-   **Port Management:** It is vital to **close unnecessary ports** to reduce the attack surface. Tools like **Nmap** can be used to scan for and identify open ports that might have been opened unknowingly by software installations.

### Endpoint Detection and Response (EDR)
Because of the massive scale of new malware variants, the industry has moved toward **EDR** solutions. Unlike traditional antivirus, EDR provides:
-   **Behavioral Analysis:** It <ins>monitors what users and applications do</ins> to <ins>identify malicious activity</ins> even without a known signature.
-   **Machine Learning and Process Monitoring:** These tools rapidly <ins>identify malicious software</ins> and constantly <ins>watch running processes</ins>.
-   **Automated Response:** EDR can perform **root-cause analysis**, <ins>isolate</ins> infected systems, </ins>quarantine</ins> threats, and <ins>roll back to previous configurations autonomously</ins> via **APIs**.

### Host-Based Security Tools
-   **Host-Based Firewalls:** These software-based firewalls run on the OS and can <ins>see data before or after encryption</ins>, allowing them to <ins>block unknown or unusual processes</ins>.
-   **Host-Based IPS (HIPS):** Often built into EDR or anti-malware, HIPS <ins>monitors inbound traffic</ins> for <ins>known vulnerabilities</ins>. It can also protect OS configurations and block actions like **buffer overflows** or unauthorized **registry changes**.

### Device and Application Maintenance
-   **Default Configurations:** You must manually change **default usernames and passwords** on management interfaces for routers, switches, and firewalls, as attackers easily find these defaults.
-   **Multifactor Authentication (MFA):** Implementing MFA or centralized authentication helps synchronize and secure accounts across the network.
-   **Application Hygiene:** To simplify security, you should **delete unused applications**. This removes potential vulnerabilities and the burden of keeping those applications updated.