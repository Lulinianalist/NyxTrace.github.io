# 🍪 Analisi attacco a sito web – Forza bruta + malware JavaScript

## 📌 Scenario
Un ex dipendente ha compromesso il sito `yummyrecipesforme.com`:
- Attacco di **forza bruta** all'account amministratore (password predefinita)
- Iniezione di **JavaScript malevolo** che forza il download di un file eseguibile
- **Reindirizzamento** a `greatrecipesforme.com` (sito fasullo con malware)

## 🔍 Evidenze dai log (tcpdump)

| Fase | Protocollo | Dettaglio |
|------|------------|-----------|
| 1 | DNS | Richiesta A per `yummyrecipesforme.com` → IP `203.0.113.22` |
| 2 | TCP | Handshake a 3 vie verso porta 80 |
| 3 | HTTP | `GET / HTTP/1.1` – il server risponde con il malware |
| 4 | DNS | Nuova richiesta A per `greatrecipesforme.com` → IP `192.0.2.17` |
| 5 | TCP/HTTP | Connessione verso il sito fasullo con malware |

## 🧠 Analisi dell’attacco

| Fase | Descrizione |
|------|-------------|
| **Accesso iniziale** | Forza bruta su pannello admin (password predefinita) |
| **Persistenza** | Modifica del codice sorgente (JavaScript iniettato) |
| **Azione malevola** | Download forzato + reindirizzamento a sito fasullo |
| **Impatto** | Clienti infettati, rallentamento PC, perdita fiducia |

## 🛡️ Raccomandazioni per prevenire attacchi di forza bruta

- ✅ Imporre **password complesse** (non quelle predefinite)
- ✅ Abilitare **autenticazione a più fattori (MFA/2FA)**
- ✅ Implementare **CAPTCHA / reCAPTCHA** dopo tentativi falliti
- ✅ **Limitare i tentativi di login** (es. 5 tentativi, poi blocco temporaneo)
- ✅ Monitorare i log degli accessi al pannello admin

## 📁 File allegati

| File | Descrizione |
|------|-------------|
| [tcpdump.log](./tcpdump.log) | Log originale dell’analisi (da caricare) |

## ✅ Stato
📌 **Completato** – Esercizio del corso Google Cybersecurity

## 👤 Autore
NyxTrace – Cybersecurity Analyst
