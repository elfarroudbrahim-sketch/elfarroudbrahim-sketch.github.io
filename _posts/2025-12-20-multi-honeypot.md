---
title: "Multi-Honeypot Réseau & Analyse ELK Stack"
author: Brahim El Farroud
date: 2025-12-20 10:00:00 +0100
categories: [Projects, Cybersecurity]
tags: [Honeypot, ELK Stack, Docker, AppArmor, Python]
image:
  path: /assets/img/posts/honeypot-banner.png
  alt: "Architecture Multi-Honeypot"
---

<style>
  /* --- Style Pro Cybersécurité --- */
  .threat-card {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    padding: 20px;
    border-radius: 12px;
    margin: 20px 0;
    transition: all 0.3s ease;
  }
  .threat-card:hover {
    border-color: #28a745;
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(40,167,69,0.1);
  }
  .tech-badge-cyan {
    background: rgba(0, 255, 255, 0.05);
    color: #00bcd4;
    border: 1px solid #00bcd4;
    padding: 3px 10px;
    border-radius: 15px;
    font-size: 0.8rem;
    font-weight: bold;
  }
  .shield-header {
    font-size: 1.5rem;
    font-weight: 700;
    color: #28a745;
    margin-top: 2rem;
    display: flex;
    align-items: center;
    gap: 10px;
  }
</style>

<div class="threat-card">
  <h2 style="margin-top:0">🛡️ Objectif du Projet</h2>
  Développement d'un écosystème de <strong>déception réseau</strong> conçu pour capturer et analyser les vecteurs d'attaque en temps réel. Le système simule des services critiques vulnérables tout en garantissant un isolement total de l'attaquant pour protéger l'infrastructure hôte.
</div>

---

<div class="shield-header"><i class="fas fa-network-wired"></i> Architecture Multi-Services</div>

Le système déploie plusieurs capteurs spécialisés orchestrés via **Docker** :

* **Honeypot SSH** : Capture des tentatives de brute-force et des commandes exécutées dans un shell restreint.
* **Honeypot HTTP** : Simulation d'une interface web pour capturer les injections SQL et les tentatives de path traversal.
* **Honeypot FTP** : Surveillance des transferts de fichiers malveillants.


---

<div class="shield-header"><i class="fas fa-user-shield"></i> Confinement & Hardening</div>

Pour éviter qu'un attaquant ne s'évade du conteneur (*Container Escape*), plusieurs couches de sécurité ont été implémentées :

1.  **AppArmor & Seccomp** : Profils personnalisés pour restreindre les appels système (syscalls) autorisés.
2.  **Réseaux Isolés** : Utilisation de bridges Docker dédiés sans accès au réseau interne de l'organisation.
3.  **Moindre Privilège** : Chaque service s'exécute avec un utilisateur non-root.

---

<div class="shield-header"><i class="fas fa-chart-pie"></i> Analyse de Données avec ELK Stack</div>

L'intelligence du projet réside dans la centralisation des logs pour une analyse comportementale.

![Structure du projet sur GitHub](/assets/img/posts/github-honeypot.png)
<p style="text-align: center; font-style: italic; font-size: 0.85rem;">Structure du dépôt : Scripts Python de simulation et fichiers de configuration Docker</p>

* **Elasticsearch** : Indexation massive des logs d'attaques.
* **Logstash** : Parsing et enrichissement des données (Géo-IP pour localiser les attaquants).
* **Kibana** : Tableaux de bord affichant les payloads les plus utilisés et la provenance géographique des menaces.


---

<div class="shield-header"><i class="fas fa-terminal"></i> Implémentation Technique</div>

Le backend est développé en **Python** pour simuler les réponses des protocoles de manière réaliste.

```python
# Extrait du script de capture SSH (ssh_honeypot.py)
def handle_connection(client_socket):
    # Envoi de la bannière de bienvenue simulée
    client_socket.send(b"SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.1\n")
    # Log de l'adresse IP et des credentials tentés
    # ...