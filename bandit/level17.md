# Bandit Level 17 → Level 18

## Obiettivo
Trovare l'unica riga modificata tra due file, `passwords.old` e `passwords.new`, che contiene la password per il livello successivo.

## Comandi utilizzati
```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220
diff passwords.old passwords.new
```

## Analisi tecnica

### Cosa ho imparato
- `diff`: strumento fondamentale per confrontare file riga per riga
- **Sintassi output** `diff`:
    - `42c42`: alla riga 42, il contenuto è stato cambiato (`c` = changed)
    - `<`: riga rimossa dal primo file (`passwords.old`)
    - `>`: riga aggiunta nel secondo file (`passwords.new`)
- **Applicazione reale**: confronto di configurazioni, log, versioni di codice, dump di database

**Output**:
```text
42c42
< *password vecchia*
---
> *password nuova*
```

- La password vecchia (omessa per sicurezza) è la riga che è stata rimossa
- La password nuova è la riga che è stata aggiunta

### Alternative e varianti
```bash
# Mostrare solo le righe diverse (formato compatto)
diff --suppress-common-lines passwords.old passwords.new

# Confronto side-by-side
diff -y passwords.old passwords.new

# Usare altri tool
cmp -l passwords.old passwords.new  # Confronto byte per byte
comm -3 passwords.old passwords.new # Mostra righe uniche per file
```

### Domande aperte
- Come confrontare file binari invece che di testo ?
- In analisi forense, come identificare cambiamenti in file di sistema dopo un incidente?
- Quali strumenti avanzati esistono per il versioning e diff di grandi dataset?
- Come automatizzare il monitoraggio di file critici per cambiamenti non autorizzati?
- Quali sono le implicazioni di sicurezza quando file di password vengono mantenuti in chiaro?


### Note
Il livello insegna l'importanza del **change detection** in sicurezza.
In scenari reali, questo approccio può essere usato per:

- Identificare modifiche a file di configurazione
- Analizzare log per attività sospette
- Confrontare snapshot di filesystem