# Bandit Level 15 → Level 16

## Obiettivo
Inviare la password corrente al servizio SSL/TLS in ascolto sulla porta 30001 di localhost.

## Comandi utilizzati
```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220

# Leggere la password corrente
cat /etc/bandit_pass/bandit15

# Connettersi via SSL e inviare la password
echo "*password livello 15*" | openssl s_client -connect localhost:30001 -quiet
```

## Analisi tecnica

### Cosa ho imparato
- `openssl s_client` è lo strumento per interagire con servizi SSL/TLS
- `-connect host:port` specifica l'endpoint
- `-quiet` riduce l'output verbose 
- Il servizio usa un certificato autofirmato "SnakeOil Ltd."
- Il messaggio "read R BLOCK" indica che OpenSSL attende input

### Errori comuni e soluzioni

- "RENEGOTIATING": attesa normale durante handshake

- "KEYUPDATE": parte del protocollo TLS 1.3

- "DONE": connessione stabilita, pronto per input

- "Verify return code: 18 (self-signed certificate)": ignorabile per testing

### Alternative
```bash
# Senza -quiet per debugging
openssl s_client -connect localhost:30001

# Con timeout
echo "password" | timeout 5 openssl s_client -connect localhost:30001

# Usare ncat (se disponibile)
echo "password" | ncat --ssl localhost 30001
```

### Domande Aperte
- Come funziona l'handshake SSL/TLS a livello di protocollo?
- Quali vulnerabilità sono comuni in implementazioni SSL/TLS?
- In penetration test, come testare la sicurezza di servizi SSL?
- Quali tool automatizzano l'analisi SSL ?
- Come intercettare traffico SSL/TLS per debugging?

### Note
Il servizio accetta input plaintext sul canale cifrato.
In scenari reali, servizi SSL/TLS potrebbero richiedere:

- Client certificate authentication
- Specific cipher suites
- SNI (Server Name Indication)