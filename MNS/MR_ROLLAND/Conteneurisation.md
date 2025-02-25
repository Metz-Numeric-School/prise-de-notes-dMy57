
```
La conteneurisation est un **processus de déploiement logiciel qui regroupe le code d'une application avec tous les fichiers et bibliothèques dont elle a besoin pour s'exécuter sur n'importe quelle infrastructure.
```

Docker :
* technologie de conteneurisation qui permet la création et l'utilisation de conteneurs Linux
* Open source ; gratuit
* Docker Inc s'appuie sur le travail de la communauté Docker, sécurise sa tech et partage ses avancées avec les users. Elle prend ensuite en charge les tech améliorées et sécurisées pour ses clients.

Avantages : 
* Modularité
* Couche et contrôle des versions d'images 
* Restauration
* Déploiement rapide

Limites : 
- Complexité lors de la montée en puissance
- Toutes les fonctionnalités UNIX ne sont pas présentent (cron/syslog) 

---
Couche et contrôle des versions images :
- Chq fichier image Docker est composé d'une série de couche
- Ces couches sont assemblées dans une image unique
- Chq modifs de l'image engendra la création d'une couche
- Chq user exécute une commande, comme run ou copy, une nouvelle couche se crée
- Docker réutilise ces couches pour la construction de nvx conteneurs accélérant ainsi le processus de construction
- Les modifs intermédiaires sont partagées entre les images, ce qui optimise la vitesse, la taille et l'efficacité 
- Qui dit superposition de couches, dit contrôles des versions 
- Chq changement, un journal des modifs est mis à jour afin d'offrir un contrôle total des images de votre conteneur
---
De l'image au conteneur 
- Une image Docker est une structure en lecture seule qui contient l'ensemble des instructions pour créer un conteneur
- Une même image peut servir à créer plusieurs conteneurs différents (réemploi, limitation du stockage)
- Une image Docker est fabriquée (build) à partir d'une collection de fichiers qui mis ensemble forment l'essentiel requis au fonctionnement du conteneur
- On recherche à minimiser la taille de l'image afin de minimer le sotckage et les coûts et améliorer les performances.
---





