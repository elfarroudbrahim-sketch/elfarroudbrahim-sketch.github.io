---
title: "Plateforme CTF Full-Stack : Challenges & Chatbot IA"
author: Brahim El Farroud
date: 2025-11-15 14:00:00 +0100
categories: [Projects, Development]
tags: [Laravel, PHP, Cybersecurity, AI, CTF]
image:
  path: /assets/img/posts/ctf-platform-banner.jpeg
  alt: "Interface de la plateforme CTF"
---

<style>
  /* --- Style Moderne et Gaming --- */
  .ctf-card {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    border-radius: 15px;
    padding: 25px;
    margin-bottom: 25px;
    transition: all 0.3s ease;
  }
  .ctf-card:hover {
    border-color: #fd7e14;
    box-shadow: 0 8px 25px rgba(253, 126, 20, 0.15);
  }
  .tech-badge {
    display: inline-block;
    padding: 4px 12px;
    border-radius: 8px;
    font-size: 0.8rem;
    font-weight: bold;
    margin-right: 10px;
    border: 1px solid rgba(253, 126, 20, 0.3);
    color: #fd7e14;
    background: rgba(253, 126, 20, 0.05);
  }
  .ai-section {
    border-left: 4px solid #8e44ad;
    padding-left: 20px;
    background: rgba(142, 68, 173, 0.05);
    border-radius: 0 10px 10px 0;
    padding: 20px;
  }
</style>

<div class="ctf-card">
  <h2>🎮 Présentation de la Plateforme</h2>
  Développement d'une application web de type <strong>Capture The Flag (CTF)</strong> complète, permettant aux utilisateurs de s'affronter sur des épreuves de cybersécurité. Le site intègre un système de scoring dynamique, une gestion de profil et un assistant intelligent pour accompagner les participants.
</div>

---

## 💻 Architecture Full-Stack

Le projet repose sur une stack moderne garantissant performance et sécurité :

* **Backend (Laravel)** : Utilisation de PHP pour la logique métier, la gestion des sessions et la protection native contre les failles SQLi, CSRF et XSS.
* **Frontend** : Interface utilisateur responsive réalisée avec HTML, CSS et JavaScript, utilisant **Bootstrap** pour un design épuré et fonctionnel.
* **Base de données (MySQL/PostgreSQL)** : Stockage sécurisé des utilisateurs, des flags et du classement en temps réel.



---

## 🛡️ Fonctionnalités & Sécurité

La plateforme a été conçue avec une attention particulière portée à la robustesse :

* **Moteur de Challenges** : Catégories variées (Web, Crypto, Forensics) avec validation de flags côté serveur.
* **Système de Scoring** : Algorithme calculant les points en fonction de la difficulté et du temps de résolution.
* **Sécurité Applicative** : Chiffrement des mots de passe avec Bcrypt et validation stricte des entrées utilisateurs.

---

<div class="ai-section">
  <h2><i class="fas fa-robot"></i> Innovation : Chatbot d'Assistance IA</h2>
  L'une des pièces maîtresses du projet est l'intégration d'un <strong>Chatbot</strong> agissant comme un mentor :
  <ul>
    <li><strong>Aide Contextuelle</strong> : Le chatbot analyse la progression de l'utilisateur pour offrir des indices (hints) sans révéler la solution.</li>
    <li><strong>Engagement</strong> : Améliore la rétention des débutants en réduisant la frustration face aux challenges complexes.</li>
    <li><strong>Traitement du Langage</strong> : Utilisation de scripts pour traiter les requêtes et retourner des réponses pertinentes basées sur la base de connaissances du CTF.</li>
  </ul>
</div>



---

## 🚀 Impact & Apprentissage

Ce projet m'a permis de fusionner mes deux passions : le développement logiciel et la cybersécurité. J'ai pu approfondir mes compétences en **Secure Coding** et explorer les possibilités offertes par l'IA pour l'éducation en cybersécurité.

---

### 🔗 Liens du Projet

