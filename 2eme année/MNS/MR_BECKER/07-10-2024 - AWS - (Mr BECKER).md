

[**CLOUD**](https://www.cloudflare.com/fr-fr/learning/cloud/what-is-the-cloud/) :

Le terme « cloud » désigne les serveurs accessibles sur Internet, ainsi que les logiciels et bases de données qui fonctionnent sur ces serveurs.
Les serveurs situés dans le cloud sont hébergés au sein de [datacenters](https://www.cloudflare.com/learning/cdn/glossary/data-center/) répartis dans le monde entier. 

L'utilisation de l'informatique cloud (cloud computing) permet aux utilisateurs et aux entreprises de s'affranchir de la nécessité de gérer des serveurs physiques eux-mêmes ou d'exécuter des applications logicielles sur leurs propres équipements. (sécu, stockage, décentralisé)

### FOURNISSEURS DE CLOUD

* AWS : (Amazon Web Service) 
* AZURE :  (Microsoft)
* GOOGLE 
---
# MODULE 1 

## PRESENTATION DES CONCEPTS CLOUD

**Cloud Computing** : *Déploiement à la dmd de puissance, de calcul, de stockage, de base de données, d'applications et d'autres ressources informatique par Internet, avec une **tarification à l'utilisation***

Ces ressources fonctionnent sur des ordi serveurs situés dans de grands centre de données à différents endroits dans le monde

Ces ressources peuvent être utilisées ensemble comme des blocs de construction pour fabriquer des solutions qui vous aideront à atteindre vos objectifs commerciaux et à satisfaire aux exigences technologique. 

Le #cloud_computing vous permet de ne plus considérer votre infrastructure comme du matériel mais plutôt comme un logiciel.

#### MODELE D'INFORMATIQUE TRADITIONNELLE

	Infrastructure en tant que matériel
	Solutions matérielles :
	Nécessitent de la place, du personnel, une sécurité physique, une planification et des dépenses d'investissement.
	Impliquent un long cycle d'approvisionnement en matériel, la maitenance
	Vous obligent à allouer la capacité en devinant les pics maximaux théoriques

Avec une "solution matérielle" vous devez vous demandez si vous disposez d'une capacité de ressources ou de stockage suffisante pour répondre à vos besoins et vous provisionnez la capacité en devinant les pics maximaux théoriques. 

* Si vous "n'atteignez" pas le pic "maximal" prévu vous "payez" pour des ressources coûteuses qui restent inutilisées et nous vous apportent aucun avantage. 

* Si vous dépasser le pic max prévu, vous n'avez pas la capacité suffisante pour répondre à vos besoins et vos clients ne reçoivent pas le service qu'il souhaitent.

***Exemple :*** 

	Si vous souhaitez mettre en service un nouveau site web, il faut acheter le matériel, l'installer et l'intégrer. L'installer dans un centre de données, puis le gérer ou le faire gérer par qqun d'autre (couteux et prend bcp de temps)

	En revanche, si on utilise le cloud computing notre "infrastructure"  est considérer comme "logiciel".

#### Modèle de cloud computing 

	.Infrastructure en tant que logiciel
	· Solutions logicielles :
	. Assurent la flexibilité (chosir les services cloud correspondent le mieux à vos besoins, les mettre en service et mettre fin à leur utilisation en fonction de votre demande)
	· Peuvent évoluer plus rapidement, plus facilement et à moindre coût que les solutions matérielles
	· Éliminent les tâches opérationnelles, lourdes et indifférenciées (approvisionnement, maitenance, planification des capacités)
	· Augmente et diminue les ressources de manière automatisée afin d'étendre et de réduire votre déploiement pour répondre à la demande de vos clients. 
	· Avec le modèle de cloud computing, vous pouvez considérer les ressources comme temporaire et jetables
	· La flexibilité qu'offre le cloud computing permet aux entreprise de mettre en œuvre rapidement de nouvelles solutions avec un coût initial très faible

***Solution logicielles peuvent évoluer plus rapidement et facilement et à moindre coût que les solutions matériels***.
***permet de ce concentrer sur ce qui compte le plus : votre entreprise*** 

Chq type de modèle de service cloud et de stratégie de déploiement vous offre un nv différent de contrôle de gestion et de flexibilité 

#### Modèle de service cloud

3 principaux : 

**1 - IaaS** = Infrastructure as a Service = élément de base de votre tech cloud ; accès à des fonctions réseau, des pc virtuels ou dédiés et stockage

**2 - PaaS** = Plateforme as a Service = plus haut nv de flexibilité et de contrôle sur vos ressources informatiques - dispense de gérer l'infrastructure sous-jacente (matériel, os, etc .. ) par le biais de l'automatisation et permet de vous concentrer sur le déploiement et gestion des applications à la place de l'approvisionnement

**3 - SaaS** = Software as a Service (m365, suite google, etc ...) = fournit un produit complet, logiciel en tant que service fait référence à des applications pour l'user final / pas de maintenance du service ou de la gestion de l'infra 

![[Pasted image 20241008134509.png]]

#### Modèle de déploiement de cloud computing 

Cloud : 
- Une appli basée sur le cloud est entièrement déployée dans le cloud (tout dans le cloud) toutes les parties de votre application seront exécutées dans le cloud.
- Les applis ont été créées dans le cloud ou migrées depuis une infrastructure existante 

Hybride : (entre le cloud & locaux existants)
+ Permet de connecter vos infra et vos applis existantes à des ressources basées sur le cloud
+ Pas situées dans le cloud, situées dans vos installations physiques
+ Permet d'étendre et de développer votre mise en œuvre tout en connectant les ressources du cloud à vos systèmes internes.

Cloud privée : 
- Déploiement des ressources sur site, utilise des outils de virtualisation et de gestion des ressources parfois appelé cloud privé
- Pas un grand nbr d'avantages sur le cloud computing, parfois recherché pour sa capacité à fournir des ressources dédiées 
- Dans la plus part des cas même modèle de déploiement qu'une infrastructure "traditionnelle" 
#### Similitude entre AWS et l'informatique "traditionnelle"


![[Pasted image 20241019172934.png]]


## AVANTAGES DU CLOUD COMPUTING

6 avantages : 

- Investissement en centre de données basé sur les prévisions -> Paiement en fonction de la qté consommée *(échanger les dépenses en capital contre des dépenses variables)

- AWS peut réaliser de plus grandes économies de mise à l'échelle et en faire bénéficier ses clients (cout d'achats - élevés)

- Plus besoin de deviner la capacité nécessaire (surestimation de la capacité du serveur / sous-estimation)  -> Mise à l'échelle à la demande

- Augmenter la vitesse et l'agilité (Qlq semaines entre la dmd de ress et leur obtention (info tradi) -> Qlq mintues entre la demande de ress et l'obtention 

- Ne dépensez plus d'argent pour le fonctionnement de la maintenance de centres de données.

- Déploiement international en qql minutes 
## INTRODUCTION A AWS

Un service web est un logiciel qui se rend dispo sur internet ou réseau privé et utilise un format normalisé tel que **XML** *(extensible Markup Language)* ou **JSON** *(JavaScript Object Notation*) pour la dmd et la réponse d'une **interaction API**

* Il s'agit du jeu de données et du format utilisé pour la requête et la réponse afin d'interagir avec ce service web via une interface de programmation d'applications (pas lié à l'OS, pas au langage utilisé pour développer le logiciel) 

