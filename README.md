
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lulinianalist | Cybersecurity Analyst Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: #0a0a0f;
            color: #e0e0e0;
            line-height: 1.6;
            padding: 2rem 1rem;
        }
        .container {
            max-width: 1100px;
            margin: 0 auto;
        }
        header {
            text-align: center;
            margin-bottom: 3rem;
        }
        h1 {
            font-size: 2.5rem;
            background: linear-gradient(135deg, #00ff88, #00cc6a);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 0.5rem;
        }
        .badge {
            display: inline-block;
            background: #00ff8822;
            color: #00ff88;
            border: 1px solid #00ff8844;
            padding: 0.3rem 1rem;
            border-radius: 30px;
            font-size: 0.8rem;
            margin-top: 0.5rem;
        }
        .section {
            background: #111118;
            border-radius: 20px;
            padding: 2rem;
            margin-bottom: 2rem;
            border: 1px solid #222230;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }
        .section h2 {
            color: #00ff88;
            border-left: 4px solid #00ff88;
            padding-left: 1rem;
            margin-bottom: 1.5rem;
        }
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }
        .project-card {
            background: #0d0d14;
            border-radius: 15px;
            padding: 1.5rem;
            border: 1px solid #222230;
            transition: transform 0.2s, border-color 0.2s;
        }
        .project-card:hover {
            transform: translateY(-5px);
            border-color: #00ff8855;
        }
        .project-card h3 {
            color: #00ff88;
            margin-bottom: 0.5rem;
        }
        .project-card small {
            color: #00ff8866;
            font-size: 0.7rem;
        }
        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
        }
        .skill-tag {
            background: #1a1a24;
            padding: 0.4rem 1rem;
            border-radius: 30px;
            font-size: 0.85rem;
            font-weight: 500;
            color: #00ff88;
            border: 1px solid #00ff8822;
        }
        .contact-links {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
        }
        .contact-links a {
            color: #e0e0e0;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.2s;
        }
        .contact-links a:hover {
            color: #00ff88;
        }
        footer {
            text-align: center;
            margin-top: 2rem;
            color: #666;
            font-size: 0.85rem;
        }
        .status-badge {
            display: inline-block;
            background: #00ff8822;
            color: #00ff88;
            font-size: 0.7rem;
            padding: 0.2rem 0.6rem;
            border-radius: 20px;
            margin-top: 0.8rem;
        }
        @media (max-width: 768px) {
            h1 { font-size: 1.8rem; }
            .section { padding: 1.5rem; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🛡️ Ciao, sono Lulinianalist</h1>
            <div class="badge">🔒 Cybersecurity Analyst | Network Security | Threat Detection</div>
        </header>

        <div class="section">
            <h2>📁 Progetti Cybersecurity</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <h3>🛡️ Analisi ICMP Flood</h3>
                    <p>Simulazione attacco DoS su rete locale. Cattura traffico con Wireshark, identificazione pacchetti malevoli, regole di mitigazione iptables.</p>
                    <div class="status-badge">📌 Primo progetto completato</div>
                </div>
                <div class="project-card">
                    <h3>📊 Dashboard Threat Intelligence</h3>
                    <p>Visualizzazione attacchi in tempo reale da log firewall. Top source IP, geo-localizzazione, timeline attacchi.</p>
                    <div class="status-badge">🔜 In arrivo</div>
                </div>
                <div class="project-card">
                    <h3>🤖 Anomaly Detection su Traffico</h3>
                    <p>Script Python per rilevare pattern anomali (scan port, flood, brute force) da file pcap.</p>
                    <div class="status-badge">🔜 In arrivo</div>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>🛠 Competenze Tecniche</h2>
            <div class="skills">
                <span class="skill-tag">Wireshark / tcpdump</span>
                <span class="skill-tag">Python (Scapy, pandas)</span>
                <span class="skill-tag">IDS/IPS (Snort/Suricata)</span>
                <span class="skill-tag">ELK Stack / Grafana</span>
                <span class="skill-tag">Linux / iptables</span>
                <span class="skill-tag">Log Analysis</span>
                <span class="skill-tag">TCP/IP, ICMP, HTTP</span>
            </div>
        </div>

        <div class="section">
            <h2>📫 Contatti</h2>
            <div class="contact-links">
                <a href="#">🔗 LinkedIn</a>
                <a href="https://github.com/Lulinianalist" target="_blank">🐙 GitHub</a>
                <a href="#">✉️ Email</a>
            </div>
        </div>

        <footer>
            🛡️ Portfolio in aggiornamento — nuovi progetti e threat analysis ogni settimana
        </footer>
    </div>
</body>
</html>
