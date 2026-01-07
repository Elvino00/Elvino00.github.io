# Bandit Level 27 → Level 28

## Obiettivo
Clonare un repository Git remoto e analizzarne il contenuto per trovare la password per il livello successivo.

## Comandi utilizzati
```bash
# 1. Creare una directory temporanea per il clone
mkdir /tmp/git_repo_27
cd /tmp/git_repo_27

# 2. Clonare il repository Git (password = bandit27 password)
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo

# 3. Entrare nel repository clonato
cd repo

# 4. Esplorare il contenuto
ls -la
cat README
```

## Analisi Tecnica
### Cosa ho imparato
- **Git via SSH**: clonare repository usando SSH con porta non standard (2220)
- **Repository analisi**: esplorare file in repository Git clonati
- **Gestione credenziali**: password per bandit27-git = password per bandit27
- **Isolamento**: lavorare in `/tmp/` per non inquinare la home directory

### Tecniche Git avanzate per analisi
```bash
# Visualizzare la storia dei commit
git log --oneline

# Mostrare tutte le reference (branch, tag)
git show-ref

# Cercare contenuto nella storia del repository
git log --all --grep="password" -i

# Esaminare file eliminati nella storia
git log --diff-filter=D --summary
```

### Comandi di diagnostica

```bash
# Verificare la configurazione remota
git remote -v

# Mostrare l'ultimo commit
git show HEAD

# Elencare tutti i file nel repository (inclusi quelli .git)
find . -type f | grep -v "^./.git/"
```

### Domande aperte
- Come funziona il protocollo Git over SSH a livello di autenticazione?
- Quali vulnerabilità di sicurezza sono comuni in repository Git?
- In penetration test, come cercare repository Git esposti?
- Quali tool automatizzano l'analisi di repository Git per segreti?
- Come proteggere repository Git da accessi non autorizzati?

### Note
Questo livello introduce l'analisi di repository di controllo versione come skill di sicurezza.
In scenari reali, repository Git possono contenere:

- Credenziali hardcoded
- Chiavi private
- Informazioni sensibili in commit storici
- Configurazioni esposte

**Best practice per repository Git sicuri**:

1. Mai commitare credenziali o segreti
2. Usare git-secrets o pre-commit hooks
3. Revisionare la storia prima di push pubblici
4. Implementare scanning automatico
5. Proteggere l'accesso al server Git

**Problemi comuni**: assicurarsi di avere spazio in `/tmp/` e permessi di scrittura.