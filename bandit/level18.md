# Bandit Level 18 → Level 19

## Obiettivo
Leggere il contenuto del file `readme` nella home directory quando il file `.bashrc` è stato modificato per terminare immediatamente la sessione SSH al login.

## Comandi utilizzati

### Soluzione 1: Eseguire comando remoto senza shell interattiva
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat ~/readme"
```

### Soluzione 2: Utilizzare SCP per copiare il file localmente
```bash
scp -P 2220 bandit18@bandit.labs.overthewire.org:readme .
cat readme
```

### Soluzione 3: Usare altri protocolli (se disponibili)
```bash
# Con sftp (se abilitato)
sftp -P 2220 bandit18@bandit.labs.overthewire.org
get readme
exit
```

## Analisi tecnica

### Cosa ho imparato
- `.bashrc` viene eseguito automaticamente all'avvio di una shell interattiva Bash
- **Bypass di restrizioni di login**: eseguire comandi direttamente via SSH evita l'esecuzione di `.bashrc`
- `ssh user@host "command"`: esegue il comando remoto senza avviare shell interattiva
- `scp` può essere usato per estrarre file quando l'accesso shell è bloccato


Funziona perchè quando ci si connette normalmente si ha questo flusso qui:
```text
ssh → avvia shell → esegue .bashrc → logout
```

Se si passa un comando direttamente:
```text
ssh "cat readme" → esegue comando → ritorna output → termina (senza shell)
```

### Tecniche di bypass alternative
```bash
# Usare un'altra shell (se disponibile)
ssh bandit18@bandit.labs.overthewire.org -p 2220 "/bin/sh"

# Disabilitare l'esecuzione di .bashrc
ssh bandit18@bandit.labs.overthewire.org -p 2220 "bash --norc"

# Usare un comando non-interattivo
ssh bandit18@bandit.labs.overthewire.org -p 2220 "tail -1 ~/readme"
```

### Domande aperte
- Quali altri file di inizializzazione shell esistono?
- In penetration test, come bypassare restrizioni shell in ambienti controllati?
- Come diagnosticare problemi di login SSH?
- Quali tecniche di "shell restriction bypass" sono comuni in CTF/sfide reali?
- Come proteggere un server da accessi non autorizzati quando `.bashrc` è compromesso?

### Note
Il livello insegna l'importanza di comprendere il **flusso di autenticazione SSH** e l'**inizializzazione della shell**.
In scenari reali, questa tecnica può essere utile per:

- Estrarre file da server con shell ristrette
- Eseguire comandi su server con problemi di configurazione
- Automatizzare attività remote senza shell interattiva

**Problemi comuni**: Assicurarsi che il comando remoto sia tra virgolette e che i percorsi dei file siano corretti.