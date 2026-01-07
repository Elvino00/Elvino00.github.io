# Bandit Level 28 → Level 29

## Obiettivo
Analizzare la cronologia di un repository Git per trovare una password che è stata aggiunta e poi rimossa in commit successive.

## Comandi utilizzati
```bash
# 1. Clonare il repository
mkdir /tmp/git_repo_28
cd /tmp/git_repo_28
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
cd repo

# 2. Esaminare la cronologia dei commit
git log --oneline --graph

# 3. Confrontare commit per identificare modifiche
# Mostra tutti i commit con dettagli
git log -p

# Oppure: diff tra commit specifici
git diff HEAD~2 HEAD~1
```

## Analisi Tecnica
### Cosa ho imparato
- **Analisi dei log di Git**: `git log --oneline` mostra commit concise, `git log -p` mostra patch
- **Recupero dati storici**: dati rimossi in commit successive rimangono nella cronologia
**Analisi delle differenze (diff)**: `git diff <commit1> <commit2>` rivela cambiamenti tra commit
- **Leak segreti**: informazioni sensibili spesso "nascoste" ma recuperabili dalla storia

### Cronologia commit rilevata
```text
* 375c2cf - (HEAD -> master) fix info leak
* 61435ea - add missing data  
* 04d2b4d - initial commit of README.md
```

### Analisi delle modifiche
```bash
# Diff tra "add missing data" e "initial commit"
git diff 04d2b4d 61435ea
# Rivela aggiunta: +password: *password livello successivo*

# Diff tra "fix info leak" e "add missing data"
git diff 61435ea 375c2cf
# Rivela rimozione: -password: *password*
```

### Domande aperte
- Come funziona l'archiviazione dati di Git a livello di oggetti?
- Quali tecniche esistono per purgare definitivamente dati da repository Git?
- In penetration test, come automatizzare la ricerca di segreti in repository Git?
- Quali sono le implicazioni legali del recupero di dati da cronologia Git?
- Come implementare pre-commit hooks per prevenire leakage di segreti?

### Note
Questo livello dimostra il pericolo dei dati persistenti in sistemi di versioning.
In scenari reali, la cronologia Git ha esposto:

- Credenziali AWS/API keys
- Chiavi SSH private
- Token di autenticazione
- Informazioni di configurazione sensibili

**Best practice per repository sicuri**:

1. Usare `git-secrets` o `pre-commit` hooks per bloccare segreti
2. Scansionare regolarmente la cronologia con tool automatizzati
3. Considerare `git filter-repo` per rimuovere dati sensibili dalla storia
4. Implementare politiche di code review rigorose
5. Limitare accesso ai repository contenenti informazioni sensibili

**Strumenti di sicurezza Git**:

- `trufflehog`: scanner per segreti in repository
- `git-hound`: tool per trovare segreti nella cronologia
- `BFG Repo-Cleaner`: rimuove file di grandi dimensioni o sensibili