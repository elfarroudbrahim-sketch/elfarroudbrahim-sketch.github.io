---
layout: page
title: About
icon: fas fa-info-circle
order: 1
---

<style>
  .about-container {
    color: var(--main-text-color);
    line-height: 1.7;
  }

  .intro-card {
    background: var(--main-bg);
    border: 1px solid var(--main-border-color);
    border-radius: 20px;
    padding: 2.5rem;
    margin-bottom: 3rem;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  }

  [data-mode='dark'] .intro-card {
    background: linear-gradient(145deg, #1e1e22, #121214);
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  }

  .intro-header {
    font-size: 1.8rem;
    font-weight: 800;
    color: var(--heading-color);
    margin-bottom: 1rem;
  }

  .section-title {
    font-size: 1.6rem;
    font-weight: 700;
    margin: 3rem 0 1.5rem;
    display: flex;
    align-items: center;
    gap: 15px;
    color: var(--heading-color);
  }

  .section-title::after {
    content: "";
    height: 1px;
    background: var(--main-border-color);
    flex-grow: 1;
  }

  .skills-grid, .cert-grid {
    display: grid;
    gap: 1.5rem;
  }

  .skills-grid { grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); }
  .cert-grid { grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); }

  .skill-column, .cert-card {
    background: var(--card-bg);
    border: 1px solid var(--main-border-color);
    border-radius: 16px;
    padding: 1.5rem;
    transition: all 0.3s ease;
  }

  .skill-column:hover, .cert-card:hover {
    border-color: #007bff;
    transform: translateY(-5px);
  }

  .column-header, .cert-card i {
    color: #007bff;
    margin-bottom: 1.2rem;
    font-weight: 600;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    background: var(--checkbox-checked-bg);
    opacity: 0.8;
    border: 1px solid var(--main-border-color);
    color: var(--main-text-color);
    padding: 5px 12px;
    border-radius: 8px;
    font-size: 0.85rem;
  }

  .cert-name {
    font-weight: 600;
    display: block;
    color: var(--heading-color);
  }

  .cert-issuer {
    font-size: 0.75rem;
    color: var(--text-muted-color);
  }
</style>

<div class="about-container">
  
  <div class="intro-card">
    <div class="intro-header">Bonjour, je suis Brahim El Farroud</div>
    <p>
      Étudiant en 2ème année d'ingénierie en <strong>Développement Numérique et Cybersécurité</strong> à l'ENSA de Fès. 
      Passionné par la sécurité offensive et défensive, je me forme sur des environnements complexes allant du <strong>Pentesting Web</strong> au <strong>durcissement de systèmes</strong>. 
    </p>
    <p>
      Mon objectif est d'allier expertise technique en développement et innovation pour protéger les infrastructures critiques.
    </p>
  </div>

  <h2 class="section-title"><i class="fas fa-certificate"></i> Certifications</h2>
  <div class="cert-grid">
    <div class="cert-card">
      <i class="fas fa-user-secret"></i>
      <span class="cert-name">Junior Penetration Tester Path</span>
      <span class="cert-issuer">TryHackMe</span>
    </div>
    <div class="cert-card">
      <i class="fas fa-plug"></i>
      <span class="cert-name">API Penetration Testing</span>
      <span class="cert-issuer">APIsec University</span>
    </div>
    <div class="cert-card">
      <i class="fas fa-shield-alt"></i>
      <span class="cert-name">Introduction to Cybersecurity</span>
      <span class="cert-issuer">Cisco</span>
    </div>
    <div class="cert-card">
      <i class="fas fa-database"></i>
      <span class="cert-name">Oracle SQL</span>
      <span class="cert-issuer">Database Administration</span>
    </div>
    <div class="cert-card">
      <i class="fas fa-lock"></i>
      <span class="cert-name">Cybersecurity Fundamentals</span>
      <span class="cert-issuer">Udemy Professional</span>
    </div>
  </div>

  <h2 class="section-title"><i class="fas fa-laptop-code"></i> Skills</h2>
  <div class="skills-grid">
    <div class="skill-column">
      <div class="column-header"><i class="fas fa-biohazard"></i> Cybersecurity</div>
      <div class="skill-tags">
        <span class="skill-tag">Pentesting Web/Réseau</span>
        <span class="skill-tag">OWASP Top 10</span>
        <span class="skill-tag">Splunk & Suricata</span>
        <span class="skill-tag">Vulnerability Analysis</span>
        <span class="skill-tag">Active Directory</span>
      </div>
    </div>

    <div class="skill-column">
      <div class="column-header"><i class="fas fa-code"></i> Development</div>
      <div class="skill-tags">
        <span class="skill-tag">Python</span>
        <span class="skill-tag">Java</span>
        <span class="skill-tag">PHP (Laravel)</span>
        <span class="skill-tag">C / C++ / C#</span>
        <span class="skill-tag">JavaScript / Next.js</span>
        <span class="skill-tag">Dart</span>
      </div>
    </div>

    <div class="skill-column">
      <div class="column-header"><i class="fas fa-tools"></i> Tools</div>
      <div class="skill-tags">
        <span class="skill-tag">Linux (Kali/Ubuntu)</span>
        <span class="skill-tag">Docker</span>
        <span class="skill-tag">TCP/IP & VLAN</span>
        <span class="skill-tag">SQL / PostgreSQL</span>
        <span class="skill-tag">MATLAB</span>
        <span class="skill-tag">Figma / XML</span>
      </div>
    </div>
  </div>
</div>