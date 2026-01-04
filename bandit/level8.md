# Bandit Level 8 → Level 9

## Obiettivo
Trovare l'unica riga di testo che appare una sola volta nel file `data.txt`.

## Comandi utilizzati
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
sort data.txt | uniq -u
```

## Analisi tecnica

### Cosa ho imparato
- `sort`: ordina le righe in ordine alfabetico/numerico
- `uniq`: lavora su righe consecutive duplicate
- `uniq -u`: mostra solo le righe uniche (che appaiono una volta)
- La combinazione `sort | uniq` è standard per trovare duplicati in file non ordinati

Senza `sort`. righe duplicate non consecutive non sarebbero rilevate da `uniq`:

```text
AAA
BBB
AAA <- questa AAA non è consecutiva alla prima
```

`uniq` vedrebbe entrambe le AAA come uniche.


### Domande aperte
- Quali algoritmi di sorting usa `sort` per grandi file?
- Come gestire file troppo grandi per la memoria?
- In analisi sicurezza: come identificare entry sospette in log (es. IP unici)?
- Quali altri tool esistono per comparare file?

### Note
`uniq` è potente ma ha limitazioni: richiede input ordinato, lavora solo su righe complete.
La pipeline Unix (`|`) permette di combinare tool semplici per risolvere problemi complessi.