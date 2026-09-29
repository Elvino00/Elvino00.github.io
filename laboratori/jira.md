# Gestione Incident L1/L2 e Tracciamento SLA su Jira Service Management

## Obiettivo
Configurazione e gestione del ciclo di vita di un ticket di tipo **Incident** su Jira Service Management, simulando il supporto a un utente finale in conformità con le buone pratiche ITIL.

## Scenario
- **Utente:** Mario Rossi
- **Problema:** Errore nell'avvio dell'applicazione Microsoft Outlook.
- **Priorità:** Urgenza Alta (blocco dell'invio e-mail a un cliente).

---

## 1. Mappatura Workflow e SLA
- **Tipo di richiesta:** Segnalazione di un Incident.
- **SLA Applicati:** 
  - Time to first response: entro 6 ore.
  - Time to resolution: entro 36 ore.

![1- Dettagli Ticket e SLA](https://res.cloudinary.com/dnhgctqsu/image/upload/v1790679545/Screenshot_2026-09-29_124653_vi5mhh.png)

---

### 2. Diagnosi Iniziale e Prima Nota Interna
- Identificazione del problema di avvio dell'applicazione sul client locale.
- Tracciamento delle prime verifiche tramite nota interna riservata al team IT.

![Prima risposta e note interna](https://res.cloudinary.com/dnhgctqsu/image/upload/v1790679545/Screenshot_2026-09-29_124729_iesyrh.png)

---

## 3. Workaround Operativo e Troubleshooting
- **Continuità di business:** Fornita all'utente l'indicazione per accedere subito a **Outlook Web** da browser.
- **Troubleshooting locale:** Verificato l'eventuale blocco del processo `OUTLOOK.EXE` da Gestione Attività.

![3 - Workaround Outlook Web e verifica processi](https://res.cloudinary.com/dnhgctqsu/image/upload/v1790679545/Screenshot_2026-09-29_124745_zsgcnz.png)

---

## 4. Risoluzione Applicativa
- Guidato l'utente nella procedura di **Ripristino rapido** dell'applicazione tramite `Impostazioni > App > App installate > Opzioni avanzate`.
- Conferma da parte dell'utente del corretto avvio di Outlook.

![4 - Guida al ripristino rapido dell'applicazione](https://res.cloudinary.com/dnhgctqsu/image/upload/v1790679545/Screenshot_2026-09-29_124808_xvvig6.png)

---

## 5. Chiusura del Ticket e Summary
- Documentata la risoluzione tramite nota interna finale e archiviazione del ticket nello stato **Completed** nei tempi previsti dagli SLA.
- **Time to First Response:** 15 min *(Target: 6h)*
- **Time to Resolution:** 2h *(Target: 36h)*

![5 - Chiusura e risoluzione finale](https://res.cloudinary.com/dnhgctqsu/image/upload/v1790679545/Screenshot_2026-09-29_124818_h9qdes.png)