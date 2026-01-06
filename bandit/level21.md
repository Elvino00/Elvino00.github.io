# Bandit Level 21 → Level 22

## Obiettivo
Sfruttare un cron job configurato in modo non sicuro per ottenere la password dell'utente bandit22, che viene scritta in un file temporaneo accessibile.

## Comandi utilizzati
```bash
ssh bandit21@bandit.labs.overthewire.org -p 2220

# 1. Esaminare la configurazione cron
ls -la /etc/cron.d/
cat /etc/cron.d/cronjob_bandit22

# 2. Analizzare lo script eseguito dal cron
cat /usr/bin/cronjob_bandit22.sh

# 3. Leggere il file temporaneo creato dallo script
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

### Contenuto dello script (/usr/bin/cronjob_bandit22.sh):
```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

## Analisi tecnica

### Cosa ho imparato
- **Cron**: demone per l'esecuzione programmata di comandi (crontab in `/etc/cron.d/`)
- **Vulnerabilità**: scrittura di dati sensibili in file temporanei con permessi larghi (`644` = leggibile da tutti)
- **Analisi di sistema**: tracciare l'esecuzione da cron job allo script ai file creati
- **Principio del minimo privilegio violato**: lo script non dovrebbe esporre la password ad altri utenti

### Flusso dell'attacco
1. **Ricognizione**: esplorare `/etc/cron.d/` per job configurati
2. **Analisi**: leggere script eseguito (`/usr/bin/cronjob_bandit22.sh`)
3. **Sfruttamento**: Identificare file temporaneo (`/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`) e leggerlo
4. **Exfiltration**: ottenere password da file temporaneo

### Tecniche di enumerazione avanzata
```bash
# Cercare tutti i file cron
find /etc -name "*cron*" -type f 2>/dev/null

# Verificare cron job per utente specifico
crontab -u bandit22 -l 2>/dev/null

# Monitorare esecuzioni in tempo reale
tail -f /var/log/syslog | grep CRON
```

### Domande aperte
- Come funziona il sistema cron a livello di architettura?
- Quali altre vulnerabilità comuni affliggono i cron job?
- In penetration test, come enumerare job schedulati in ambienti Windows?
- Come proteggere script cron?
- Quali tecniche di persistence usano gli attacker via cron?

### Note
Questo livello illustra una vulnerabilità reale comune: **esposizione di dati sensibili attraverso percorsi indiretti.**

In scenari reali, i cron job possono esporre dati tramite:

- File temporanei con permessi larghi

- Output in log accessibili

- Email o notifiche non cifrate


Gli script cron dovrebbero:

- Eseguire con privilegi minimi necessari
- Usare file temporanei sicuri (`mktemp`)
- Loggare in modo sicuro
- Validare input e ambiente