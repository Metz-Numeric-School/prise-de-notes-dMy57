
# 1.2.1 Boîtier et alimentations :

### 1.2.1.1 Cas :

- Boîtier horizontal
- Tour pleine grandeur
- Tour compacte
- Tout-en-un

Cette liste n'est pas exhaustive, car de nombreux fabricants de boîtiers ont leurs propres conventions de dénomination. 
Il peut s'agir de **super tour, de tour complète, de tour moyenne, de mini tour, de boîtier cube, etc.**

Les boîtiers sont également conçus pour protéger contre les dommages causés par l'électricité statique. Les composants internes de l'ordinateur sont mis à la terre via une fixation au boîtier.

**Remarque** : les boîtiers d’ordinateur sont également appelés châssis d’ordinateur, armoire, tour, boîtier ou simplement boîte.

![[Pasted image 20250108140813.png]]

### 1.2.1.2 Alimentations :

L'électricité provenant des prises murales est fournie en courant alternatif (CA).
Tous les composants d'un ordinateur nécessitent une alimentation en courant continu (CC)

**Pour obtenir une alimentation CC, les ordinateurs utilisent une alimentation électrique, comme illustré ici, pour convertir le courant alternatif en courant continu à plus faible tension.**

- **Technologie avancée (AT)** – Il s’agit de l’alimentation électrique d’origine pour les anciens systèmes informatiques désormais considérés comme obsolètes.
- **AT Extended (ATX)** – Il s’agit de la version mise à jour de l’AT mais toujours considérée comme obsolète.
- **ATX12V** – Il s’agit de l’alimentation la plus courante sur le marché aujourd’hui. Elle comprend un deuxième connecteur de carte mère pour fournir une alimentation dédiée au processeur. Il existe plusieurs versions d’ATX12V disponibles.
- **EPS12V** – Conçu à l’origine pour les serveurs réseau, il est désormais couramment utilisé dans les modèles de bureau haut de gamme.

### 1.2.1.3 Connecteurs :

![[Pasted image 20250108141659.png]]

### 1.2.1.4 Tension d'alimentation : 

Les différents connecteurs fournissent également des tensions différentes. Les tensions les plus courantes fournies sont 3,3 volts, 5 volts et 12 volts.

Les alimentations 3,3 volts et 5 volts sont généralement utilisées par les circuits numériques, tandis que l'alimentation 12 volts est utilisée pour faire fonctionner les moteurs des lecteurs de disque et des ventilateurs.

Les alimentations électriques peuvent également être à rail simple, à rail double ou à rails multiples.

Un rail est le circuit imprimé (PCB) à l'intérieur de l'alimentation électrique auquel sont connectés les câbles externes. 
Un rail simple a tous les connecteurs connectés au même PCB tandis qu'un PCB à rails multiples a des PCB séparés pour chaque connecteur.

Un ordinateur peut tolérer de légères fluctuations de puissance, mais un écart important peut entraîner une panne de l'alimentation.

![[Pasted image 20250108141838.png]]

# 1.2.2 Cartes mères :

### 1.2.2.1 Cartes mères : 

La carte mère, également appelée carte système ou carte principale

une carte mère est un circuit imprimé (PCB) qui contient des bus, ou des voies électriques, qui interconnectent les composants électroniques.

Ces composants peuvent être soudés directement à la carte mère ou ajoutés à l'aide de sockets, d'emplacements d'extension et de ports.

### 1.2.2.2 Composants de la carte mère : 

![[Pasted image 20250108151253.png]]

- **Unité centrale de traitement (CPU)** - Elle est considérée comme le cerveau de l'ordinateur.
- **Mémoire vive (RAM)** - Il s'agit d'un emplacement temporaire pour stocker des données et des applications
- **Emplacements d'extension** : ils fournissent des emplacements pour connecter des composants supplémentaires.
- **Chipset** - Il s'agit des circuits intégrés de la carte mère qui contrôlent la manière dont le matériel du système interagit avec le processeur et la carte mère. Il détermine également la quantité de mémoire pouvant être ajoutée à une carte mère et le type de connecteurs sur la carte mère.
- **Puce du système d'entrée/sortie de base (BIOS) et puce UEFI (Unified Extensible Firmware Interface)** - Le BIOS est utilisé pour aider à démarrer l'ordinateur et à gérer le flux de données entre le disque dur, la carte vidéo, le clavier, la souris, etc. Dans les ordinateurs modernes, le BIOS a été remplacé par l'UEFI. L'UEFI spécifie un micrologiciel différent pour les services de démarrage et d'exécution. Le micrologiciel est une programmation qui permet à un système d'exploitation d'ordinateur de contrôler le matériel.

