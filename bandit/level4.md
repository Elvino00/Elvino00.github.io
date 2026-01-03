# Bandit Level 4 → Level 5

## Obiettivo

## Comandi utilizzati
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
cd inhere
cat ./'-file07'
```



## Analisi tecnica

### Cosa ho imparato
- Non tutti i file contenenti testo sono automaticamente "human-readable"
- Alcuni file possono contenere dati binari, caratteri non stampabili, o encoding speciali
- Metodo di ricerca: esaminare ogni file finché non si trova quello con testo leggibile
- Il comando `file` può aiutare a identificare il tipo di file senza aprirlo


### Alternative migliori
```bash
# Usare 'file' per identificare i tipi
file ./*

# Cercare file ASCII/text
find . -type f -exec file {} \; | grep text

# Oppure con string
strings ./* | head
```

### Domande aperte
- Cosa definisce esattamente un file "human-readable"?
- Quali encoding di testo sono comuni in Linux?
- Come funziona il comando `file` internamente?
- In un assessment reale, come si identificano rapidamente file interessanti?


### Note
Ho risolto tentando ogni file finché cat ./-file07 ha restituito testo leggibile.
In retrospettiva, usare file ./* sarebbe stato più efficiente.