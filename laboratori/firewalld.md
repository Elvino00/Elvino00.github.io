## Laboratorio: Firewall con firewalld su CentOS

**Obiettivo:**  
Configurare un firewall virtuale su CentOS 7 che inoltri il traffico tra due reti e blocchi selettivamente pacchetti verso un IP specifico.

---

### Descrizione tecnica

Ho creato un firewall virtuale con:
- **CentOS 7** con due interfacce di rete:
  - `enp1s0` (NAT) → accesso a internet
  - `enp7s0` (rete interna) → IP 192.168.100.1/24
- **Client Linux (Lubuntu)** sulla stessa rete interna con IP 192.168.100.2/24
- **firewalld** per gestire le regole di blocco
- **forwarding IP** attivato per far passare il traffico tra le due interfacce

Ho applicato una rich-rule per bloccare (reject) tutto il traffico diretto a `1.1.1.1`, testando con ping dal client.

---

### Spiegazione teorica

- **firewalld** è un firewall dinamico basato su zone e regole. A differenza di iptables (statico), permette di modificare le regole in runtime senza riavviare il servizio.
- **Reject vs Drop**:  
  - `reject` restituisce un errore ICMP (Destination Unreachable) → il client sa subito che il pacchetto è bloccato.  
  - `drop` ignora il pacchetto senza risposta → il client aspetta un timeout (più lento). Ho usato `reject` per testare rapidamente.
- **Forwarding IP**: il kernel deve essere abilitato a inoltrare pacchetti tra interfacce (`net.ipv4.ip_forward=1`). Senza questa opzione, il firewall non fa da router e il traffico si ferma.

---

### Applicazione pratica

**Configurazione IP statici** (per evitare DHCP):

```bash
# Su CentOS (firewall)
sudo ip addr add 192.168.100.1/24 dev enp7s0
sudo ip link set enp7s0 up

# Su Lubuntu (client)
sudo ip addr add 192.168.100.2/24 dev enp2s0
sudo ip link set enp2s0 up
```

**Disabilitare NetworkManager** (per evitare che sovrascriva gli IP):

```bash
sudo nmcli device set enp2s0 managed no   # Sul client
sudo nmcli device set enp7s0 managed no   # Sul firewall (opzionale)
```

**Abilitare forwarding IP**

```bash
sudo sysctl -w net.ipv4.ip_forward=1
```

**Avviare firewalld e aggiungere la regola**

```bash
sudo systemctl start firewalld
sudo systemctl enable firewalld

sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" destination address="1.1.1.1" reject'
sudo firewall-cmd --reload
```

**Test**

```bash
# Da Lubuntu - ping diretto al firewall (deve funzionare)
ping -I enp2s0 192.168.100.1

# Da Lubuntu - ping verso 1.1.1.1 (deve fallire con "Destination Host Unreachable")
ping -I enp2s0 1.1.1.1
```

**Verifica log (per vedere la regola attivata)**

```bash
sudo journalctl -u firewalld -f   # In tempo reale, mentre si invia il ping
```

### Domande aperte

1. Come si comporta firewalld con zone diverse?

2. Se assegno `enp7s0` alla zona *trusted* e `enp1s0` a *public*, le regole cambiano?
 Ho provato ma non ho ancora capito il comportamento.

3. **Reject** vs **Drop** in produzione?

4. In un ambiente enterprise, conviene usare `drop` per non rivelare informazioni (es. che esiste un firewall). Ma `reject` è più utile per debugging.

5. Persistenza dopo reboot?

Il forwarding IP con `sysctl -w` non è persistente dopo il riavvio. Ho scoperto che va aggiunto a `/etc/sysctl.conf` o a un file in `/etc/sysctl.d/`.

6. Come gestire il NAT?