# Gestion et suivi des équipements informatiques

## GLPI : Qu'est-ce que c'est ?  

GLPI (**Gestion Libre de Parc Informatique**) est un outil open-source qui permet de gérer efficacement les infrastructures informatiques.  
Il offre une vision centralisée et complète de l'ensemble des équipements et des processus associés, tout en facilitant la maintenance et le suivi.  

### Fonctionnalités principales
1. **Gérance et suivi** : GLPI permet de suivre en temps réel l'état et l'utilisation des équipements informatiques d'une organisation (ordinateurs, serveurs, périphériques, etc.).  
2. **Remontée automatique des équipements** :  
   - Pour simplifier le suivi, un **agent** doit être installé sur chaque poste informatique. Cet agent communique automatiquement avec le serveur GLPI pour remonter les informations sur le matériel (comme le processeur, la RAM, le stockage, etc.) et les logiciels installés.  
3. **Gestion manuelle pour les périphériques non compatibles** :  
   - Certains équipements (comme les écrans, scanners ou imprimantes sans connexion réseau) ne peuvent pas remonter d'informations automatiquement. Ces périphériques doivent être **saisis manuellement** dans GLPI.  
   - **Astuce pour simplifier la gestion :** Créer un fichier CSV regroupant toutes les informations nécessaires (marque, modèle, numéro de série, emplacement, etc.) et l'importer directement dans GLPI.  

### Inventaire automatisé avec **OCS Inventory**  
- **OCS Inventory** est un outil complémentaire à GLPI qui permet d’automatiser la collecte des données sur le matériel et les logiciels d'un parc informatique.  
- Il scanne les postes et remonte les données vers GLPI, ce qui élimine la nécessité de saisir manuellement chaque élément.  

---

## Gestion des tickets dans GLPI

GLPI propose une gestion efficace des **incidents et demandes** grâce à un système de tickets.  
- Les utilisateurs peuvent créer des tickets lorsqu’ils rencontrent des anomalies ou des problèmes techniques.  
- Les techniciens peuvent alors prendre en charge ces tickets, les traiter et les clôturer une fois résolus.

### Principe d'escalade
Le **principe d'escalade** est utilisé pour garantir que les problèmes complexes sont traités au bon niveau :  
1. **Premier niveau** : Problèmes simples résolus par le service IT interne.  
2. Si non résolus, les problèmes sont **escaladés** au niveau supérieur (par exemple, une société de maintenance externe ou un prestataire spécialisé).  
3. Ce processus se poursuit jusqu'à ce que le problème soit résolu.  

---

## Suivi effectué par GLPI  

GLPI ne se limite pas à la gestion des équipements et des tickets. Il propose également des fonctionnalités avancées pour suivre :  

- **Les licences** : Assurez-vous que tous les logiciels sont conformes et sous licence valide.  
- **Le budget** : Planifiez les dépenses liées au matériel et au logiciel, avec des prévisions sur plusieurs années (exemple : 3ᵉ ou 4ᵉ année).  
- **Les fournisseurs** : Gardez une trace des fournisseurs pour un suivi rapide des commandes et des contrats.  
- **Les contrats de maintenance/support** :  
  - GLPI envoie des alertes avant la fin des contrats pour permettre le renouvellement.  
  - Évitez les interruptions de maintenance ou de support technique grâce à ces rappels automatiques.  
- **Les documents** : Stockez et organisez les procédures internes, manuels, guides, etc.  
- **L'annuaire téléphonique** : Centralisez les informations de contact pour tous les intervenants (internes et externes).  
- **Les certificats** : Suivez les certificats de sécurité (SSL, etc.) et recevez des alertes avant leur expiration.  
- **Les bases de données** : Gérez les informations concernant vos bases de données et leurs accès.  
- **Les domaines** : Recevez des rappels pour renouveler vos noms de domaine avant expiration.  
- **Les garanties matérielles** : GLPI alerte avant la fin des garanties pour vous permettre de planifier les interventions ou remplacements.

---

# Les outils intégrés à GLPI

### Modules complémentaires
GLPI intègre plusieurs modules pour aller au-delà de la simple gestion informatique :  

- **Projets** : Suivez et gérez des projets IT (mises à jour, migrations, nouvelles installations).  
- **Notes** : Prenez et partagez des notes entre techniciens pour garder une trace des actions ou idées importantes.  
- **Base de connaissances** :  
  - Consultez les solutions d’incidents passés pour gagner du temps sur des problèmes similaires. 
	déal pour documenter les résolutions de problèmes complexes.  
- **Réservation de matériel** :  
  - Planifiez et gérez les réservations d’équipements (voitures, téléphones, ordinateurs, etc.).  
  - Utilisez un **planning de réservation** pour éviter les conflits d’utilisation.  

### Accès des utilisateurs
- Les utilisateurs finaux n'ont accès qu'à la section **Assistance**, où ils peuvent :  
  - Créer des tickets pour signaler des problèmes.  
  - Suivre l'avancement de leurs tickets.  

---

# VMware : Résolution des problèmes de connexion

VMware est couramment utilisé pour créer des environnements virtuels, mais il peut parfois y avoir des problèmes de connexion réseau. Voici les étapes pour les résoudre :  

### Étapes pour corriger la connexion réseau
1. Supprimer toutes les **cartes réseau existantes** dans VMware.  
2. Créer un nouveau réseau virtuel nommé **VMNET 0**.  
3. Affecter **VMNET 0** à **NAT** (Network Address Translation).  
4. Vérifier que l’option **DHCP** est activée (case cochée).  
5. Configurer l’adresse du réseau NAT : `10.10.10`.  
6. Appliquer les modifications.  

### Configuration des machines virtuelles
- Lorsque vous configurez une machine virtuelle, choisissez **Custom** dans les paramètres réseau.  
- Sélectionnez ensuite **VMNAT0 (NAT)** comme réseau utilisé.  

---

## Configuration IP statique pour Linux  

Pour configurer une adresse IP statique dans une machine virtuelle sous Linux, modifiez le fichier :  
`/etc/network/interfaces`.  

Voici un exemple de configuration :  

```plaintext
# Configuration réseau statique
iface ens33 = carte réseau
address : 10.10.10.100
netmask : 255.255.255.0
gateway : 10.10.10.2
dns-nameservers : 8.8.8.8 4.4.4.4
