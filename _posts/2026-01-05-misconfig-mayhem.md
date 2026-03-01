---
title: "Misconfig Mayhem : Audit & Hardening OWASP A02"
author: Brahim El Farroud
date: 2026-01-05 10:00:00 +0100
categories: [Projects, Cybersecurity]
tags: [Docker, OWASP, RedTeam, BlueTeam, Hardening, Python]
image:
  path: /assets/img/posts/misconfig-mayhem-banner.png # Remplacez par votre image
  alt: "Analyse de sécurité SharePy"
---

<style>
  /* --- CSS Personnalisé pour un rendu Pro --- */
  
  /* Badges de sévérité */
  .vuln-badge {
    padding: 2px 8px;
    border-radius: 5px;
    font-size: 0.75rem;
    font-weight: bold;
    margin-right: 5px;
    display: inline-block;
  }
  .severity-high { background: #ff4d4d; color: white; }
  .severity-medium { background: #ffa64d; color: white; }
  .severity-low { background: #4d94ff; color: white; }
  
  /* Cartes d'analyse avec effet Hover */
  .analysis-card {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    padding: 20px;
    border-radius: 12px;
    margin: 20px 0;
    transition: all 0.3s ease;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
  }
  .analysis-card:hover {
    border-color: #007bff;
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,123,255,0.1);
  }
  
  /* Titres de section stylisés */
  .pro-header {
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--heading-color);
    margin-top: 2rem;
    margin-bottom: 1rem;
    border-bottom: 2px solid #007bff;
    display: inline-block;
    padding-bottom: 5px;
  }
  
  /* Liste de méthodologie */
  .methodology-list {
    list-style: none;
    padding: 0;
  }
  .methodology-item {
    background: rgba(0, 123, 255, 0.05);
    border: 1px solid rgba(0, 123, 255, 0.2);
    margin-bottom: 10px;
    padding: 15px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    gap: 15px;
  }
  
  /* Lien GitHub stylisé */
  .github-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: #24292e;
    color: white !important;
    padding: 10px 20px;
    border-radius: 5px;
    text-decoration: none !important;
    transition: background 0.3s;
    margin-top: 20px;
  }
  .github-btn:hover {
    background: #555;
  }
</style>

<div class="pro-header">📝 Résumé Exécutif</div>

Le projet **SharePy** est une plateforme de partage de fichiers conteneurisée (type mini-Dropbox) qui a servi de base à un audit de sécurité complet. L'objectif était d'identifier, exploiter, puis corriger **15 vulnérabilités de configuration** majeures basées sur le standard **OWASP A02:2025 (Cryptographic Failures)**.

### Résultats Principaux
* **Audit Initial** : 15 failles détectées (6 critiques, 5 moyennes, 4 faibles).
* **Impact Global** : Risque d'exposition totale des données utilisateurs et compromission du serveur.
* **Résultat Final** : Sécurisation à 100% validée par un script de test automatisé.

---

<div class="pro-header">🛡️ Méthodologie (Red Team vs Blue Team)</div>

Le projet a été mené selon une approche structurée en trois phases :

<ul class="methodology-list">
  <li class="methodology-item">
    <i class="fas fa-user-secret fa-2x" style="color:#ff4d4d"></i>
    <div>
      <strong>Phase 1 : Red Team (Offensive)</strong><br>
      Recherche de vulnérabilités, scan de ports, et exploitation manuelle des failles de configuration.
    </div>
  </li>
  <li class="methodology-item">
    <i class="fas fa-shield-alt fa-2x" style="color:#007bff"></i>
    <div>
      <strong>Phase 2 : Blue Team (Défensive)</strong><br>
      Application des correctifs, durcissement des configurations (Hardening) et isolation réseau.
    </div>
  </li>
  <li class="methodology-item">
    <i class="fas fa-check-circle fa-2x" style="color:#28a745"></i>
    <div>
      <strong>Phase 3 : Validation & Documentation</strong><br>
      Développement d'un script Python de validation et rédaction du rapport final.
    </div>
  </li>
</ul>

---

<div class="pro-header">🔍 Analyse Détaillée & Correction des Vulnérabilités (Top 15)</div>

Voici une analyse approfondie des points critiques extraits de mon rapport d'audit. Chaque carte détaille la faille, son impact et la correction appliquée.

<div class="analysis-card">
  <h3 style="margin-top:0"><span class="vuln-badge severity-high">HIGH</span> M1 : Mots de passe codés en dur</h3>
  <p><strong>Description :</strong> Les identifiants de base de données étaient inscrits directement dans le fichier `docker-compose.yml`.</p>
  <p><strong>Impact :</strong> Un attaquant ayant accès au système de fichiers pourrait compromettre l'intégralité de la base de données.</p>
  <p><strong>Correction :</strong> Migration des secrets vers des variables d'environnement sécurisées (`.env`) et utilisation de Docker Secrets.</p>
</div>

<div class="analysis-card">
  <h3 style="margin-top:0"><span class="vuln-badge severity-high">HIGH</span> M15 : Secret JWT faible</h3>
  <p><strong>Description :</strong> La clé de signature des tokens JWT était une chaîne de caractères simple et prévisible.</p>
  <p><strong>Exploitation :</strong> Brute-force du secret pour forger des jetons administrateur et usurper des identités.</p>
  <p><strong>Correction :</strong> Génération d'un secret de 512 bits via `openssl` et stockage sécurisé.</p>
</div>

<div class="analysis-card">
  <h3 style="margin-top:0"><span class="vuln-badge severity-medium">MEDIUM</span> M7 : CORS avec Wildcard (*)</h3>
  <p><strong>Description :</strong> La politique CORS autorisait toutes les origines (`*`).</p>
  <p><strong>Correction :</strong> Restriction des origines autorisées au domaine spécifique de l'application.</p>
</div>

<div class="analysis-card">
  <h3 style="margin-top:0"><span class="vuln-badge severity-high">HIGH</span> M5 : Adminer accessible publiquement</h3>
  <p><strong>Description :</strong> L'interface de gestion de base de données Adminer était exposée sur Internet.</p>
  <p><strong>Correction :</strong> Retrait de l'exposition du port 8080 et restriction de l'accès à l'hôte local via le réseau Docker.</p>
</div>

---


<div class="pro-header">🚀 Script de Validation Automatisée</div>

Pour clore le projet et garantir la non-régression de la sécurité, j'ai développé un script **Python** qui effectue des tests après chaque déploiement.


<div class="pro-header">🔗 Voir le Projet</div>

<a href="https://github.com/sssyouna/project_final_cyber/tree/secure/sharepy" class="github-btn" target="_blank">
  <i class="fab fa-github fa-lg"></i>
  Voir le Projet sur GitHub
</a>