# 🛡️ Valutazione del rischio – Hardening di rete

## 📌 Contesto
Un'azienda di social media ha subito una grave violazione dei dati, con esposizione di informazioni personali dei clienti (nomi, indirizzi).  
Dopo un'ispezione della rete aziendale, sono state identificate **quattro vulnerabilità principali**:

| # | Vulnerabilità | Rischio |
|---|---------------|---------|
| 1 | Condivisione password tra dipendenti | Espansione superficie d'attacco |
| 2 | Password amministratore DB = default | Facilmente violabile con forza bruta |
| 3 | Firewall senza regole di filtro | Nessun controllo su traffico in/out |
| 4 | MFA non utilizzata | Accesso facilitato con sole credenziali |

---

## 🔧 Parte 1 – Strumenti e metodi di hardening raccomandati

### 1️⃣ Policy di gestione password
- **Divieto assoluto di condivisione** delle password tra dipendenti
- Ogni account deve essere **personale e tracciabile**
- Le password devono essere **complesse**:  
  `[A-Z][a-z][0-9][simboli]`, min. 12 caratteri
- Imporre il **cambio periodico** (es. ogni 90 giorni)

### 2️⃣ Protezione contro attacchi di forza bruta
- **Limitare i tentativi di login** a 4 tentativi falliti
- Dopo il 4° tentativo: **blocco temporaneo dell'account** (es. 15 minuti)
- Logging di tutti i tentativi falliti per analisi successiva

### 3️⃣ Autenticazione a più fattori (MFA)
- Obbligatoria per:
  - Accesso al pannello di amministrazione
  - Accesso al database
  - Accesso da reti esterne
- Fattori consigliati:
  - **Password** (qualcosa che sai)
  - **OTP via SMS/App** (qualcosa che hai)
  - **Impronta digitale** (opzionale, per ambienti protetti)

### 4️⃣ Configurazione firewall
- Regole di default: **blocca tutto** (whitelist)
- Aprire solo le porte strettamente necessarie (es. 443 HTTPS, 22 SSH con MFA)
- Filtrare traffico in entrata e in uscita
- Monitorare log del firewall per pattern anomali

---

## 📋 Parte 2 – Spiegazione delle raccomandazioni

### 🔹 Perché queste misure sono efficaci?

| Vulnerabilità | Soluzione | Perché funziona |
|---------------|-----------|------------------|
| Condivisione password | Policy + password complesse | Riduce superficie d'attacco, ogni azione è tracciabile |
| Password admin di default | Password complessa + limitazione tentativi | Rende la forza bruta impraticabile |
| Firewall senza regole | Regole whitelist + filtro porte | Solo traffico autorizzato entra/esce |
| MFA assente | Implementazione MFA obbligatoria | Anche se la password è rubata, l'accesso è bloccato |

### 🔹 Frequenza di implementazione

| Attività | Frequenza |
|----------|-----------|
| Cambio password amministratore | **Immediato**, poi ogni 90 giorni |
| Revisione regole firewall | **Mensile** o dopo ogni modifica di rete |
| Controllo tentativi di login | **In tempo reale** (automatizzato) |
| Policy di sicurezza (MFA, password) | **Una tantum** all'implementazione, poi **annuale** in fase di revisione |
| Formazione dipendenti | **Semestrale** (per evitare condividione password) |

### 🔹 Monitoraggio e miglioramento continuo
- Centralizzare i log di accesso (firewall, database, MFA)
- Impostare **alert automatici** per:
  - Tentativi di login falliti > 3 in 5 minuti
  - Accessi da IP anomali
  - Cambi password amministratore non autorizzati

---

## ✅ Stato
📌 **Completato** – Esercizio del corso Google Cybersecurity

## 👤 Autore
NyxTrace – Cybersecurity Analyst
