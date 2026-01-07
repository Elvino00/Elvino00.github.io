# Bandit Level 30 → Level 31

## Obiettivo
Analizzare i tag di un repository Git per trovare la password nascosta in un tag specifico.

## Comandi utilizzati
```bash
# 1. Clonare il repository
mkdir /tmp/git_repo_30
cd /tmp/git_repo_30
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
cd repo

# 2. Elencare tutti i tag disponibili
git tag

# 3. Esaminare il contenuto del tag "secret"
git show secret
```

## Analisi tecnica

### Cosa ho imparato
- **Git tags**: riferimenti statici a commit specifici (spesso usati per release)
- **Tag exploration**: spesso contengono dati nascosti o versioni specifiche
- **Git show per tag**: `git show <tagname>` rivela contenuto del tag
- **Completezza repository**: analisi completa include branch, commit history E tags

### Output del comando critico
```bash
$ git show secret
# Output: *password livello successivo omessa*
```

### Tecniche avanzate di analisi tag
```bash
# Mostrare tutti i tag con commit associati
git show-ref --tags

# Mostrare tag annotati (con messaggio)
git tag -n

# Cercare pattern in tutti i tag
for tag in $(git tag); do
    echo "=== Tag: $tag ==="
    git show $tag | head -20
done

# Confrontare tag con branch corrente
git diff secret HEAD

# Verificare tipo di tag (lightweight vs annotated)
git cat-file -t secret
```

### Domande aperte
- Qual è la differenza tra lightweight e annotated tags in Git?
- Come vengono usati i tag in workflow di release? 
- In penetration test, perché i tag sono spesso trascurati durante l'analisi?
- Quali vulnerabilità possono essere introdotte tramite tag maliziosi?
- Come gestire tag in ambienti production?

### Note
In scenari reali, i tag possono contenere:

- Build artifacts con segreti incorporati
- Versioni specifiche con vulnerabilità note
- Metadata sensibile in tag annotati
- Riferimenti a commit rimossi dalla storia principale

**Best practice per gestione tag sicura**:

1. Firmare tag critici con GPG
2. Verificare integrità dei tag prima di usarli
3. Limitare chi può creare/eliminare tag
4. Scansionare tag per segreti come parte della pipeline
5. Documentare scopo e contenuto dei tag

**Pattern di sicurezza nei tag**:

- Tag di release potrebbero contenere binari non scrutinizzati
- Tag di sviluppo potrebbero avere configurazioni di test
- Tag sperimentali potrebbero contenere codice vulnerabile
- Tag legacy potrebbero referenziare commit con segreti