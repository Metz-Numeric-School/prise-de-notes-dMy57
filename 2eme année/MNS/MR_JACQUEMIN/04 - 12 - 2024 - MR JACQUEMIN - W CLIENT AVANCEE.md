## Introduction au déploiement de Windows

Installation postes neuf :  (duplication "image" multiposte pour éviter de paramétrer cheque pc)

Serveur de déploiement (WDS) 

Contexte d'utilisation : 
- renouvellement parc
- ajout de nv postes
- Réinstallation après cyberattaque ou dysfonctionnement critique 

Installation manuelle : 
- Adapté pour des besoins ponctuels
- Longue et sujette à des erreurs humaines
- Pas scalable

Clonage systèmes :
* Création image d'un Windows configuré (modèle)
* Déploiement tapide sur plusieurs machines
* Limité aux config matérielles similaires

Déploiement automatisé : 
* Utilisation des fichiers de réponses (Unattend.xml)
* Automatisation du processus
* Idéal pour les parc info hétérogène

Déploiement centralisé : 
* Basé sur des serveurs tel que W Deployement Services (WDS) ou SCCM
* Gestion des installations via le réseau
* Convient aux grosses entreprises avec des parc info important

![[Pasted image 20241204133611.png]]

Outils Microsoft : 
- Windows PE (WinPE)
- DISM
- Unattend.xml
- Sysprep
- ADK

