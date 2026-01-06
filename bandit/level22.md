# Bandit Level 22 → Level 23

## Obiettivo
Sfruttare uno script cron che utilizza un hash MD5 deterministico per prevedere il percorso del file temporaneo contenente la password di bandit23.

## Comandi utilizzati
```bash
ssh bandit22@bandit.labs.overthewire.org -p 2220

# 1. Esaminare la configurazione cron
cat /etc/cron.d/cronjob_bandit23

# 2. Analizzare lo script eseguito
cat /usr/bin/cronjob_bandit23.sh

# 3. Calcolare l'hash per l'utente bandit23
echo "I am user bandit23" | md5sum | cut -d ' ' -f1

# 4. Leggere il file temporaneo corrispondente
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

## Analisi tecnica

### Cosa ha imparato
- **Hash deterministici**: stesso input → stesso output (MD5 in questo caso)
- **Prevedibilità**: nomi file basati su dati prevedibili equivalgono a nomi fissi
- **Analisi statica di script**: comprendere codice senza eseguirlo
- **Calcolo anticipato**: poter determinare il nome del file prima che venga creato

### Script analizzato (/usr/bin/cronjob_bandit23.sh)

```bash
#!/bin/bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

### Vulnerabilità identificata
1. **Input prevedibile**: "*I am user bandit23*" è noto a priori
2. **Algoritmo noto**: MD5sum è standard e facilmente calcolabile
3. **Permessi larghi**: file in `/tmp/` accessibili da altri utenti
4. **Determinismo**: sempre stesso hash per stesso utente

### Spiegazione comando di calcolo
```bash
echo "I am user bandit23" | md5sum | cut -d ' ' -f1
# echo → invia stringa a stdout
# md5sum → calcola hash MD5 (es: 8ca319486bfbbc3663ea0fbe81326349  -)
# cut -d ' ' -f1 → taglia su spazi, prende primo campo (solo hash)
```

### Domande aperte
- Perché MD5 è considerato insicuro per scopi crittografici?
- Quali alternative esistono per generare nomi file non prevedibili?
- In penetration test, come identificare algoritmi hash deboli in applicazioni?
- Come funzionano gli attacchi a dizionario contro hash deterministici?
- Quali sono le best practice per la gestione sicura di file temporanei?

### Note
Questo livello insegna l'importanza della non prevedibilità nella sicurezza.
Hash deterministici basati su input noti sono vulnerabili a:

- Calcolo anticipato
- Enumerazione
- Attacchi a dizionario