![[Pasted image 20250108152148.png]]

### 1.2.2.3 Chipset de la carte mère : 

La figure illustre comment une carte mère connecte différents composants.

La plupart des chipsets se composent des deux types suivants :

- **Northbridge** – Contrôle l'accès haut débit à la RAM et à la carte vidéo. Il contrôle également la vitesse à laquelle le processeur communique avec tous les autres composants de l'ordinateur. La fonction vidéo est parfois intégrée au Northbridge.

- **Southbridge** – Permet au processeur de communiquer avec des périphériques à vitesse plus lente, notamment des disques durs, des ports USB (Universal Serial Bus) et des connecteurs d'extension

![[Pasted image 20250108152719.png]]

### 1.2.2.4 Facteurs de forme de la carte mère

1.2.2.4 Facteurs de forme de la carte mère 

Le facteur de forme des cartes mères concerne la **taille** et la **forme** de la carte.  
Il décrit également la disposition physique des différents composants et dispositifs sur la carte mère.

De nombreuses variations de cartes mères ont été développées au fil des ans.  
Voici les trois facteurs de forme de carte mère les plus courants :

---
 Advanced Technology eXtended (ATX)

- C'est le facteur de forme de carte mère le plus courant.  
- Le boîtier ATX peut accueillir les ports d'E/S (I/O) intégrés sur une carte mère ATX standard.  
- L'alimentation ATX se connecte à la carte mère via un connecteur **20 broches unique**.

---
Micro-ATX

- Il s'agit d'un facteur de forme plus petit, conçu pour être **rétrocompatible avec l'ATX**.  
- Les cartes Micro-ATX utilisent souvent les mêmes chipsets Northbridge et Southbridge ainsi que les mêmes connecteurs d'alimentation que les cartes ATX pleine taille.  
- En général, les cartes Micro-ATX peuvent être installées dans des **boîtiers ATX standard**.  
- Cependant, les cartes Micro-ATX sont **plus petites** que les cartes ATX et possèdent **moins de slots d'extension**.

---
ITX

- Le facteur de forme ITX a gagné en popularité en raison de sa **très petite taille**.  
- Il existe de nombreux types de cartes ITX, mais le **Mini-ITX** est l'un des plus populaires.  
- Le facteur de forme Mini-ITX consomme **très peu d'énergie**, ce qui permet de ne pas utiliser de ventilateurs pour le refroidir.  
- Une carte mère Mini-ITX n'a qu'**un seul emplacement PCI** pour des cartes d'extension.  
- Ce facteur de forme est idéal pour des endroits où il est peu pratique d'avoir un ordinateur volumineux ou bruyant.

---
**Remarque : **

Il est important de distinguer les facteurs de forme.  
Le choix du facteur de forme de la carte mère détermine :  
1. La manière dont les composants individuels s'y attachent.  
2. Le type d'alimentation nécessaire.  
3. La forme du boîtier de l'ordinateur.  

Certains fabricants ont également des facteurs de forme propriétaires basés sur la conception ATX.  
Cela peut rendre certaines cartes mères, alimentations et autres composants **incompatibles** avec les boîtiers ATX standard.

| **Facteur de forme** | **Description**                                                                |
| -------------------- | ------------------------------------------------------------------------------ |
| **ATX**              | - Technologie avancée étendue                                                  |
|                      | - Facteur de forme le plus populaire                                           |
|                      | - 12 po x 9,6 po (30,5 cm x 24,4 cm)                                           |
| **Micro-ATX**        | - Empreinte plus petite que l'ATX                                              |
|                      | - Populaire dans les ordinateurs de bureau et les ordinateurs de petite taille |
|                      | - 9,6 po x 9,6 po (24,4 cm x 24,4 cm)                                          |
| **Mini-ITX**         | - Conçu pour les petits appareils tels que les clients légers et les décodeurs |
|                      | - 6,7 po x 6,7 po (17 cm x 17 cm)                                              |
| **ITX**              | - Facteur de forme comparable au Micro-ATX                                     |
|                      | - 8,5 po x 7,5 po (21,5 cm x 19,1 cm)                                          |
### 1.2.2.5 Vérifiez votre compréhension - Cartes mères

Associez les options comme décrit dans le tableau.

