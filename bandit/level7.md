# Bandit Level 7 → Level 8

## Obiettivo
Trovare la password nel file `data.txt` accanto alla parola "millionth".

## Comandi utilizzati
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
find / -name data.txt 2>/dev/null
cat data.txt | grep millionth
```

## Analisi tecnica

### Cosa ho imparato
- `find / name data.txt`: cerca file di nome esatto `data.txt` in tutto il filesystem
- `grep millionth`: filtra le linee contenenti la stringa "millionth"
- Pipeline (`|`): connette output di `cat` a input di `grep`
- L'output è `millionth *password livello successivo omessa per sicurezza*`

### Alternative equivalenti
```bash
# grep legge direttamente il file
grep millionth data.txt

# con espressione regolare per estrarre solo la password
grep -oP 'millionth\s+\K.*' data.txt
```

### Domande aperte
- Qual è la differenza tra `grep`, `awk` e `sed` per l'estrazione di testo?

- Come cercare ricorsivamente stringhe in molti file?

- In scenari reali, cosa si cerca nei file di log con `grep`?

- Come gestire file molto grandi che non entrano in memoria?

### Note
Il file `data.txt` era nella home directory, quindi `find` non era strettamente necessario.
`grep` è uno strumento fondamentale per analisi testuale in sicurezza (log, configurazioni, dati).