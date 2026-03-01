---
title: "Administration Active Directory & Migration : De 2003 à 2019"
author: Brahim El Farroud
date: 2025-10-10 09:00:00 +0100
categories: [Projects, Infrastructure]
tags: [Active Directory, Windows Server, GPO, Migration, FSMO]
image:
  path: /assets/img/posts/ad-migration-banner.png
  alt: "Schéma de migration Active Directory"
---

<style>
  /* --- Style Professionnel pour Infrastructure --- */
  .step-card {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    border-radius: 15px;
    padding: 20px;
    margin-bottom: 20px;
    transition: all 0.3s ease;
  }
  .step-card:hover {
    border-color: #28a745;
    transform: translateX(10px);
    box-shadow: 0 5px 15px rgba(40, 167, 69, 0.1);
  }
  .phase-badge {
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: bold;
    color: white;
    margin-bottom: 10px;
    display: inline-block;
  }
  .phase-setup { background: #6c757d; }
  .phase-migration { background: #28a745; }
  
  .tech-label {
    font-family: monospace;
    background: rgba(0,0,0,0.1);
    padding: 2px 5px;
    border-radius: 4px;
  }
</style>

<div class="step-card">
  <h2>📖 Contexte du Stage</h2>
  Effectué au <strong>Tribunal de Première Instance</strong>, ce projet portait sur la modernisation d'une infrastructure réseau critique conformément à la <strong>Loi 38.15</strong>. L'objectif était de garantir la pérennité des services informatiques et de la mise en œuvre par intérim via une migration orchestrée des contrôleurs de domaine.
</div>

---

##  Phase 1 : Préparation de l'Environnement

Avant la migration, une infrastructure de base a été reconstruite pour simuler l'environnement de production.

* **Virtualisation** : Création de machines virtuelles pour isoler les différents serveurs et postes clients Windows 10.
* **Contrôleur de Domaine Initial** : Installation de <span class="tech-label">Windows Server 2003</span>, promotion en tant que DC et configuration du service **DHCP** pour la gestion dynamique des adresses.
* **Organisation de l'Annuaire** : Création d'Unités d'Organisation (OU) et application de **GPO** (Group Policy Objects) pour restreindre et sécuriser les accès utilisateurs.



---

##  Phase 2 : Migration vers Windows Server 2012

Le passage direct de 2003 à 2019 étant impossible, une étape intermédiaire via la version 2012 a été nécessaire pour assurer la compatibilité du niveau fonctionnel de la forêt.

<div class="step-card">
  <span class="phase-badge phase-migration">MIGRATION STEP 1</span>
  <h3>Transfert des Rôles FSMO</h3>
  <ul>
    <li>Intégration du serveur 2012 au domaine existant.</li>
    <li>Promotion du serveur en tant que contrôleur de domaine supplémentaire.</li>
    <li><strong>Action Critique</strong> : Transfert des 5 rôles <span class="tech-label">FSMO</span> (Schema, Domain Naming, PDC, RID, Infrastructure) du serveur 2003 vers le 2012.</li>
  </ul>
</div>

---

##  Phase 3 : Migration Finale vers Windows Server 2019

Une fois l'infrastructure stabilisée sous 2012, la dernière étape consistait à migrer vers la version moderne 2019.



1.  **Installation & Promotion** : Déploiement du serveur 2019 et promotion en tant que nouveau DC.
2.  **Transfert Final** : Migration des rôles FSMO vers le serveur 2019 pour le rendre maître de la forêt.
3.  **Vérification Autonome** : Retrait progressif des anciens serveurs (2003 et 2012) et validation de la réplication DNS et Active Directory sur le serveur 2019 seul.

---

##  Termes Techniques Clés

* **Rôles FSMO** : Fonctions spécifiques indispensables au bon fonctionnement d'un domaine Active Directory.
* **GPO** : Stratégies permettant de configurer les paramètres de sécurité et de bureau de manière centralisée.
* **Niveau Fonctionnel** : Définit les capacités et les versions de serveurs autorisées dans la forêt Active Directory.

---


---

