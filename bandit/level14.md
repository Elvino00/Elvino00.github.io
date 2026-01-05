# Bandit Level 14 → Level 15

## Obiettivo
Inviare la password corrente al servizio in ascolto sulla porta 30000 di localhost e ricevere la password del livello successivo.

## Comandi utilizzati
```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220

# Leggere la password corrente
cat /etc/bandit_pass/bandit14

# Connettersi al servizio e inviare la password
echo "*password omessa presa da bandit14*" | nc localhost 30000
```

## Analisi tecnica

### Cosa ho imparato
- `nc` (netcat) è lo strumento base per interagire con servizi di rete
- Alcuni servizi richiedono input semplice: password + newline (`\n`)
- `echo` automaticamente aggiunge newline alla fine
- Diagnostica servizi:
    1. `nc -zv localhost 30000` → test connettività
    2. `echo "test" | nc localhost 30000` → test interazione plaintext
    3. `openssl s_client -connect localhost:30000` → test SSL/TLS

- Il servizio rispondeva solo a connessioni plaintext via `nc`
- `openssl s_client` si connetteva ma il servizio non rispondeva sullo stream SSL
- `telnet` funzionava ma `nc` è più adatto per scripting

Il formato corretto della password è:
```text
PASSWORD\n
```

Dove `\n` è il carattere newline (aggiunto automaticamente da `echo`).


### Note
Il servizio era un semplice echo server che restituiva la password successiva se riceveva quella corrente.
In scenari reali, servizi simili potrebbero essere:

- API interne
- Servizi di autenticazione
- Daemon custom