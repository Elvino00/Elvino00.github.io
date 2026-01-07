# Bandit Level 31 → Level 32

## Obiettivo
Superare un Git pre-receive hook che valida il contenuto di un file specifico (`key.txt`) prima di accettare un push.

## Comandi utilizzati
```bash
# 1. Clonare il repository
mkdir /tmp/git_repo_31
cd /tmp/git_repo_31
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
cd repo

# 2. Creare il file con contenuto esatto (senza newline finale)
printf "May I come in?" > key.txt

# 3. Forzare l'aggiunta nonostante .gitignore
git add -f key.txt

# 4. Committare
git commit -m "Added key.txt as requested"

# 5. Pushare (il pre-receive hook risponderà)
git push origin master
```

## Analisi tecnica

### Cosa ho imparato
- **Git hooks**: script eseguiti automaticamente su eventi Git (pre-receive, post-receive, pre-commit)
- **Pre-receive hook**: eseguito sul server PRIMA di accettare push, può rifiutare cambiamenti
- **Bypass .gitignore**: `git add -f` forza l'aggiunta di file ignorati
- **Formato file critico**: encoding, line endings, trailing newline possono far fallire validazione

### Problemi comuni e soluzioni
```bash
# Windows line endings (CRLF) vs Unix (LF)
# Errato: echo "May I come in?" > key.txt  (aggiunge newline)
# Corretto: printf "May I come in?" > key.txt

# Verificare contenuto esatto
hexdump -C key.txt
# Output corretto: 4d 61 79 20 49 20 63 6f 6d 65 20 69 6e 3f
# (nessun 0a finale = nessun newline)

# Verificare encoding
file key.txt
# Deve essere: ASCII text
```

### Tecniche debug hooks
```bash
# Verificare hook lato client (se presenti)
ls -la .git/hooks/

# Test locale (se hook client-side)
.git/hooks/pre-commit  # se esiste

# Forzare push con verbose output
GIT_TRACE=1 git push origin master

# Alternative se printf non disponibile
python3 -c 'with open("key.txt", "w") as f: f.write("May I come in?")'
```

### Domande aperte
- Come funzionano i Git hooks a livello di architettura client/server?
- Quali vulnerabilità di sicurezza possono introdurre gli hooks?
- In penetration test, come identificare e analizzare hooks in repository?
- Come proteggere server Git da hooks malevoli?
- Quali alternative esistono per validazione centralizzata?

### Note
Questo livello introduce i Git hooks come meccanismo di validazione server-side.
In scenari reali, i pre-receive hook sono usati per:

- Validare formato commit messages
- Eseguire test automatici
- Verificare permessi
- Scansionare per segreti/sicurezza

**Best practice per Git hooks**:

1. Mantenere hooks minimali e ben auditati
2. Implementare timeout per prevenire DoS
3. Loggare tutte le esecuzioni
4. Testare hooks in ambienti di staging
5. Considerare alternative più sicure (CI/CD pipelines)

**Sicurezza degli hooks**:

- Hooks eseguiti con privilegi dell'utente Git
- Possono essere usati per persistence in compromissioni
- Possono esfiltrare dati durante push/pull
- Devono essere revisionati come codice normale