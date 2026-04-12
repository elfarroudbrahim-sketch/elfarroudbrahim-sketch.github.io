---
title: "Implémentation SOC & SOAR : Automatisation de la Réponse aux Incidents"
author: Brahim El Farroud
date: 2026-04-12 10:00:00 +0100
categories: [Projects, Cybersecurity]
tags: [Wazuh, TheHive, Shuffle, SOC, SOAR, Threat Hunting]
image:
  path: /assets/img/posts/soc_project.jpg
  alt: "Architecture SOC/SOAR avec Wazuh et TheHive"
---

<style>
  .main-container {
    font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.6;
  }
  .soc-header-card {
    background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
    border-radius: 15px;
    padding: 30px;
    border: 1px solid #334155;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    margin-bottom: 40px;
  }
  .feature-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    margin: 30px 0;
  }
  .feature-item {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    border-radius: 12px;
    padding: 20px;
    transition: transform 0.3s ease, border-color 0.3s ease;
  }
  .feature-item:hover {
    transform: translateY(-5px);
    border-color: #3b82f6;
  }
  .feature-item h4 {
    color: #3b82f6;
    margin-top: 0;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .workflow-section {
    background: #0f172a;
    border-radius: 15px;
    padding: 25px;
    border-left: 4px solid #ef4444;
    position: relative;
    overflow: hidden;
  }
  .workflow-section::before {
    content: "LIVE ANALYSIS";
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 0.6rem;
    color: #ef4444;
    letter-spacing: 2px;
    font-weight: bold;
    border: 1px solid #ef4444;
    padding: 2px 8px;
    border-radius: 4px;
  }
  .tech-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 20px;
  }
  .pill {
    background: #1e293b;
    color: #f8fafc;
    border: 1px solid #334155;
    padding: 5px 15px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: 500;
  }
  .success-metric {
    color: #10b981;
    font-weight: bold;
  }
</style>

<div class="main-container">

<div class="soc-header-card">
  <h2 style="color: #f8fafc; margin-top: 0;">🛡️ Mission du Projet</h2>
  <p style="color: #cbd5e1; font-size: 1.1rem;">
    Conception d'un écosystème de cyber-défense distribué visant à transformer la détection passive en <strong>réponse active automatisée</strong>. Ce projet simule un environnement d'entreprise réel pour minimiser le MTTR (Mean Time To Respond).
  </p>
</div>

## 🏗️ Architecture du Réseau (Lab)

Comme illustré dans mon schéma, l'infrastructure est segmentée pour isoler les flux critiques :

<div class="feature-grid">
  <div class="feature-item">
    <h4>🔍 Détection & SIEM</h4>
    <p><strong>Wazuh</strong> assure la corrélation des logs, le monitoring d'intégrité (FIM) et la détection des Rootkits.</p>
  </div>
  <div class="feature-item">
    <h4>⚡ SOAR & Automation</h4>
    <p><strong>Shuffle</strong> orchestre les workflows entre les outils via Webhooks et APIs REST.</p>
  </div>
  <div class="feature-item">
    <h4>📁 Incident Response</h4>
    <p><strong>TheHive</strong> centralise les alertes et permet une investigation collaborative sur les cas complexes.</p>
  </div>
  <div class="feature-item">
    <h4>🌐 Network Security</h4>
    <p><strong>pfSense</strong> et <strong>Suricata</strong> gèrent le filtrage et l'IDS/IPS au périmètre du réseau.</p>
  </div>
</div>

---

## 🚀 Workflow de Remédiation Automatisée

<div class="workflow-section">
  <h3 style="color: #f8fafc; margin-top: 0;">Processus de Réponse Dynamique</h3>
  <ol style="color: #cbd5e1;">
    <li><strong>Ingestion :</strong> Un agent Wazuh sur le <em>Victim Network</em> détecte une activité suspecte.</li>
    <li><strong>Orchestration :</strong> Shuffle reçoit l'alerte et déclenche un script d'enrichissement.</li>
    <li><strong>Enrichissement :</strong> L'observable (IP/Hash) est soumis à <strong>VirusTotal</strong> pour vérification.</li>
    <li><strong>Action :</strong> Si malveillant, le système crée un incident dans <strong>TheHive</strong> et envoie une notification instantanée.</li>
  </ol>
</div>

---

## 🛠️ Stack Technique

<div class="tech-stack">
  <span class="pill">Wazuh SIEM</span>
  <span class="pill">TheHive 5</span>
  <span class="pill">Shuffle SOAR</span>
  <span class="pill">Suricata IDS</span>
  <span class="pill">Docker & Docker Compose</span>
  <span class="pill">pfSense</span>
</div>

---

## 📈 Résultats & Impact

* <span class="success-metric">Vitesse :</span> Passage d'une analyse manuelle de 5-10 min à une réponse automatisée en **< 15 secondes**.
* <span class="success-metric">Efficacité :</span> Centralisation de 100% des logs de sécurité sur un tableau de bord unique.
* <span class="success-metric">Fiabilité :</span> Réduction drastique des faux positifs grâce à l'enrichissement automatique via l'intelligence des menaces (Threat Intel).

</div>