* Autodescriptif à l'aide d'un fichier de définition d'interface et "découvrable"
#### Qu'est-ce que AWS ?

. AWS est une **plateforme cloud sécurisée** qui offre un **large éventail** de **produits mondiaux basés sur le cloud.**
. AWS fournit un **accès à la demande** au calcul, au stockage, au réseau, aux bases de données et à d'autres ressources informatiques et outils de gestion.
· AWS assure la **flexibilité.** 
. Vous **ne payez que pour les services dont vous avez besoin, tant que vous les utilisez.**
. Les services **AWS interagissent** comme des blocs de construction.
. Les facturations service AWS devient une dépenses opérationnelle et non plus une dépense d'investissement 

Les services AWS sont conçus pour fonctionner ensemble afin de prendre en charge pratiquement tout type d'application ou de charge de travail (comme des bloc de constructions qui sont interconnectés afin de les assembler pour construire des solutions sophistiqués et évolutives)

La service que vous choisissiez dépend de vos objectifs métier et de vos besoins en technologie 
Plusieurs outils différents (calculs, stockage, gestion et de gouvernance, Sécurité, Service de base, Service de mise en réseau, Service de gestion des coûts AWS)
#### Catégories de services AWS :

Chaque catégorie contient un ou plusieurs services 
- On peux choisir le service qu'on souhaite pour élaborer des solutions

