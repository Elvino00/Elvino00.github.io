# Bandit Level 6 → Level 7

## Obiettivo
Trovare un file da 33 byte di proprietà dell'utente `bandit7` e del gruppo `bandit6` da qualche parte sul server.

## Comandi utilizzati
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -size 33c -user bandit7 -group bandit6 -type f 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

## Analisi tecnica

### Cosa ho imparato
- Il comando `find` è estremamente potente per ricerche avanzate
- Sintassi : `find [percorso] [espansioni]`
- Criteri combinabili:
    - `-size 33c`: file di esattamente 33 byte (`c` = byte)
    - `user bandit7`: il proprietario è l'utente *bandit7*
    - `group bandit6`: il proprietario è il gruppo *bandit6*
    - `type f`: solo file regolari (non directory, pipe, socket)
- `2>/dev/null`: reindirizza stderr(errori) a /dev/null per un output pulito

### Spiegazione dettagliata
- `find /`: cerca dalla root directory (tutto il filesystem)
- Errori "Permission denied" sono normali quando si cerca in `/` senza privilegi
- `/dev/null` è un device speciale che scarta tutto ciò che vi viene scritto
- L'output è stato: `/var/lib/dpkg/info/bandit7.password`

### Domande aperte
- Quali altri operatori di `find` sono utili in ambito sicurezza?
- Come cercare file modificati di recente?
- Qual è la differenza tra `-exec` e `xargs` con `find`?
- In un assessment reale, quali tipi di file si cercano con criteri simili?
- Come funzionano i permessi Unix a livello di filesystem?

### Note
Ho trovato il comando `find` complesso inizialmente, ma la pratica è essenziale.
La redirezione `2>/dev/null` è cruciale quando si cercano in aree con permessi limitati.