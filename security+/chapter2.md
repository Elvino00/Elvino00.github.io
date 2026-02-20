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