![[Pasted image 20241019172711.png]]

#### Choix d'un service : 
![[Pasted image 20241019172739.png]]

### MODULE 6 - Services des calculs AWS

Elastic container / Elastic Kubernetes / AWS Fargate sont utilisés pour une architecture de conteneurs ou de micro-services
#### Services couverts dans ce cours (fondamentaux / les plus courant)

![[Pasted image 20241019173201.png]]

Trois moyen d'interagir avec AWS : 

- Interface WEB (AWS Management console) *interface graphique facile à utiliser*
- Interface de ligne de commandes (AWS CLI) *accès aux services par des cmd ou des scripts simples utilisant un environnement d'exploitation Linux, MacOS, Microsoft Windows)
- Kits de développement logiciel (SDK) *accès au service directement depuis votre code
	(JAVA, C#, Python, Node.js et d'autres)*

Ces trois options sont construites à l'aide d'une interface de programmation d'applications de type #rest [[Définitions -]] , elle forme la base de AWS 
## MIGRATION VERS LE CLOUD AWS

Migration vers AWS Cloud à l'aide du Framework d'adoption d'AWS Cloud
	
	Le Cloud Computing transforme de façon considérable la manière donc la tech est obtenue.
	
	Il modifie aussi radicalement la manière dont les organisations budgétisent et paient pour des services technologiques.
	
	L'adoptation d'un cloud exige que des changements fondamentaux soient discutés et envisagés dans l'ensemble d'une organisation. 
	
	Il faut également que les parties prenantes de toutes les untiés de l'organisation, tant à l'intérieur qu'a l'éxtérieur.












## CONCLUSION DU MODULE : 

- Définir les diff types de modèles de cloud computing
- Décrire 


Pq AWS est-il plus économique que les centres de données traditionnels pour les appli avec des charges de travail informatique variables ?
	Les instances Amazon EC2 peuvent être lancées à la demande, lorsque que cela est nécessaire.



# MODULE 2 

## Couts du cloud et facturation 

Trois facteurs fondamentaux de coûts avec AWS : 
Modèle de tarification ( calcul, stockage, transfert de données)

Payez ce que vous utilisez, payez moins lorsque que vous réserver, payer moins lorsque XXXXX

Payez seulement les services que vous utilisez, sans frais initiaux excessif

Tarifs dégressifs selon l'utilisation  

![[Pasted image 20241019174933.png]]

![[Pasted image 20241019175054.png]]

![[Pasted image 20241019175213.png]]

![[Pasted image 20241019175414.png]]

![[Pasted image 20241019175443.png]]

![[Pasted image 20241019175512.png]]

![[Pasted image 20241019175534.png]]

![[Pasted image 20241019175611.png]]


---
## Cout total de possession





# MODULE 6 

## Services des calculs AWS

- **Amazon Elastic Compute Cloud (EC2)** *fournit des machines virtuelles redimensionnables
- **EC2 auto scaling** *soutient la disponibilités des applications en vous permettant de définir des conditions qui lanceront ou arrêteront automatiquement les instances EC2*
- **Elastic Container Registry (ECR)** *permet de stocker et récupérer les images #docker[[Définitions -]]
- **Elastic Container Service (ECS)** *est un service d'orchestration de conteneurs qui prend en charge #docker
- **VMware cloud sur AWS** *permet de mettre en service un cloud hybride sans matériel personnalisé
- **AWS Elastic Beanstalk** *offre un moyen simple d'exécuter et de gérer des applications Web*
- **AWS Lambda** *est une solution de calcul sans serveur, vous ne payerez que le temps de calcul que vous utilisez*
- **Elastic Kubernetes Service (EKS)** vous permet d'éxécuter #kubernetes [[Définitions -]] géré sur AWS
- **Amazon Lightsail** *fournit un service simple à utiliser* pour créer une appli/site web
- **Batch** *est un outil permettant d'exécuter des taches par lots à n'importe quelle échelle
- **Fargate** *permet d'exécuter des conteneurs qui réduisent la nécessité de gérer des serveurs ou des clusters*
- **AWS Outpost**, *permet d'exécuter certains service AWS dans votre centre de données sur site*
- **AWS Serverless Application Repository** *offre un moyen de découvrir, déployer, publier des applications sans serveur*

### Catégorisation des services de calcul 

CHAQUE SERVICE DE CALCUL AWS APPARTIENT A L'UNE DES 4 GRANDES CATEGORIES DEFINIES COMME SUIT : (Services / Concept clés / Caractéristiques / Simplicité d'utilisation)

