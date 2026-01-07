# Bandit Level 26 → Level 27

## Obiettivo
Utilizzare un binario setuid per eseguire comandi con i privilegi di bandit27 e leggere la password protetta.

## Comandi utilizzati
```bash
# Dalla shell di bandit26 ottenuta nel livello precedente
./bandit27-do cat /etc/bandit_pass/bandit27
```

## Analisi Tecnica
### Cosa ho imparato
- **Setuid binari**: eseguiti con i privilegi del proprietario del file
- **Privilege escalation diretta**: quando un binario setuid permette esecuzione arbitraria
- **Path traversal**: il binario esegue qualsiasi comando fornito come argomento
- **Minimal exploitation**: spesso la soluzione più semplice è la migliore

### Analisi del binario
```bash
# Verificare i permessi
ls -la bandit27-do
# Output: -rwsr-x--- 1 bandit27 bandit26 14876 Oct 14 09:46 bandit27-do

# Testare il funzionamento
./bandit27-do id
# Output: uid=11026(bandit26) gid=11026(bandit26) euid=11027(bandit27) groups=11026(bandit26)
# euid=11027 conferma che viene eseguito come bandit27
```

### Vulnerabilità
1. **Setuid bit attivo**: `-rwsr-x---` (la `s` indica setuid)
2. **Nessuna validazione input**: esegue qualsiasi comando passato
3. **Accesso completo**: permette di leggere qualsiasi file accessibile a bandit27

### Comandi alternativi di verifica
```bash
# Verificare i permessi in dettaglio
stat bandit27-do

# Eseguire shell interattiva
./bandit27-do /bin/bash
# Attenzione: questa shell potrebbe non avere tutti i permessi setuid

# Esplorare filesystem come bandit27
./bandit27-do ls -la /home/bandit27
./bandit27-do find / -type f -name "*bandit27*" 2>/dev/null
```

### Domande aperte
- Qual è la differenza tra UID reale (real) ed effettivo (effective) in contesti setuid?
- Come proteggere binari setuid da abusi (capabilities, seccomp, namespaces)?
- In penetration test, come cercare binari setuid vulnerabili?
- Quali vulnerabilità comuni affliggono i binari setuid?
- Come auditare binari setuid in ambienti production?

### Note

Questo livello dimostra il pericolo dei binari setuid con funzionalità eccessive.
In scenari reali, binari simili sono stati sfruttati per:
- Leggere file di configurazione sensibili
- Modificare file di sistema
- Ottenere shell privilegiate
- Bypass controlli di accesso



Best practice per binari setuid:
1. Principio del minimo privilegio: fare solo ciò strettamente necessario
2. Validazione rigorosa degli input
3. Drop dei privilegi quando possibile
4. Isolamento (chroot, namespaces)
5. Audit regolare del codice

**Nota**: Se ./bandit27-do non funziona direttamente, assicurarsi di essere nella directory corretta e che il binario abbia permessi di esecuzione.