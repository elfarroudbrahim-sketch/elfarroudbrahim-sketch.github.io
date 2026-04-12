---
title: "Architecte DevOps : Déploiement CI/CD de Haute Disponibilité"
author: Brahim El Farroud
date: 2026-04-12 11:00:00 +0100
categories: [Projects, DevOps]
tags: [Jenkins, Docker, AWS, Cloudflare, Nginx, CI/CD]
image:
  path: /assets/img/posts/devops-pipeline-banner.png
  alt: "Architecture DevOps Complète"
---

<style>
  /* --- Global Dashboard Style --- */
  .project-body { font-family: 'Inter', sans-serif; color: var(--text-color); }
  
  .hero-card {
    background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
    border: 1px solid #334155;
    border-radius: 16px;
    padding: 35px;
    margin-bottom: 40px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.3);
  }

  .tech-stack-container {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin: 25px 0;
  }

  .badge-tech {
    background: #0ea5e9;
    color: white;
    padding: 6px 16px;
    border-radius: 50px;
    font-size: 0.85rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  /* --- Grid System --- */
  .info-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin-bottom: 40px;
  }

  .card-glass {
    background: rgba(30, 41, 59, 0.5);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 12px;
    padding: 25px;
    height: 100%;
  }

  .card-glass h3 { color: #38bdf8; margin-top: 0; }

  /* --- Pipeline Stages --- */
  .pipeline-flow { border-left: 2px dashed #334155; padding-left: 30px; margin-left: 20px; }
  .step { position: relative; margin-bottom: 30px; }
  .step::before {
    content: '';
    position: absolute;
    left: -41px;
    top: 0;
    width: 20px;
    height: 20px;
    background: #0ea5e9;
    border-radius: 50%;
    border: 4px solid #0f172a;
  }

  /* --- Troubleshooting Section --- */
  .debug-log {
    background: #000;
    color: #10b981;
    font-family: 'Fira Code', monospace;
    padding: 20px;
    border-radius: 8px;
    font-size: 0.9rem;
    border-left: 4px solid #10b981;
  }
  .error-text { color: #ef4444; }
</style>

<div class="project-body">

<div class="hero-card">
  <h1 style="color: #fff; margin: 0 0 15px 0; font-size: 2.2rem;">🚀 Infrastructure DevSecOps Cloud</h1>
  <p style="color: #94a3b8; font-size: 1.1rem; line-height: 1.6;">
    Réalisation d'une chaîne <strong>CI/CD industrielle</strong> orchestrée sur AWS. Ce projet démontre la maîtrise du cycle de vie logiciel, de l'isolation réseau des bases de données jusqu'à l'automatisation sécurisée via Jenkins et Docker.
  </p>
  <div class="tech-stack-container">
    <span class="badge-tech">AWS EC2</span>
    <span class="badge-tech">Docker Compose</span>
    <span class="badge-tech">Jenkins 2.541</span>
    <span class="badge-tech">Cloudflare</span>
    <span class="badge-tech">Nginx</span>
    <span class="badge-tech">React</span>
  </div>
</div>

## 🌐 Architecture & Topologie Réseau

L'infrastructure est conçue pour la résilience et la sécurité, utilisant Cloudflare comme première ligne de défense.

<div class="info-grid">
  <div class="card-glass">
    <h3>🛡️ Sécurité & DNS</h3>
    <ul>
      <li><strong>Cloudflare Proxy :</strong> Protection WAF et masquage de l'IP réelle du serveur EC2 (52.55.147.178).</li>
      <li><strong>SSL Origin :</strong> Chiffrement TLS de bout en bout entre le Edge et l'origine AWS.</li>
      <li><strong>Isolation Docker :</strong> Bases de données (MariaDB/Redis) confinées dans un réseau privé sans accès Internet.</li>
    </ul>
  </div>
  <div class="card-glass">
    <h3>🛠️ Orchestration Services</h3>
    <ul>
      <li><strong>Gateway Nginx :</strong> Point d'entrée unique gérant le virtual hosting pour 4 sous-domaines.</li>
      <li><strong>Frontend Optimized :</strong> Build multi-stage Node.js réduisant l'image de 500MB à 25MB.</li>
      <li><strong>CTFd Management :</strong> Plateforme de cybersécurité avec persistance des données et cache Redis.</li>
    </ul>
  </div>
</div>

---

## ⚡ Automatisation CI/CD : Jenkins Pipeline

Déploiement en continu déclenché par **Webhooks GitHub** avec une durée moyenne de build de **56 secondes**.

<div class="pipeline-flow">
  <div class="step">
    <strong>Stage: Check Tools</strong>
    <p>Validation de l'intégrité de l'environnement (Docker, Compose, Git).</p>
  </div>
  <div class="step">
    <strong>Stage: Source Control</strong>
    <p>Pull automatique du code depuis la branche <code>main</code> suite à un push développeur.</p>
  </div>
  <div class="step">
    <strong>Stage: Build & Deploy</strong>
    <p>Reconstruction sélective des conteneurs modifiés sans interruption de service (Zero Downtime).</p>
  </div>
</div>

---

## 🔍 Troubleshooting & Ingénierie

La mise en production a nécessité la résolution de défis techniques complexes rencontrés durant la phase de stabilisation :

### 1. Permission Socket Docker
<div class="debug-log">
  <span class="error-text">ERROR: Permission denied while trying to connect to the Docker daemon socket</span><br>
  > Cause: Utilisateur Jenkins limité dans le conteneur.<br>
  > Fix: Montage du socket hôte et exécution en mode <code>user: root</code>.
</div>

### 2. Redirection Proxy HTTPS
<div class="debug-log">
  <span class="error-text">ISSUE: Jenkins/CTFd redirecting to HTTP 302 (Mixed Content)</span><br>
  > Cause: Perte du schéma HTTPS derrière le reverse proxy.<br>
  > Fix: Injection des headers X-Forwarded-Proto: https  via Nginx.
</div>

---


</div>