| **Élément**          | **Description**                                                                         |
| -------------------- | --------------------------------------------------------------------------------------- |
| **CPU**              | Considéré comme le cerveau de l'ordinateur.                                             |
| **Micro ITX**        | Un facteur de forme plus petit, compatible avec l'ATX.                                  |
| **Mini ITX**         | Ne dispose que d'un seul emplacement PCI pour des cartes d'extension.                   |
| **Northbridge**      | Contrôle l'accès à haute vitesse à la RAM et à la carte vidéo.                          |
| **Southbridge**      | Permet au CPU de communiquer avec des périphériques à vitesse réduite.                  |
| **RAM**              | Un emplacement temporaire pour stocker des données et des applications.                 |
| **Puce BIOS**        | Utilisée pour démarrer l'ordinateur et effectuer un autotest de mise sous tension.      |
| **Slot d'extension** | Fournit des emplacements pour connecter des composants supplémentaires à la carte mère. |

---

# 1.2.3 Processeurs et systèmes de refroidissement

### 1.2.3.1 Qu'est-ce qu'un processeur ?

##### Synthèse sur le CPU

Le processeur (**CPU**) est une puce électronique essentielle responsable d'interpréter et d'exécuter les commandes provenant des composants matériels et des logiciels. Il gère les instructions, comme celles d'un clavier, et envoie les informations nécessaires à d'autres périphériques, comme le moniteur.

Le CPU est logé dans un boîtier de processeur, souvent appelé lui-même CPU. Ces boîtiers existent en différents formats, nécessitant un socket spécifique sur la carte mère. Les principaux fabricants de processeurs sont **Intel** et **AMD**.

#### Socket CPU

Le **socket CPU** relie la carte mère au processeur.
Les architectures modernes de sockets incluent notamment :

- **Réseau de broches (PGA)** : Les broches sont situées sous le processeur et s'insèrent dans le support de la carte mère.
- Technologie **ZIF (Force d'insertion nulle)** : Réduit l'effort requis pour installer le processeur dans son socket, simplifiant ainsi l'installation.

![[Pasted image 20250108204038.png]]

- **Réseau de grilles terrestres (LGA)**

Dans une architecture LGA (illustrée ci-dessous), les broches se trouvent dans le socket plutôt que sur le processeur.

![[Pasted image 20250108204227.png]]

### 1.2.3.2 Systèmes de refroidissement

Le flux de courant entre les composants électroniques génère de la chaleur, ce qui peut ralentir l'ordinateur, provoquer des pannes ou endommager les composants. Il est donc essentiel de maintenir les ordinateurs au frais.

#### Types de solutions de refroidissement

1. **Refroidissement passif** : 
   - Ne nécessite pas d'énergie.
   - Utilise des dissipateurs thermiques ou réduit la vitesse des composants.

2. **Refroidissement actif** :
   - Nécessite de l'énergie.
   - Inclut des dispositifs comme les ventilateurs de boîtier.

Ces solutions permettent de maintenir des performances optimales tout en protégeant les composants de la surchauffe.

![[Pasted image 20250108205250.png]]
# 1.2.4 Vérifiez votre compréhension – Processeurs et systèmes de refroidissement

#### Question 1
**Vrai ou faux :**

**Dans l'architecture LGA, les broches se trouvent sur la face inférieure du processeur qui est insérée dans le socket CPU de la carte mère à l'aide de ZIF.**

- Vrai
- **FAUX**

**Commentaire :**
Dans l'architecture PGA, les broches se trouvent sur la face inférieure du boîtier du processeur et sont insérées dans le socket CPU de la carte mère à l'aide d'une force d'insertion nulle (ZIF). 
La ZIF fait référence à la quantité de force nécessaire pour installer un processeur dans le socket ou l'emplacement de la carte mère.

Dans une architecture LGA, les broches se trouvent dans le socket au lieu d'être sur le processeur.


#### Question 2

Quel est un exemple de refroidissement passif pour CPU ?

**Commentaire :**
Un dissipateur thermique évacue la chaleur du composant électronique. Il est doté d'un conducteur thermique qui absorbe et disperse la chaleur dans les ailettes. Ces ailettes possèdent une grande surface, ce qui permet à la chaleur de se dissiper à travers le boîtier de l'ordinateur. Le ventilateur du boîtier peut ensuite expulser l'air chaud hors du boîtier.


# 1.2.5 Mémoire

### 1.2.5.1 Types de mémoires

#### Synthèse : Types de mémoire d'un ordinateur

Les ordinateurs utilisent différents types de puces mémoire, qui stockent toutes les données sous forme d'octets. Un octet, composé de huit bits (0 ou 1), représente des informations telles que des lettres, chiffres ou symboles. Plus précisément, un octet est un bloc de huit bits stocké sous la forme de 0 ou de 1 dans la puce mémoire.

#### Mémoire en lecture seule (ROM) 
(Read Only Memory)

- La **ROM** est une mémoire non volatile, ce qui signifie que son contenu reste intact même lorsque l'ordinateur est éteint.
- Située sur la carte mère et d'autres circuits imprimés, elle contient des instructions essentielles, comme :
  - Le démarrage de l'ordinateur.
  - Le chargement du système d'exploitation.
- Le processeur peut accéder directement aux instructions stockées dans la ROM.

#### Mémoire à accès aléatoire (RAM)

- La **RAM** est une mémoire volatile, ce qui signifie que son contenu est effacé lorsque l'ordinateur est éteint.
- Elle sert de stockage temporaire pour les données et programmes utilisés par le processeur.
- L'ajout de RAM améliore les performances du système :
  - Augmente la capacité de traitement des programmes et fichiers.
  - Réduit le besoin d'échanger des données avec le disque dur, qui est beaucoup plus lent.
- La quantité maximale de RAM dépend des limites de la carte mère.

### 1.2.5.2 Types de ROM

![[Pasted image 20250108212527.png]]

![[Pasted image 20250108212631.png]]

### 1.2.5.3 Types de RAM :

#### RAM DYNAMIQUE
- Technologie plus ancienne, populaire jusqu'au milieu des années 1990
- Utilisé pour la mémoire principale
- La DRAM décharge progressivement de l'énergie, elle doit donc être constamment rafraîchie par des impulsions électriques afin de conserver les données stockées dans la puce

#### RAM STATIQUE
- Nécessite une alimentation constante pour fonctionner
- Souvent utilisé pour la mémoire cache
- Utilise une consommation d'énergie inférieure
- Beaucoup plus rapide que la DRAM
- Plus cher que la DRAM

#### MEMOIRE SDRAM 
- DRAM qui fonctionne en synchronisation avec le bus mémoire
- Capable de traiter des instructions qui se chevauchent en parallèle, par exemple, il peut traiter une lecture avant qu'une écriture ne soit terminée
- Taux de transfert plus élevés

#### RAM DYNAMIQUE SYNCHRONE A DOUBLE DEBIT DE DONNEES
- La DDR SDRAM transfère les données deux fois plus vite que la SDRAM
- Capable de prendre en charge deux écritures et deux lectures par cycle d'horloge du processeur
- Le connecteur possède 184 broches et une seule encoche
- Utilise une tension standard inférieure (2,5 V)
- Famille : DDR2, DDR3, DDR4

#### RAM DYNAMIQUE SYNCHRONE DDR2
- La SDRAM DDR2 transfère également les données deux fois plus vite que la SDRAM
- Fonctionne à des vitesses d'horloge plus élevées que la DDR (553 MHz contre DDR à 200 MHz)
- Améliore les performances en réduisant le bruit et la diaphonie entre les fils de signal
- Le connecteur a 240 broches
- Utilise une tension standard inférieure (1,8 V)

#### RAM DYNAMIQUE SYNCHRONE DDR3
- La SDRAM DDR3 étend la bande passante mémoire en doublant la fréquence d'horloge de la DDR2
- Consomme moins d'énergie que la DDR2 (1,5 V)
- Génère moins de chaleur
- Fonctionne à des vitesses d'horloge plus élevées (jusqu'à 800 MHz)
- Le connecteur a 240 broches

