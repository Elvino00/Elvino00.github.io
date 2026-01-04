# Bandit Level 3 → Level 4

## Obiettivo
Trovare e leggere un file nascosto all'interno della directory `inhere`.

## Comandi utilizzati
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
cd inhere
ls -a
cat ...Hiding-From-You
```


## Analisi tecnica


### Cosa ho imparato
- I file che iniziano con `.` (dotfiles) sono normalmente nascosti in Linux
- Il comando `ls -a` mostra tutti i file, inclusi quelli nascosti (`a` sta per "all")
- I file nascosti non sono protetti, solo non visibili con ls standard
- Directory come `inhere` possono contenere file nascosti come elemento di un *Capture The Flag*

### Domande aperte
- Qual è lo scopo originale dei file nascosti in Unix/Linux?
- Ci sono altri modi per visualizzare file nascosti oltre a `ls -a`?
- Come cercare ricorsivamente file nascosti in un sistema?
- Quali file nascosti sono comunemente sfruttati in attacchi reali?


### Note
Il file si chiamava *...Hiding-From-You* . I file nascosti sono una feature del filesystem, non una misura di sicurezza.