**Windows ADK = Assessment and Deployment Kit = Kit de déploiement et d'évaluation Windows**
(permet d'installer les autres outils)

**WinPE = Mini OS conçu par Microsoft**
(pour installer ou dépanner Windows) - s'exécute directement depuis USB ou un CD sans nécessiter d'installation sur le DD (Windows très allégé)

**DISM = Deployment Image Servicing and Management **
(outil en ligne de commande pour les fichiers .WIM) 
- Capturer une image système Windows
- Modifier une image pour add ou delete une fonctionnalité
- Déployer une image sur une nvl machine

**Unattend.XML :**
- Fichier de réponse XML utilisé pour automatiser l'installation de Windows en répondant aux invites utilisateur pdnt le processus d'installation 

4 paramètre principaux : 
- WindowsPE : configure les paramètre initiaux, comme la partition de disque
- OfflineServicing : Ajoute des MAJ et pilotes pdnt l'installation
- Specialize : Configure les paramètre réseau et de domaine
- OOBE (Out of box Experience) Définit les paramètres utilisateurs comme le compte admin et le fuseau horaire

**Sysprep :**
- Avant de déployer une image Windows sur de nv PC, vous devez d'abord généraliser cette image. La généralisation de l'image supprime les informations spécifiques à l'ordinateur, telles que les pilotes installés et l'identificateur de sécurité (SID) de l'ordinateur

- Utilisation de sysprep seul ou sysprep avec un fichier de réponses Unattend.XML pour généraliser votre image et le préparer au déploiement 
## CREATION CLE BOOT

Avec WinPE :


**Caractéristiques principales :**
- Fournit un environnement temporaire pour préparer une machine
- Permet de capturer ou déployer des images systèmes
- Inclut des outils pour diag et réparer des systèmes Windows

**Cas d’utilisation :**
- Pré-installation de Windows sur des machines neuves 
- Clonage et déploiement d'images système 
- Récupération de données ou réparation après une panne critique

**Possibilité de :**
- Configurer votre disque dur avant d’installer Windows. 
- Installer Windows à l’aide d’applications ou de scripts à partir d’un réseau ou d’un lecteur local. 
- Capturer et appliquer des images Windows. 
- Modifier le système d’exploitation Windows lorsqu’il n’est pas en cours d’exécution. 
- Configurer des outils de récupération automatique. 
- Récupérer des données à partir d’appareils non démarrables. 
- Ajoutez votre propre interpréteur de commandes ou votre interface graphique personnalisée pour automatiser ce type de tâches.

**Commandes utiles :**
- diskpart : permet de gérer les partitions de disque
- wmic : Fournit des infos systèmes sur le matériel
- dism : Sert à gérer les images windows (dans WinPE)
- notepad : Ouvre un éditeur de texte
- Regedit : Lane d'éditeur de systèmes
- ver : Connaitre la version du systèmes

## Clonage et gestion d'image 

**Clonage :** 
- Dupliquer un OS et ses configurations pour les reproduire sur plusieurs machines
- Cela permet un gain de temps considérables dans les environnements d'entreprise ou des déploiement à grande échelle sont nécessaires

**Avantages :** 
* Réduction du temps d'installation et de config
* Uniformité des environnements de travail
* Simplification des MAJ ou migrations 

**Format WIM =**  Windows Imaging Fomart
- Format d'image utilisé par Microsoft pour capturer, modifier et déployer des OS
- Permet de stocker plusieurs images dans un seul fichier (exemple : différentes éditions de Windows)
- Offre une compression efficace pour économiser de l'espace disque

**DISM :**
- Deployment Image Servicing and Management = outil en ligne de cmd pour manipuler les fichiers WIM 
- Permet de capturer une image d'un OS Windows
- Modifier une image pour ajouter ou supprimer une fonctionnalités 
- Déployer une image sur une nv machine 

![[Pasted image 20241204135726.png]]

**Capture d'une image :** 
- Configurer une machine Windows avec les paramètres et logiciels souhaité 
- Capturer son image avec DISM pour l'obtenir au format .wim


## Utilisation du fichier unattend.xml et de SYSPREP

**unattend.xml** est un fichier de réponse XML utilisé pour automatiser l'installation de Windows en répondant aux invites utilisateurs pdnt le processus d'installation

4 paramètres principaux :

1. **WindowsPE** : Configure les paramètres initiaux, comme la partition de disque
2. **OfflineServicing** : Ajoute des mises à jour et pilotes pendant l’installation hors ligne
3. **Specialize** : Configure les paramètres réseau et de domaine 
4. **OOBE (Out-of-Box Experience)** : Définit les paramètres utilisateur, comme le compte administrateur et le fuseau horaire

**L'outil WSIM :** - Windows System Image Manager 
- Inclus dans le kit ADK 
- Permet de créer et personnaliser les fichiers de réponse

**SYSPREP :**
Avant de pouvoir déployer une image Windows sur de nouveaux PC, vous devez d’abord généraliser cette image. 
La généralisation de l’image supprime les informations spécifiques à l’ordinateur, telles que les pilotes installés et l’identificateur de sécurité (SID) de l’ordinateur.

Vous pouvez utiliser Sysprep seul ou Sysprep avec un fichier de réponses Unattend.xml pour généraliser votre image et la préparer au déploiement.


## SYNTHESE DEPLOIEMENT D'IMAGE :

- Le déploiement automatisé de Windows est un pilier essentiel pour gérer efficacement les parcs informatiques en entreprise. 
- Plusieurs méthodes de déploiement existent, chacune adaptée à des besoins spécifiques. 
-  Microsoft fournit des outils puissants comme WinPE, DISM et SYSPREP pour simplifier le processus.
- WinPE est un outil essentiel pour déployer et dépanner Windows. 
- La création d'une clé USB bootable est une compétence fondamentale pour les administrateurs
- Les outils ADK, DiskPart, et à exécuter les commandes nécessaires. 
- Le clonage permet d’accélérer le déploiement et d’uniformiser les configurations. 
- Le format WIM est flexible et efficace pour stocker plusieurs images

* Les fichiers unattend.xml permettent une installation entièrement automatisée et personnalisée de Windows. • 
- SYSPREP est essentiel pour la préparation d’images généralisées avant le déploiement. 
-  La combinaison des deux outils offre une solution puissante pour les environnements professionnels. • 
- DISM est un outil puissant pour gérer et déployer des images Windows dans des environnements professionnels. 
- La capture et le déploiement d’images standardisées améliorent l’efficacité et réduisent les erreurs. 
- La maîtrise de DISM est essentielle pour les administrateurs système travaillant avec Windows.



