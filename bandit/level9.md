# Bandit Level 9 → Level 10

## Obiettivo
Trovare una stringa leggibile da umani preceduta da due o più caratteri `=` nel file `data.txt` (che contiene dati binari).

## Comandi utilizzati
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
grep -Eo '={2,}[[:print:]]+' -a data.txt | tail -1 | sed 's/^[= ]*//'
```

**Oppure** :

```bash
strings data.txt | grep -E '={2,}'
```

## Analisi tecnica

### Cosa ho imparato
- `strings`: estrae sequenze di caratteri stampabili da file binari
- `grep -E`: abilita espressioni regolari estese
- `grep -a`: forza la lettura come testo (binary-safe)
- `grep -o`: stampa solo la parte corrispondente al pattern
- `tail -1`: prende l'ultima riga dell'output
- `sed 's/^[= ]*//'`: rimuove `=` e spazi all'inizio della stringa

### Spiegazione pattern regex
- `={2,}`: due o più caratteri `=`
- `[[:print:]]` è una classe POSIX più affidabile di `[ -~]` per encoding misti
- `[[:print:]]+`: uno o più caratteri stampabili (lettere, numeri, punteggiatura, spazi)

### Perchè questa complessità?
1. Il file contiene dati binari → serve `-a` o `strings`
2. La password è preceduta da `==========` → pattern `={2,}`
3. Ci sono più corrispondenze → `tail -1` prende l'ultima (la password)
4. La password ha `=` attaccati → `sed` li rimuove


### Domande aperte
- Qual è la differenza tra `strings` e `grep -a` per file binari?
- Come cercare pattern specifici in grandi dump di memoria o network capture?
- Quali altri caratteri non stampabili sono comuni in file "contaminati"?
- In forensics, come identificare dati significativi in file corrotti?

### Note
Le classi POSIX (`[[:print:]]`) sono più portabili di range specifici.
La combinazione di tool Unix (`grep`, `sed`, `tail`) permette di risolvere problemi complessi con semplici componenti.