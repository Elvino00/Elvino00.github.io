# Bandit Level 10 → Level 11

## Obiettivo
Decodificare dati Base64 dal file `data.txt` per ottenere la password.

## Comandi utilizzati
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
base64 -d data.txt
```

## Analisi Tecnica 

### Cosa ho imparato
- Base64 è un encoding per rappresentare dati binari come testo ASCII
- Caratteri usati: A-Z, a-z, 0-9. +, /, = (padding)
- `base 64 -d` o `--decode` decodifica dati Base64
- Il comando legge da file se specificato, altrimenti da stdin

### Alternative equivalenti
```bash
# Usare input redirection
base64 -d < data.txt

# Con cat e pipe
cat data.txt | base64 -d

# Decodifica riga per riga (se file multi-riga)
while read line; do echo $line | base64 -d; done < data.txt
```

### Domande Aperte
- Quando si usa Base64 in sicurezza (certificati, auth, dati web)?
- Come riconoscere Base64 vs altri encoding (hex, binary)?
- Quali tool alternativi esistono?
- In incident response, dove si trovano dati Base64 encoded (log, malware, exfil)?

### Note
Base64 è comune in:

- Email attachments (MIME)

- Web (Basic Auth, data URLs)

- Certificati (PEM format)

- Configurazioni con dati binari

La decodifica diretta con `base64 -d` è stata immediata.