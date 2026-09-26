# Windows Server 2025 & Active Directory Domain Services (AD DS) Security Lab

## Panoramica del Laboratorio
Questo laboratorio documenta la configurazione da zero di un ambiente enterprise basato su **Windows Server 2025** e **Windows 11 Client**. L'obiettivo è configurare Active Directory Domain Services (AD DS), definire politiche di sicurezza tramite Group Policy Objects (GPO), gestire le autorizzazioni di archiviazione NTFS/Share e implementare restrizioni avanzate sugli accessi.

---

## Modulo 1: Configurazione della Macchina Virtuale e Rete
Un'infrastruttura Active Directory richiede un indirizzo IP statico e una risoluzione DNS coerente prima di promuovere il server a Domain Controller.

### 1. Configurazione della VM Server (VirtualBox)
- **OS Target:** Windows Server 2025 Standard
- **Scheda di rete iniziale:** Bridged Adapter (per ottenere l'accesso a Internet dal router e completare le prime configurazioni).

### 2. Riservatezza DHCP e IP Statico
1. Recuperare l'indirizzo MAC e l'IP corrente del server con il comando:
   ```cmd
   ipconfig /all
   ```

2. Accedere al pannello del router ed eseguire una prenotazione DHCP (*DHCP Reservation*) associando il MAC address all'IP scelto (es. `192.168.1.27`).
3. Configurare la scheda di rete sul server (**Control Panel > Network and Sharing Center > Ethernet Properties > IPv4**):
- **IP Address:** `192.168.1.27`
- **Subnet Mask:** `255.255.255.0`
- **Default Gateway:** `192.168.1.1` (IP del router)
- **Preferred DNS:** `192.168.1.1` (temporaneo per il primo test di rete)


4. Verificare la connettività di rete:
```cmd
ping google.com
```



---

## Modulo 2: Installazione AD DS e Promozione a Domain Controller

### Concetti chiave

- **Domain Controller (DC):** Il server che esegue il ruolo AD DS e gestisce l'autenticazione (Kerberos/NTLM), l'autorizzazione e il database centrale.
- **Active Directory (AD):** Servizio di directory gerarchico per la gestione centralizzata di utenti, computer e risorse di rete.

### 1. Installazione del Ruolo AD DS

1. Aprire **Server Manager** > **Manage** > **Add Roles and Features**.
2. Selezionare **Role-based or feature-based installation**.
3. Scegliere il server locale dal Server Pool.
4. Spuntare **Active Directory Domain Services** e confermare l'inclusione degli strumenti di gestione (**RSAT**).
5. Proseguire e cliccare su **Install**.

### 2. Promozione a Domain Controller

1. Cliccare sull'icona della bandiera (Avvisi) in alto a destra su Server Manager > **Promote this server to a domain controller**.
2. **Deployment Configuration:** Selezionare *Add a new forest* e inserire il nome del dominio radice (es. `firstdomain.com`).
3. **Domain Controller Options:**
    - **Forest & Domain Functional Level:** Windows Server 2025.
    - Spuntare **Domain Name System (DNS) server** e **Global Catalog (GC)**.
    - Impostare la password per la *Directory Services Restore Mode (DSRM)*.


4. **DNS Options:** Ignorare l'avviso di delega DNS (normale per la prima foresta radice).
5. **Additional Options & Paths:** Verificare il nome NetBIOS e lasciare invariati i percorsi di default (`NTDS` e `SYSVOL`).
6. Completare il check dei prerequisiti e cliccare su **Install**. Il server si riavvierà automaticamente.

### 3. Verifica del Servizio e DNS Resolution

Dopo il riavvio, accedere come `FIRSTDOMAIN\Administrator` e verificare il corretto funzionamento del DNS tramite CMD:

```cmd
nslookup firstdomain.com
```

*Output atteso:* Risoluzione corretta dell'indirizzo IP locale del Domain Controller.

---

## Modulo 3: Gestione delle Organizational Units (OU) e dei Gruppi

### Concetti

- **Organizational Unit (OU):** Contenitori logici usati per applicare GPO e delegare permessi amministrativi.
- **Security Groups:** Gruppi utilizzati per l'assegnazione di permessi su risorse condivise.

### Ambiti dei Gruppi (Group Scopes)

| Scope | Membri ammessi | Ambito Permessi | Utilizzo Principale |
| --- | --- | --- | --- |
| **Domain Local** | Ogni dominio | Solo stesso dominio | Accesso alle risorse locali |
| **Global** | Solo stesso dominio | Ogni dominio | Raggruppamento utenti/ruoli |
| **Universal** | Ogni dominio | Ogni dominio | Accesso multi-dominio / Foresta |

### Procedura di Creazione OU e Gruppi

1. Aprire **Server Manager** > **Tools** > **Active Directory Users and Computers (ADUC)**.
2. Fai clic con il tasto destro sul dominio radice (`firstdomain.com`) > **New** > **Organizational Unit**.
3. Inserire il nome (es. `Employees`) e assicurarsi che sia spuntata l'opzione *Protect container from accidental deletion*.
4. All'interno della nuova OU, fare clic con il tasto destro > **New** > **Group**:
    - Nome: `IT Department` / `Sales Department`
    - Group Scope: **Global**
    - Group Type: **Security**



---

## Modulo 4: Rete Interna e Join del Client al Dominio

Per simulare una rete aziendale isolata, il server e le macchine client devono comunicare su una rete privata dedicata.

### 1. Configurazione Rete Interna (VirtualBox)

- **Server & Client VirtualBox Settings:**
- Network Adapter: **Internal Network**
- Name: `intnet` (identico su tutte le VM)
- Promiscuous Mode: **Allow VMs**



### 2. Configurazione IP del Client (Windows 11)

1. Aprire **Control Panel > Network and Sharing Center > Ethernet Properties > IPv4**.
2. Impostare un IP statico sulla stessa subnet (es. `192.168.1.29`).
3. **Preferred DNS Server:** Impostare rigorosamente l'IP del Domain Controller (`192.168.1.28`).

### 3. Procedura di Join al Dominio

1. Sulla macchina client, andare in **Settings > System > About > Advanced system settings**.
2. Nella scheda **Computer Name**, cliccare su **Change...**.
3. Selezionare **Domain** e digitare `firstdomain.com`.
4. Inserire le credenziali dell'amministratore del dominio (`FIRSTDOMAIN\Administrator`).
5. Alla comparsa del messaggio *"Welcome to the firstdomain.com domain"*, riavviare il PC.

---

## Modulo 5: Hardening e Configurazione Group Policy (GPO)

Le politiche di gruppo consentono di applicare configurazioni di sicurezza centralizzate.

### Struttura GPO

- **Computer Configuration:** Sostituisce le impostazioni locali della macchina indipendentemente dall'utente connesso.
- **User Configuration:** Si applica ai profili utente al momento del login.
- **Policies vs Preferences:** Le *Policies* sono vincolanti e non modificabili dall'utente; le *Preferences* impostano configurazioni di default personalizzabili.

---

### Attività di Hardening Implementate

#### 1. Rinforzare Password Policy

- **Percorso GPO:** `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy`
- **Configurazioni:**
- *Minimum password length:* **12 caratteri**
- *Password must meet complexity requirements:* **Enabled**



#### 2. Account Lockout Policy (Protezione Brute Force)

- **Percorso GPO:** `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy`
- **Configurazioni:**
    - *Account lockout threshold:* **3 tentativi falliti**
    - *Account lockout duration:* **15 minuti**



#### 3. Restrizione Accesso al Pannello di Controllo

- **Percorso GPO:** `User Configuration > Policies > Administrative Templates > Control Panel`
- **Impostazione:** *Prohibit access to Control Panel and PC settings* -> **Enabled**

#### 4. Disabilitazione Dispositivi di Archiviazione USB

- **Percorso GPO:** `Computer Configuration > Policies > Administrative Templates > System > Removable Storage Access`
- **Impostazione:** *All Removable Storage classes: Deny all access* -> **Enabled**

#### 5. Configurazione Desktop Wallpaper

- **Percorso GPO:** `User Configuration > Policies > Administrative Templates > Desktop > Desktop > Desktop Wallpaper`
- **Impostazione:** Inserire il percorso della risorsa e selezionare lo stile di visualizzazione.

#### 6. User Rights Assignment (Restrizione Log on Locally e RDP)

- **Percorso GPO:** `Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment`
- **Blocco Login Locale:** Modificare *Deny log on locally* aggiungendo i gruppi di utenti non autorizzati (es. utenti interinali o HR).
- **Controllo Accesso Remote Desktop:** Modificare *Allow log on through Remote Desktop Services* includendo solo i gruppi autorizzati (es. `IT Department`).

---

### Applicazione Forzata delle Politiche

Per applicare immediatamente le GPO modificate senza attendere il ciclo di refresh automatico, eseguire sul client:

```cmd
gpupdate /force
```

---

## Modulo 6: Storage Management (NTFS vs Share Permissions & FSRM)

### Differenza tra Permessi NTFS e Share

- **Share Permissions:** Controllano l'accesso a livello di rete.
- **NTFS Permissions:** Controllano l'accesso a livello di file system locale e di rete.
- **Regola di applicazione:** Quando combinati, prevale sempre il permesso **più restrittivo**.

---

### Scenari di Configurazione Permessi

#### Scenario A: Marketing Intern (Solo Lettura)

- **Condizione:** L'intern deve poter visualizzare la cartella condivisa ma non modificare/eliminare file.
- **Share Permissions:** Gruppo `Marketing_Staff` -> **Read (Allow)**
- **NTFS Permissions:** Gruppo `Marketing_Intern` -> **Read & Execute (Allow)**

#### Scenario B: Cartella Riservata HR

- **Condizione:** Solo il personale HR deve poter accedere alla cartella.
- **Share Permissions:** Rimuovere `Everyone`. Aggiungere gruppo `HR_Group` -> **Full Control (Allow)**
- **NTFS Permissions:** Gruppo `HR_Group` -> **Full Control (Allow)**

#### Scenario C: Vendor Esterno (Solo Upload)

- **Condizione:** Un fornitore deve poter caricare report senza vedere o modificare i file caricati da altri.
- **Share Permissions:** Gruppo `Vendors` -> **Full Control (Allow)**
- **NTFS Permissions:** Gruppo `Vendors` -> **Write (Allow)** (deselezionare Read/List folder contents).

---

### Mappatura Automatica Drive di Rete tramite GPO

1. In **Group Policy Management Console**, creare una GPO legata al dominio/OU.
2. Navigare in `User Configuration > Preferences > Windows Settings > Drive Maps`.
3. Tasto destro > **New > Mapped Drive**:
- **Action:** Update
- **Location:** `\\<HOSTNAME_SERVER>\<NOME_CARTELLA>` (es. `\\WIN-8RTLLRN31B8\Shared`)
- **Drive Letter:** Usare una lettera specifica (es. `E:`).



---

### Gestione Archiviazione tramite FSRM (File Server Resource Manager)

1. In **Server Manager**, installare il ruolo *File Server Resource Manager* da **File and Storage Services > File and iSCSI Services**.
2. **Quota Management:**
- Aprire **FSRM > Quota Management > Quotas > Create Quota**.
- Impostare un limite rigido (*Hard Quota*) di **10 GB** sulla cartella `C:\Shared` con soglie di notifica via avviso di sistema.


3. **File Screening Management:**
- Creare una regola di blocco (*File Screen*) per impedire l'upload di specifiche estensioni (es. bloccare file multimediali `.exe`, `.mp3` o `.mp4` nelle cartelle condivise).



---

## Modulo 7: Configurazione Avanzata di Sicurezza

### Fine-Grained Password Policies (FGPP)

Consente di applicare politiche password differenti a gruppi di utenti specifici senza dover creare domini separati.

1. Aprire **Active Directory Administrative Center (ADAC)**.
2. Selezionare il dominio > **System > Password Settings Container**.
3. Tasto destro > **New > Password Settings**:
    - **Name:** `Admin_Password_Policy`
    - **Precedence:** `1` (valore più basso indica priorità massima).
    - Impostare parametri restrittivi (es. lunghezza minima 16 caratteri).
    - In **Directly Applies To**, aggiungere il gruppo di destinazione (es. `IT-USA`).



---

### Account di Servizio e Configurazione Kiosk Mode

#### 1. Creazione Service Account

- I **Service Account** vengono utilizzati da servizi di sistema o applicazioni automatiche.
- Convenzione di naming: iniziare il nome utente con un prefisso identificativo (es. `$svc-kiosk`).
- **Opzioni Account:** Deselezionare *User must change password at next logon*, spuntare **User cannot change password** e **Password never expires**.

#### 2. Kiosk Mode con Autologon (Sysinternals)

1. Scaricare **Sysinternals Suite** ed eseguire l'utility `Autologon.exe`.
2. Inserire le credenziali del Service Account e il dominio per abilitare l'accesso automatico all'avvio.
3. Configurare l'applicazione target (es. Browser):
    - Modificare il collegamento dell'applicazione inserendo il parametro `-start-Fullscreen` o `--kiosk`.
4. Aggiungere il collegamento alla cartella di avvio automatico di Windows:
```cmd
shell:startup
```

5. Configurare la GPO per bloccare il login locale a tutti gli utenti standard su quel PC, lasciando attivo solo l'accesso del Service Account pre-configurato.





