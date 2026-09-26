## Laboratorio: Gestione Identità (IAM) e MFA su Okta Platform

**Obiettivo:** 
Configurare un tenant Okta Developer per simulare l'onboarding di un utente aziendale, applicare una politica di autenticazione a due fattori (MFA) obbligatoria tramite Okta Verify e verificare la tracciabilità nei log di sicurezza.

### Descrizione tecnica
Ho configurato un ambiente di Identity & Access Management (IAM) con:

- **Tenant Okta Workforce Identity Cloud** (ambiente sandbox/developer).

- **Utente di test** creato all'interno della Universal Directory con email e credenziali dedicate.

- **Okta Verify** abilitato come Authenticator principale per il secondo fattore di autenticazione.

- **Authentication Policy** applicata per forzare la combinazione `Password + Another Factor` all'accesso.

Ho testato l'intero ciclo di vita dell'utente: dal primo onboarding con attivazione MFA tramite QR Code, fino al login operativo intercettato dalla richiesta di notifica Push su smartphone.




### Spiegazione teorica
- **IAM e Approccio Zero Trust**: L'autenticazione basata solo sulla password è vulnerabile ad attacchi di phishing e credential stuffing; l'MFA introduce un fattore di possesso (smartphone - *something you have*) combinato al fattore di conoscenza (password - *something you know*).

- **Enrollment Policy** vs **Authentication Policy**:

    - *Enrollment Policy*: Stabilisce quali fattori un utente è tenuto a registrare durante l'onboarding (es. l'associazione obbligatoria di Okta Verify).

    - *Authentication Policy*: Regola quando e con quali condizioni (IP, dispositivo, gruppo di appartenenza) tali fattori debbano essere richiesti durante il login.

- **Notifiche Push vs SMS/TOTP**: L'uso di Okta Verify tramite notifiche push garantisce maggiore sicurezza rispetto agli SMS e migliora l'esperienza utente rispetto all'inserimento manuale di codici temporanei (TOTP).




### Applicazione pratica
**1. Onboarding dell'Utente in Universal Directory**

Dalla console di amministrazione Okta (*Directory* > *People* > *Add Person*):

``` text
First Name: Mario
Last Name: Rossi
Username / Primary Email: mrosst.test@domain.local
User Status: Set by admin / Password da impostare al primo accesso 
```

**2. Configurazione e Abilitazione di Okta Verify**
Attivazione del fattore nella sezione *Security* > *Authenticators*:

``` text
1. Selezionare "Okta Verify" tra i fattori disponibili e fare clic su "Enable".
2. In "Authenticators Enrollment", aggiungere una regola al gruppo di test:
   - Eligible Authenticators: Okta Verify (Required)
   - Setup: Required upon first sign-in
```

**3. Configurazione della Authentication Policy**
Creazione di una regola di accesso personalizzata in *Security* > *Authentication Policies*:

``` text
Rule Name: Enforce-MFA-TestGroup
User Group: Test-Users-Group
Access: Allowed AND User Must Authenticate With: Password + Another factor
Possession Factor Constraints: Okta Verify (Push notification / TOTP)
``` 

**4. Test del Flusso di Login ed Enrollment**

- **Fase 1 (Primo Accesso)**: Navigazione sul portale Okta dall'utente di test. Inserimento della password temporanea e richiesta automatica di cambio password.

- **Fase 2 (Enrollment MFA)**: Comparsa del QR Code a schermo. Scansione del codice tramite l'app Okta Verify installata su smartphone e associazione riuscita del dispositivo.

- **Fase 3 (Verifica MFA)**: Disconnessione e nuovo tentativo di accesso. *Inserimento password* -> *Blocco temporaneo della sessione* -> *Notifica Push inviata allo smartphone* -> *Approvazione del login* -> *Accesso concesso alla dashboard*.

**5. Ispezione dei Log di Audit (System Log)**
Verifica dell'evento di sicurezza dalla sezione *Reports* > *System Log*:

``` text
EventType: user.authentication.auth_via_mfa
Outcome: SUCCESS
Authenticator: OKTA_VERIFY_PUSH
Client IP: 151.x.x.x
```

### Considerazioni sulla sicurezza
- **Riduzione del rischio:** L'implementazione dell'MFA azzera i rischi legati a password deboli o compromesse (phishing, credential stuffing).
- **Tracciabilità:** La consultazione del System Log permette all'IT Helpdesk di verificare in tempo reale i tentativi di accesso falliti e diagnosticare i problemi degli utenti.


