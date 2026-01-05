# Bandit Level 11 → Level 12

## Obiettivo
Decifrare testo ROT13 (rotazione di 13 posizioni) dal file `data.txt`.

## Comandi utilizzati
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

## Analisi tecnica

### Cosa ho imparato
- ROT13 è un cifrario a sostituzione monoalfabetica (Caesar cipher con shift 13)
- `tr` (translate) sostituisce caratteri da un set a un altro
- Sintassi: `tr 'set1' 'set2'` → mappa caratteri da set1 a set2
- `'a-zA-Z'`: tutte le lettere minuscole e maiuscole
- `'n-za-mN-ZA-M'`: mapping ROT13:
    - a→n, b→o, ..., m→z, n→a, ..., z→m
    - vale lo stesso per le maiuscole

### Alternative
```bash
# Usare input redirection
tr 'a-zA-Z' 'n-za-mN-ZA-M' < data.txt

# Con rot13 dedicato (su alcuni sistemi)
rot13 data.txt
```

### Domande aperte
- Quali altri cifrari esistono?
- Come identificare automaticamente testo cifrato/offuscato (frequenze lettere)?
- In analisi malware, dove si trova comunemente testo offuscato con metodi base come ROT13, Base64, o XOR semplice?
- Quali tool sono utili per l'analisi crittografica base di dati sospetti?
- Come distinguere ROT13 da altri encoding (Base64,hex)?

### Note
ROT13 è un esempio di "security through obscurity" inefficace.
In contesti reali, mai usare per proteggere dati sensibili.
La password ottenuta non viene riportata per sicurezza.

**Importante**: `tr` funziona solo su caratteri singoli, non su byte o multibyte.
Per dati binari, servirebbero tool diversi.