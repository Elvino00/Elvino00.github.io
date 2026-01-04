# Bandit Level 5 → Level 6


## Obiettivo
Trovare un file da 1033 byte, non eseguibile e leggibile da umani, da qualche parte nella directory `inhere` (che contiene molte sottodirectory).

## Comandi utilizzati
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
cd inhere
```

Ho ispezionato manualmente le sottodirectory finché non ho trovato:
```bash
ls -la maybehere07/
```

Output:

```text
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 .
drwxr-x--- 22 root bandit5 4096 Oct 14 09:26 ..
-rwxr-x---  1 root bandit5 3663 Oct 14 09:26 -file1
-rwxr-x---  1 root bandit5 3065 Oct 14 09:26 .file1
-rw-r-----  1 root bandit5 2488 Oct 14 09:26 -file2
-rw-r-----  1 root bandit5 1033 Oct 14 09:26 .file2  <-- TARGET
-rwxr-x---  1 root bandit5 3362 Oct 14 09:26 -file3
-rwxr-x---  1 root bandit5 1997 Oct 14 09:26 .file3
-rwxr-x---  1 root bandit5 4130 Oct 14 09:26 spaces file1
-rw-r-----  1 root bandit5 9064 Oct 14 09:26 spaces file2
-rwxr-x---  1 root bandit5 1022 Oct 14 09:26 spaces file3
```

Poi:
```bash
cat maybehere07/.file2
```


## Analisi tecnica

### Cosa ho imparato
- Il comando `ls -la` mostra dettagli fondamentali:
    - Colonna 1: permessi (`-rw-r-----` = non eseguibile, leggibile)
    - Colonna 5: dimensione in byte (1033)
- Criteri combinati: dimensione esatta + permessi specifici + leggibilità
- I file nascosti (iniziante con `.`) possono essere i target
- L' Ispezione manuale funziona ma è inefficiente per molti file

### Alternative migliori
```bash
# Cerca ricorsivamente file di esattamente 1033 byte
find . -type f -size 1033c

# Combina con controllo permessi (non eseguibile)
find . -type f -size 1033c ! -executable

# Aggiungi controllo leggibilità
find . -type f -size 1033c ! -executable -exec file {} \; | grep text
```

### Domande aperte
- Come funziona esattamente il calcolo della dimensione con find -size?
- Qual è la differenza tra -executable e permessi x in ls?
- In uno scenario reale con migliaia di file, come automatizzare questa ricerca?
- Quali altri attributi di file potrebbero essere rilevanti per la sicurezza?


### Note
Ho usato un approccio manuale (ispezione visiva di `ls -la` output) che ha funzionato ma non scala.
La soluzione con `find` sarebbe stata più professionale e trasferibile a scenari reali.