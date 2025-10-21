
Les deux termes suivants sont couramment utilisés pour décrire le moment où une menace est détectée :

### **Zero-day**

Parfois également appelé **attaque zero-day**, **menace zero-day** ou **exploit zero-day**.  
Ce terme désigne **le jour où une vulnérabilité inconnue est découverte par l’éditeur** du logiciel.  
Il fait référence au **temps dont dispose l’éditeur** pour corriger cette vulnérabilité : **zéro jour**, autrement dit **aucun délai**.

### **Zero-hour**

C’est **le moment exact où l’exploitation de la vulnérabilité est détectée** (c’est-à-dire lorsqu’un attaquant commence à l’utiliser).

---

Un réseau reste **vulnérable entre le moment du zero-day et celui où un correctif est développé** par l’éditeur.

Dans l’exemple illustré par la figure, un éditeur de logiciel a pris connaissance d’une **nouvelle vulnérabilité**.  
Le logiciel peut être exploité **jusqu’à ce qu’un patch (correctif) soit publié** pour corriger cette faille.  
Remarquez que dans cet exemple, il a fallu **plusieurs jours et plusieurs mises à jour logicielles** pour **atténuer la menace**.


---

## 1. Mesures Préventives

1. **Gestion rigoureuse des correctifs (Patch Management)**
    
    - Maintenir à jour tous les systèmes d’exploitation, applications et firmwares.        
    - Automatiser l’inventaire et la distribution des correctifs.        
    - Envisager un mécanisme de « virtual patching » (patchs virtuels au niveau du pare-feu/IPS) pour neutraliser rapidement une vulnérabilité zéro-day avant la sortie officielle du correctif.
    
2. **Segmentation et micro-segmentation du réseau**
    
    - Limiter les communications inter-segments au strict nécessaire (principe du moindre privilège).        
    - Isoler les équipements critiques (serveurs, systèmes industriels) des postes utilisateurs et d’Internet.        
    - Mettre en place des VLANs et des zones de sécurité (DMZ).
    
3. **Contrôle d’accès et authentification forte**
    
    - Adopter l’authentification multifactorielle (MFA) pour l’accès aux ressources sensibles.        
    - Mettre en œuvre un NAC (Network Access Control) pour valider la conformité des terminaux avant connexion.        
    - Utiliser le principe de moindre privilège pour les comptes utilisateurs et service accounts.
    
4. **Durcissement (« hardening ») des systèmes**
    
    - Désactiver tous les services et ports non utilisés.        
    - Appliquer les bonnes pratiques de configuration (CIS Benchmarks, STIGs, etc.).        
    - Mettre en place des listes blanches d’applications sur les postes critiques (application whitelisting).
    

---

## 2. Mesures Détectives

1. **Systèmes de détection/prévention d’intrusion (IDS/IPS)**
    
    - Utiliser des signatures mises à jour pour détecter automatiquement les exploits connus et virtuellement « patcher » les attaques émergentes.        
    - Compléter avec des techniques heuristiques et d’analyse comportementale pour les menaces inconnues.
    
2. **Monitoring et analyse du trafic**
    
    - Déployer des solutions de Network Traffic Analysis (NTA) et de Security Information and Event Management (SIEM).        
    - Corréler les logs de pare-feux, serveurs, endpoints et applications pour repérer les comportements anormaux.
    
3. **Endpoint Detection and Response (EDR)**
    
    - Installer sur chaque poste et serveur un agent EDR capable d’identifier et bloquer en temps réel les malwares et attaques de type « fileless » ou zero-day.        
    - Centraliser les alertes pour investigations rapides.
    
4. **Sandboxing et analyse dynamique**
    
    - Exécuter automatiquement les fichiers suspects dans un environnement isolé pour observer leur comportement (détection d’exfiltration, d’exploits mémoires, etc.).
    

---

## 3. Mesures Correctives et Adaptatives

1. **Threat Intelligence et partage de renseignements**
    
    - Souscrire à des flux de threat intelligence (CTI) pour recevoir des indicateurs de compromission (IoC) et informations sur les attaques zero-day en cours.        
    - Participer à des communities of interest (ISAC, CERT locaux) pour échanger sur les menaces émergentes.
    
2. **Plans de réponse aux incidents (IRP) et exercices réguliers**
    
    - Documenter les procédures de containment, d’éradication et de reprise d’activité.        
    - Organiser des simulations (table-top exercises, red team/blue team) pour éprouver la réactivité de l’équipe.
        
3. **Backups et plans de reprise d’activité (PRA/DRP)**
    
    - Mettre en place des sauvegardes régulières, chiffrées et testées.        
    - Conserver des copies hors-site ou dans le cloud pour se prémunir contre les ransomwares et attaques destructrices.
        
4. **Mises à jour continues et audits**
    
    - Planifier des scans de vulnérabilités fréquents (automatisés et manuels).        
    - Réaliser des audits de sécurité et des tests d’intrusion (pentests) périodiques.
        

---

### Pourquoi cette approche protège-t-elle des zero-day ?

- **Virtual patching et signatures dynamiques** dans les IPS/IDS réduisent la fenêtre de vulnérabilité (entre « zero-day » et la sortie officielle du correctif).    
- **Analyse comportementale et sandboxing** détectent les attaques même sans signature préexistante.    
- La **défense en profondeur** (préventive, détective, corrective) limite le risque qu’une faille non connue à un point du réseau ne provoque un compromis global.


![[Pasted image 20250511181400.png]]

En combinant ces couches de sécurité, vous diminuez drastiquement la probabilité qu’un attaquant exploite avec succès une vulnérabilité zero-day, tout en étant capable de réagir rapidement si une menace nouvelle apparaît.


Baiting

An attacker has just retrieved hard copies of recently outdated device configuration files from a trash bin.

Dumpster diving

A person claiming to be from your heating and ventilation contractor asks you if you could let him into a secure area.

Impersonation

You received an email from your bank stating that your account has been compromised and that you should click an enclosed link to rectify the problem. When you click, you unknowingly just installed malware on your device.

Phishing

Your “bank” calls you to say your account may be compromised and they would like to confirm your identity by requesting your personal and financial data.

Pretexting

You notice a fellow employee purposely overlooking your supervisor’s shoulder as they are entering their login credentials.

Shoulder surfing

You received a survey in an email for a cool free t-shirt in which you have to provide personal identifiable information.

Something for Something

An attacker sends malicious emails containing harmful links, malware, or deceptive content to a large number of random individuals.

Spam

An attacker has created a targeted phishing attack tailored specifically for the chief executive officer of a large organization.

Spear phishing

A person you have never seen before has quickly followed you into a secure building entrance saying that he forgot his security badge.

Tailgating