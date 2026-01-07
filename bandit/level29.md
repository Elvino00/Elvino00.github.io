# Bandit Level 29 → Level 30

## Obiettivo
Analizzare branch multipli in un repository Git per trovare la password nascosta in un branch di sviluppo.

## Comandi utilizzati
```bash
# 1. Clonare il repository
mkdir /tmp/git_repo_29
cd /tmp/git_repo_29
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo

# 2. Esaminare tutti i branch (locali e remoti)
git branch -a

# 3. Esaminare la cronologia del branch dev
git log remotes/origin/dev --oneline

# 4. Confrontare commit specifici nel branch dev
git diff a3b6378 e50e6cc
```

## Analisi tecnica

### Cosa ho imparato

- **Enumerazione dei branch**: `git branch -a` mostra tutti i branch (locali e remoti)
- **Analisi Multi-branch**: password spesso nascoste in branch di sviluppo/test
- **Ispezione branch remoti**: analizzare branch remoti senza checkout
- **Targeted diff**: confrontare commit specifici per trovare modifiche rilevanti

### Struttura repository
```text
Branch rilevanti:
* master                    (clean, no passwords)
  remotes/origin/dev        (contains password in commit e50e6cc)
  remotes/origin/sploits-dev
```

### Analisi diff
```bash
# Output di git diff a3b6378 e50e6cc:
@@ -4,5 +4,5 @@ Some notes for bandit30 of bandit.
 ## credentials

 - username: bandit30
-- password: <no passwords in production!>
+- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

### Tecniche avanzate di esplorazione branch
```bash
# Mostrare tutti i branch con ultimo commit
git branch -a -v

# Esaminare file specifici in branch remoti
git show remotes/origin/dev:README.md

# Confrontare branch tra di loro
git diff master..remotes/origin/dev

# Checkout del branch dev per esplorazione completa
git checkout -b dev remotes/origin/dev

# Cercare pattern in tutti i branch
for branch in $(git branch -a | grep -v HEAD); do
    echo "=== $branch ==="
    git grep -n "password" $branch 2>/dev/null || true
done
```

### Domande aperte
- Qual è la differenza tra branch locali, remoti e di tracking?
- Come funziona il merging tra branch in Git e quali conflitti di sicurezza può introdurre?
- In penetration test, come automatizzare l'analisi di tutti i branch in un repository?
- Quali sono le best practice per la gestione sicura dei branch?
- Come identificare branch abbandonati o legacy che potrebbero contenere segreti?

### Note
Questo livello dimostra l'importanza di analizzare l'intero albero dei branch in sicurezza.
In scenari reali, i branch possono contenere:

- Credenziali in branch di sviluppo/test
- Configurazioni sensibili non ancora rimosse
- Codice sperimentale con vulnerabilità
- Backdoor o codice malizioso



**Best practice per gestione branch sicura**:

1. Proteggere branch main/master da push diretti
2. Richiedere code review per tutti i merge
3. Scansionare automaticamente tutti i branch per segreti
4. Pulire regolarmente branch obsoleti
5. Implementare politiche di retention per branch di sviluppo

**Pattern comuni di leakage**:

- Credenziali in branch `dev`, `staging`, `test`
- File di configurazione `.env` in branch temporanei
- Chiavi API in commit di feature branch
- Dati di test con informazioni reali