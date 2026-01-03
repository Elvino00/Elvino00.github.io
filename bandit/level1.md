# Bandit Level 1 → Level 2

## Obiettivo
Leggere il contenuto di un file chiamato `-` situato nella home directory.

## Comandi utilizzati
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
cat $HOME/-
```

## Analisi tecnica

#### Cosa ho imparato
- In Linux, `-` è un carattere speciale che spesso rappresenta stdin/stdout
- Alcuni comandi (come `cat`) interpretano `-` come "leggi da stdin" invece che come nome file
- Modi per forzare l'interpretazione come file: path assoluto (*/home/bandit1*), `./` (`cat ./-`), redirezionamento con `<` (`cat < -`)
- La variabile $HOME contiene il path della home directory dell'utente

#### Domande aperte
- Quali altri caratteri speciali possono causare problemi con i nomi file?
- Come funziona esattamente l'interpretazione di - nei diversi comandi Linux?
- Esistono comandi che gestiscono `-` in modo diverso da cat?


#### Note
Questo problema è un classico: file con nomi "problematici". Il modo pratico per uscirsene è usare path assoluti oppure `./` per evitare ambiguità.
Dopo aver ottenuto la password, ho usato `exit` e, per affrontare il livello successivo, mi sono riconnesso con:
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

