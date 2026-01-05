# Bandit Level 16 → Level 17

## Obiettivo
Identificare l'unico servizio su una porta tra 31000-32000 che, dopo aver ricevuto la password corrente via SSL/TLS, restituisce una chiave privata SSH per il livello successivo.

## Comandi utilizzati

### 1. Scansione delle porte
```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220

# Scansione per identificare le porte aperte nel range
nc -zv localhost 31000-32000 2>&1 | grep succeeded
```

### 2. Test dei servizi utilizzati
Per ogni porta trovata (es. 31790), testare se parla SSL e se risponde con dati utili:

```bash
# Test connessione SSL e invio password
echo "*password livello 16*" | openssl s_client -connect localhost:31790 -quiet 2>/dev/null
```

### 3. Salvataggio e utilizzo della chiave
L'output del comando sopra contiene la chiave privata:

```text
Correct!
-----BEGIN RSA PRIVATE KEY-----
[chiave privata]
-----END RSA PRIVATE KEY-----
```

Copiare l'intero blocco in un file `bandit17.key` sulla macchina locale:
```bash
# Impostare permessi corretti
chmod 600 bandit17.key

# Connettersi con la chiave
ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
```

## Analisi tecnica

### Cosa ho imparato
- **Scansione porte con** `nc`: `nc -zv` testa la connettività TCP su un range di porte
- **Redirezione errori**: `2<&1` reindirizza stderr su stdout per permettere a `grep` di filtrare
- **Identificazione servizi**: Distinguere tra servizi plaintext (echo) e SSL/TLS
- **Automazione del testing**: Il processo si presta all'automazione con uno script bash

### Script di automazione

```bash
#!/bin/bash
PASSWORD="kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx"

for port in {31000..32000}; do
    echo "Testing port $port..."
    response=$(echo "$PASSWORD" | timeout 2 openssl s_client -connect localhost:$port -quiet 2>/dev/null | head -20)
    
    if echo "$response" | grep -q "BEGIN RSA PRIVATE KEY"; then
        echo "FOUND on port $port"
        echo "$response" > bandit17.key
        chmod 600 bandit17.key
        break
    fi
done
```

### Domande aperte
- Quali tecniche di scanning sono più efficienti di `nc -zv` per range ampi?
- Come funziona il protocollo SSL/TLS a livello di handshake e negoziazione?
- In penetration test, come identificare servizi custom su porte non standard?
- Quali vulnerabilità possono affliggere servizi SSL autofirmati?
- Come differenziare vari tipi di servizi dalle loro "impronte" (banner grabbing)?

### Note
Il livello insegna una metodologia fondamentale di enumeration: scan → identificazione → test → estrazione.
La chiave RSA privata è estremamente sensibile: permessi `600` e cancellazione dopo l'uso.
La password ottenuta non viene riportata per sicurezza.

**Problemi comuni**: Su Windows, assicurarsi che il file della chiave sia salvato con encoding UTF-8 senza BOM e fine riga LF (Unix), non CRLF (Windows).