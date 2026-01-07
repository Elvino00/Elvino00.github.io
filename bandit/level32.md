# Bandit Level 32 → Level 33

## Obiettivo
Fuggire da una shell interattiva che converte automaticamente tutti i comandi in maiuscolo prima dell'esecuzione, per poi leggere la password del livello successivo.

## Contesto & Analisi Iniziale
Al login, viene avviata automaticamente una shell speciale denominata "**Uppercase Shell**". Questa shell applica una trasformazione all'input dell'utente, convertendo tutti i caratteri in maiuscolo prima di passarli all'esecutore. Poiché i comandi Linux e i percorsi dei file sono case-sensitive (distinguono tra maiuscole e minuscole), digitare `ls` o `cat` risulterà in un errore "Permission denied" o "Command not found". La sfida consiste nel trovare un modo per eseguire comandi nella loro forma originale.

## Comandi utilizzati

```bash
# 1. Connettersi al livello (dopo aver ottenuto la password del livello 32)
ssh bandit32@bandit.labs.overthewire.org -p 2220

# 2. Nella Uppercase Shell, digitare:
>> $0

# 3. Questo avvia una shell normale (sh). Ora si possono eseguire comandi standard:
$ whoami
bandit33
$ cat /etc/bandit_pass/bandit33
*password livello 33*
```

## Analisi Tecnica

### Cosa ho imparato
- **Shell Restricted Escape**: Tecniche per bypassare ambienti shell ristretti o modificati.
- **Parametri Posizionali di Shell**: `$0`, `$1`, `$2`, etc. `$0` contiene il nome/path dello script o eseguibile in esecuzione.
- **Ordine di Espansione delle Variabili**: Nella shell, l'espansione delle variabili (`$VAR`) avviene **dopo** la lettura dell'input e **prima** dell'esecuzione del comando. Una trasformazione applicata all'input grezzo non influisce sul risultato di questa espansione.
- **Case Sensitivity**: I sistemi Unix-like sono case-sensitive a livello di filesystem e comandi, una restrizione di conversione in maiuscolo rompe questo modello.

### Domande aperte
- Oltre a `$0`, quali altre variabili d'ambiente o caratteristiche della shell potrebbero essere testate per evadere da ambienti ristretti simili?
- In uno scenario di **Red Team**, come si potrebbero scoprire in modo sistematico i vettori di escape in una shell custom o in un'interfaccia a riga di comando (CLI) ristretta di un'applicazione?
- Dal lato **Blue Team**, come progettare una shell ristretta o un ambiente chrooted in modo sicuro per prevenire escape tramite variabili o espansioni?
- Esistono tool o framework per automatizzare il fuzzing di possibili escape in shell non standard?

### Note
- Perché Permission denied? Quando si digita `ls`, la shell cerca un eseguibile chiamato *LS* in una directory del `$PATH`. Non trovandolo (di solito esiste solo `ls`), alcune shell falliscono silenziosamente, altre restituiscono un errore di permesso generico.
- Vettore Affidabile: `$0` è un vettore di escape particolarmente affidabile in contesti simili perché punta sempre a un eseguibile valido (la shell stessa) ed è quasi sempre presente.
- Test in Ambiente Controllato: Per comprendere meglio, si può provare a creare uno script simile in bash:

```bash
#!/bin/bash
while read -p ">> " cmd; do
    uppercmd=$(echo "$cmd" | tr 'a-z' 'A-Z')
    echo "Executing: $uppercmd"
    eval $uppercmd
done
```

Si potrebbe vedere cosa succede testando `$0` con questo script.