![[Pasted image 20241008092247.png]]

**1er catégorie** :  fournit des des VM (les services de cette catégorie offrent une certaine souplesse et vous laissent une grande partie des responsabilités de gestion de serveur) choix du système d'exploitation, capacité, ressources, etc ... 

**2eme catégorie** : plateforme de calcul sans aucune tâche administrative (vous permet d'exécuter du code sans avoir à mettre en service ou gérer des serveurs) **paye ce que vous consommé**(temps de calcul)

		l'informatique sans serveur gagne en popularaité psq elle prend en charge les architéctures natives du cloud, qui permettent une scalabilité massive à un coût inférieur à celui d'un service qui fonctionnerait 24/24 pour garantir l'exécution des mêmes charges de travail.

**3 eme catégorie** : services basés sur les conteneurs (ECS, EKS, Fargate, ECR) 
les #conteneurs [[Définitions -]] sont mis en service plus rapidement que les VM car le système d'exploitation est exclu du processus de mise en service

**4ème catégorie** : **AWS Elastic Beanstalk** qui est considéré comme une plateforme en tant que service, pour les applications web. Il facilite le déploiement rapide en fournissant tous les services dont vous avez besoin. 

AWS gère les systèmes d'exploitation, le serveur d'applications et d'autres composants d'infrastructure afin que vous puissiez vous concentrer sur le dév du code de votre application.

#### CHOISIR LE SERVICE DE CALCUL OPTIMAL

· Les services de calcul optimaux que vous utiliserez dépendent de
votre cas d'utilisation.
· Aspects à prendre en considération :
· Quelle est la conception de votre application ?
· Quelles sont vos modèles d'utilisation ?
· Quels sont les paramètres de configuration que vous souhaitez gérer ?
· La sélection d'une solution de calcul inadéquate pour une architecture
peut nuire à l'efficacité des performances, de dispo ou de déploiement d'applications
· Un bon point de départ consiste à connaître les options de calcul disponibles.
· Pour une application existante, on peut également utiliser des métriques, puis collecter des #métriques liées à l'ordinateur, pour réévaluer les besoins en calcul, en fonction de ce que les métriques vous disent. [[Définitions -]]

Un client peut commencer avec une solution de calcul et décider de changer la conception en fonction des modèles d'utilisation ou des changements dans la conception de l'application entièrement.

---




