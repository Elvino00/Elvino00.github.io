# Bandit Level 13 → Level 14

## Obiettivo
Utilizzare una chiave SSH privata trovata sul server per accedere come utente `bandit14` e leggere la password dal file protetto `/etc/bandit_pass/bandit14`.

## Comandi utilizzati

### 1.Copia della chiave SSH sulla macchina locale
```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

### 2.Impostazione permessi corretti (opzionale ma raccomandata)
```bash
chmod 600 sshkey.private 
```

### 3.Connessione SSH con chiave privata
```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

### 4.Lettura della password
```bash
cat /etc/bandit_pass/bandit14
```

## Analisi Tecnica

### Cosa ha imparato
- `scp` (Secure Copy) per trasferire file via SSH
    - `-P 2220` specifica la porta (nota: `scp` usa `-P`, SSH usa `-p`)
    - Sintassi: `scp [opzioni] sorgente destinazione`
- Connessione SSH con chiave privata: `ssh -i file_chiave`
- Permessi chiavi SSH: `chmod 600` (solo proprietario può leggere/scrivere)
- Limitazione ambientale: OverTheWire blocca connessioni SSH da localhost per conservare risorse

#### Tentativo di connessione da bandit14
```bash
# Questo NON funziona (bloccato dal server):
ssh -i sshkey.private bandit14@localhost -p 2220
```

Errore: "Connecting from localhost is blocked to conserve resources."

#### Workaround necessario
1. Trasferire chiave sulla propria macchina
2. Connettersi dall'esterno (bypassa restrizione)

### Domande aperte
- Come funziona l'autenticazione SSH con chiave RSA/ECDSA?
- Quali sono le best practice per gestire chiavi SSH in ambienti di produzione?
- Come funziona `scp` a livello di protocollo vs `sftp/rsync`?
- In penetration test, dove cercare chiavi SSH esposte (`.ssh/`, backup, log)?
- Cosa fare se una chiave privata è compromessa?

### Note
Le chiavi SSH private sono estremamente sensibili:

- Impostare permessi delle chiavi a `u+rw` o `u+r` (`600` o `400`)

- Mai commitare le chiavi in repository

- Ruotarle regolarmente in ambienti production

- Proteggerle con passphrase quando possibile

La password per il livello 14 è leggibile solo dall'utente bandit14.
Dopo l'uso, eliminare la chiave privata dalla macchina locale per sicurezza.