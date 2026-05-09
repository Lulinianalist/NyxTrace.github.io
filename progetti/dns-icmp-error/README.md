# 📡 Analisi errore DNS – Porta 53 unreachable (ICMP)

## 📌 Scenario
Un'azienda cliente (www.yummyrecipesforme.com) risulta irraggiungibile. I clienti segnalano di non riuscire ad accedere al sito, con il browser che va in timeout.

Il reparto IT avvia un'analisi del traffico di rete con `tcpdump` per identificare la causa.

---

## 🔍 Analisi dei log (tcpdump)

Sono state catturate le seguenti comunicazioni:

| Ora | Sorgente → Destinazione | Protocollo | Contenuto |
|-----|------------------------|------------|------------|
| 13:24:32 | 192.51.100.15 → 203.0.113.2 | UDP/DNS | Query ID 35084 A? yummyrecipesforme.com |
| 13:24:32 | 203.0.113.2 → 192.51.100.15 | ICMP | Port 53 unreachable |
| 13:26:32 | (stessa richiesta) | UDP/DNS | Query ID 35084 A? yummyrecipesforme.com |
| 13:26:32 | (stessa risposta) | ICMP | Port 53 unreachable |
| 13:28:32 | (stessa richiesta) | UDP/DNS | Query ID 35084 A? yummyrecipesforme.com |
| 13:28:32 | (stessa risposta) | ICMP | Port 53 unreachable |

---

## 🧠 Cosa ci dicono i log

| Evidenza | Interpretazione |
|----------|------------------|
| Il client (192.51.100.15) invia richieste DNS alla porta 53 del server 203.0.113.2 | Sta cercando di risolvere il nome `yummyrecipesforme.com` in un IP |
| Il server risponde sempre con ICMP Type 3 Code 3 | `port unreachable` → la porta 53 UDP non è in ascolto |
| La porta 53 è lo standard per il servizio DNS | Il server non sta erogando il servizio DNS |
| Lo stesso ID query (35084) viene riutilizzato 3 volte | Comportamento anomalo (possibile client mal configurato o attacco a basso rate) |

---

## 📊 Riepilogo dell'incidente

| Elemento | Dettaglio |
|----------|-----------|
| **Problema segnalato** | Sito irraggiungibile, timeout |
| **Prima segnalazione** | 13:24:32 |
| **Protocolli coinvolti** | UDP (trasporto), DNS (applicativo), ICMP (errore) |
| **Porta coinvolta** | 53 UDP (DNS) |
| **IP client** | 192.51.100.15 |
| **IP server DNS** | 203.0.113.2 |
| **Risposta del server** | ICMP port unreachable |
| **Causa probabile** | Servizio DNS non attivo sul server 203.0.113.2 (o firewall che blocca la porta 53) |

---

## 🛠️ Azioni raccomandate

1. Verificare se 203.0.113.2 è ancora il DNS corretto per il dominio
2. Controllare che il servizio DNS sia in esecuzione su quel server
3. Verificare eventuali regole firewall sulla porta 53 UDP
4. Testare la risoluzione usando un DNS alternativo (es. 8.8.8.8)
5. Indagare sull’uso anomalo dello stesso ID query (possibile spoofing o replay)

---

## 🧪 Lezione imparata

> Un errore ICMP `port unreachable` non indica un attacco, ma un **servizio non disponibile**. L'analisi dei log permette di distinguere tra un guasto tecnico e un attacco attivo.

---

## 📁 File allegati

| File | Descrizione |
|------|-------------|
| [tcpdump_log.txt](./tcpdump_log.txt) | Log originale dell'analisi (da caricare) |

---

## ✅ Stato
📌 **Completato** – Esercizio del corso Google Cybersecurity

## 👤 Autore
Lulinianalist – Portfolio Cybersecurity
