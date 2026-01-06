# Bandit Level 19 → Level 20

## Obiettivo
Utilizzare un binario con setuid bit attivo per leggere la password di bandit20 dal file protetto `/etc/bandit_pass/bandit20`.

## Comandi utilizzati
```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220

# 1. Esaminare il file con privilegi speciali
ls -la
# Output: -rwsr-x--- 1 bandit20 bandit19 14876 Oct 14 09:46 bandit20-do

# 2. Eseguire il binario senza argomenti per vedere il suo utilizzo
./bandit20-do
# Output: Run a command as another user. Example: ./bandit20-do id

# 3. Usare il binario per leggere il file di password protetto
./bandit20-do cat /etc/bandit_pass/bandit20
```

## Analisi Tecnica

### Cosa ho imparato
- **Setuid bit**: permesso speciale (`s` al posto di `x` per il proprietario) che fa eseguire un programma con i privilegi del proprietario del file, non dell'utente che lo esegue
- **Identificazione**: `ls -la` mostra `-rwsr-x---` (la `s` nella tripletta del proprietario indica setuid)
- **Sfruttamento**: il binario `bandit20-do` viene eseguito come utente `bandit20`, permettendo di accedere ai file di quell'utente
- **Controllo di sicurezza**: binari setuid mal implementati sono un vettore di attacco comune


```text
Permessi: -rwsr-x---
│        ││││││││└── Altri: nessun permesso
│        │││││││└── Gruppo: esecuzione (x)
│        ││││││└── Gruppo: lettura (r)
│        │││││└── Proprietario: setuid bit (s invece di x)
│        ││││└── Proprietario: esecuzione (implicito)
│        │││└── Proprietario: scrittura (non presente)
│        ││└── Proprietario: lettura (r)
│        └── Tipo: file regolare (-)
└── Non rilevante
```

### Comandi di verifica
```bash
# Verificare i permessi in dettaglio
stat bandit20-do

# Verificare come UID effettivo
./bandit20-do id
# Output: uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
# euid=11020 indica l'UID effettivo è bandit20
```

### Domande aperte
- Qual è la differenza tra UID reale (real) e UID effettivo (effective) in Unix?
- Come funziona esattamente il meccanismo setuid a livello di kernel?
- Quali sono le best practice per scrivere programmi setuid sicuri?
- In un penetration test, come cercare binari setuid potenzialmente sfruttabili?
- Quali vulnerabilità comuni affliggono i binari setuid?

### Note
I binari setuid sono un meccanismo potente ma pericoloso. In ambienti reali:

- Devono essere minimi e ben auditati (ben rivisti)
- Spesso sostituiti da meccanismi più sicuri (capabilities, sudo)
- Frequente obiettivo di attacchi privilege escalation


**Importante**: Mai copiare o modificare binari setuid senza comprendere appieno le implicazioni di sicurezza.