#### RAM DYNAMIQUE SYNCHRONE DDR4
- La mémoire SDRAM DDR4 quadruple la capacité de stockage maximale de la DDR3
- Consomme moins d'énergie que la DDR3 (1,2 V)
- Fonctionne à des vitesses d'horloge plus élevées (jusqu'à 1600 MHz)
- Le connecteur a 288 broches
- Disponible avec des fonctionnalités de correction d'erreur avancées telles que la mémoire de code de correction d'erreur (mémoire ECC) pour détecter les erreurs sur plusieurs bits.

#### RAM DYNAMIQUE SYNCHRONE GDDR
- Le « G » signifie Graphics
- RAM spécialement conçue pour les graphiques vidéo
- Utilisé en conjonction avec un GPU dédié
- Famille : GDDR, GDDR2, GDDR3, GDDR4, GDDR5
- Chaque membre de la famille améliore ses performances
- Chaque membre de la famille réduit sa consommation d'énergie
- La GDDR SDRAM traite des quantités massives de données, mais pas nécessairement aux vitesses les plus rapides

#### DDR5 
- Plus du double de la vitesse des modules DDR4 les plus rapides. 
- La DDR5 quadruple la capacité de stockage maximale de la DDR4 
- Consommation d'énergie légèrement inférieure à celle de la DDR4 (1,1 V) 
- Le connecteur possède 288 broches mais un motif différent de celui de la DDR4, ils ne sont donc pas compatibles 
- La taille maximale du module est de 128 Go

### 1.2.5.4 Modules de mémoire

