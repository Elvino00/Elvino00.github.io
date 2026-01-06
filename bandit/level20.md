# Bandit Level 20 → Level 21

## Obiettivo
Utilizzare un binario setuid (`suconnect`) che si connette a una porta locale specificata, verifica la password ricevuta e, se corretta, invia la password del livello successivo.

## Comandi utilizzati

### Soluzione 1: Usando job control in una singola sessione
```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220

# 1. Avviare un server netcat in ascolto che invii la password
echo "*password livello corrente*" | nc -l -p 55555 -q 1

# 2. Sospendere netcat con Ctrl+Z, poi farlo ripartire in background
# [Premi Ctrl+Z]
bg

# 3. Eseguire il binario setuid sulla stessa porta
./suconnect 55555
```

### Soluzione 2: Usando due terminali o tmux/screen
```bash
# Terminale 1: Server netcat
echo "*password livello corrente*" | nc -l -p 55555 -q 1

# Terminale 2: Client suconnect
./suconnect 55555
```

### Soluzione 3: Con script automatizzato
```bash
#!/bin/bash
# In una sessione singola
(echo "*password livello corrente*"; sleep 1) | nc -l -p 55555 &
./suconnect 55555
```

## Analisi Tecnica

### Cosa ho imparato
- `nc -l -p PORT`: netcat in modalità server (listen) su porta specifica

- **Job control**: `Ctrl+Z` sospende processo foreground, `bg` lo riavvia in background

- **Comunicazione inter-processo via socket**: due processi comunicano via TCP su localhost

- `-q 1`: opzione netcat che chiude la connessione 1 secondo dopo EOF (se supportata)

### Spiegazione del flusso

1. Netcat si mette in ascolto su porta 55555
2. Suconnect si connette a localhost:55555  
3. Netcat invia la password di bandit20
4. Suconnect verifica la password
5. Se corretta, suconnect invia la password di bandit21
6. Netcat riceve e stampa la password


### Domande aperte
- Qual è la differenza tra socket TCP e UDP per comunicazioni locali?
- Come funziona il job control a livello di shell e di kernel?
- In penetration test, come sfruttare servizi che richiedono autenticazione via socket?
- Quali vulnerabilità possono affliggere applicazioni che si connettono a servizi locali?
- Come debuggare problemi di connettività tra processi?

### Note
Il livello insegna concetti importanti di comunicazione inter-processo e automazione in ambiente ristretto.
In scenari reali, tecniche simili possono essere usate per:

- Testare client/server applicativi
- Automatizzare interazioni con servizi di rete
- Debugare problemi di connettività

**Problemi comuni**: Assicurarsi che la porta scelta non sia già in uso e che netcat sia effettivamente in ascolto prima di eseguire suconnect.