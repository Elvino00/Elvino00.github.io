# Bandit Level 0 → Level 1

## Obiettivo
Accedere al server via SSH e recuperare la password per il livello successivo da un file nella home directory.

## Comandi utilizzati
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

## Password iniziale fornita

`bandit0`

## Una volta connessi:

```bash
ls
cat readme
```

## Analisi tecnica

#### Cosa ho imparato

- Accesso SSH su porta non standard (2220 invece di 22)
- Comandi base Linux: `ls` per listare file, `cat` per leggerne il contenuto
- La password per il livello successivo è memorizzata in chiaro in un file di testo

#### Domande aperte
- Perché usare una porta SSH diversa dalla 22? È una misura di sicurezza efficace?
- Come funziona il protocollo SSH?
- Quali alternative ci sono all'autenticazione via password?

#### Note
Il file `readme` conteneva la password che non riporto per sicurezza.
