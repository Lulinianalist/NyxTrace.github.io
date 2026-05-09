# 🛡️ Analisi Attacco SYN Flood – Denial of Service (DoS)

## 📌 Scenario
Un'agenzia di viaggi subisce un'interruzione del server web. I dipendenti non riescono ad accedere al sito per cercare pacchetti vacanza per i clienti. Il browser mostra un **errore di timeout della connessione**.

## 🔍 Identificazione dell'attacco

**Tipo di attacco:** SYN Flood (una forma di Denial of Service - DoS)

**Evidenze dai log:**
- Numero elevato di richieste TCP SYN provenienti da un indirizzo IP sconosciuto
- Il server web è sovraccarico e perde capacità di rispondere
- Nessuna richiesta completata (mancano gli ACK finali)

## 🧠 Come funziona l'attacco

### Handshake TCP normale (3 vie):
1. **SYN** – Il client invia una richiesta di sincronizzazione al server
2. **SYN/ACK** – Il server conferma e lascia una porta aperta
3. **ACK** – Il client conferma e la connessione viene stabilita

### Durante l'attacco SYN Flood:
- L'attaccante invia **migliaia di pacchetti SYN** senza mai completare l'handshake
- Il server lascia **connessioni half-open** (in attesa dell'ACK finale)
- La coda di connessione si **satura**
- Il server **ignora o rifiuta** le nuove richieste legittime

## 📊 Analisi traffico (Wireshark)

Dal registro pacchetti si evidenzia:
- Richieste SYN ripetute dallo **stesso indirizzo IP**
- Nessuna richiesta completa (manca il three-way handshake)
- Pattern coerente con un **attacco SYN flood**

## 💥 Impatto sulla rete aziendale

| Conseguenza | Descrizione |
|-------------|-------------|
| ❌ Server irraggiungibile | I dipendenti non possono accedere al sito |
| ⏰ Timeout di connessione | Le richieste legittime rimangono in attesa |
| 🔥 Risorse consumate | CPU, memoria e coda TCP del server sovraccaricate |
| 🚫 Sito indisponibile | Totale interruzione del servizio |

## 📉 Conseguenze per l'organizzazione

- Impossibilità per i dipendenti di cercare offerte per i clienti
- Perdita di fatturato (clienti che vanno altrove)
- Danno di immagine e reputazione
- Possibile perdita di fiducia dei clienti abituali
- Costi aggiuntivi per intervento tecnico

## 🛡️ Misure di mitigazione adottate

1. **Server messo temporaneamente offline** – per consentire il ripristino
2. **Firewall configurato** – blocco dell'indirizzo IP malevolo
3. **Consapevolezza** – la soluzione di blocco IP è temporanea (l'attaccante può falsificare altri IP)

## 🔧 Prevenzione per il futuro (opzionale)

| Tecnica | Descrizione |
|---------|-------------|
| **SYN cookies** | Evita di allocare risorse per connessioni half-open |
| **Rate limiting** | Limita il numero di richieste SYN al secondo da uno stesso IP |
| **Firewall con rilevamento DoS** | Blocca automaticamente IP che superano una soglia |
| **IDS/IPS** | Rilevamento e prevenzione in tempo reale |
| **Anti-DDoS esterno** | Servizi come Cloudflare o Akamai |

## 🆚 Differenza DoS vs DDoS

| DoS (Denial of Service) | DDoS (Distributed DoS) |
|------------------------|------------------------|
| Singolo dispositivo | Multipli dispositivi (botnet) |
| Più facile da bloccare | Difficile da bloccare (tanti IP diversi) |
| Es: SYN flood | Es: attacco coordinato da migliaia di macchine |

## ✅ Stato
📌 **Progetto completato** – Esercizio del Google Cybersecurity Certificate

## 👤 Autore
Lulinianalist – Portfolio Cybersecurity
