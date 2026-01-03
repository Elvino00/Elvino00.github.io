# Bandit Level 2 → Level 3

## Obiettivo
Leggere il contenuto di un file con spazi nel nome: `spaces in this filename`.

## Comandi utilizzati
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
cat $HOME/'--spaces in this filename-'
```


## Analisi tecnica

### Cosa ho imparato
- I file con spazi nel nome richiedono un trattamento speciale in terminale
- Modi per gestire spazi:
    1. Virgolette singole: 'nome con spazi'
    2. Virgolette doppie: "nome con spazi"
    3. Escape carattere: nome\ con\ spazi
    4. Tab completion (premere Tab per autocompletare con escape automatico)

- Senza quoting, ogni parola è interpretata come argomento separato 

### Domande aperte

- Come gestiscono gli spazi le diverse shell (bash, zsh, fish) ?
- Quali caratteri problematici ci sono oltre agli spazi e `-` ?
- Negli script, qual è il metodo più robusto per gestire nomi file arbitrari?

### Note
Questo livello insegna il concetto fondamentale di "word splitting" nello shell.
La soluzione con `$HOME/` è ancora valida, ma ora serve anche il quoting per gli spazi.