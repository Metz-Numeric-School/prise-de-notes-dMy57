
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

Permet de se connecter au serveur grâce à la clé privée **(id_rsa_bsrc2)**
```
ssh -i C:\Users\Quent\Downloads\id_rsa_bsrc2 debian@141.95.164.126
```
changez "quent" part votre nom d'ordi et mettre l'ip de votre serveur

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# **Partie 1 : Manipulation basique avec Docker CLI**
##### Permet de créer le conteneur + suite (ubuntu / wordpress)
```
sudo docker run -it
```
## Ubuntu
```
sudo docker run -it public.ecr.aws/ubuntu/ubuntu:24.04_stable bash
# public.ecr.aws/ubuntu/ubuntu:24:04_stable bash = image
```

## Wordpress
```
sudo docker run -it public.ecr.aws/docker/library/wordpress:php8.3-apache
# public.ecr.aws/docker/library/wordpress:php8.3-apache bash = image
```

---
 # permet de lister les conteneurs
 ```
sudo docker ps -a
```

 # permet de lister les images 
```
 sudo docker images
```

 # permet de supprimer un conteneur
```
 sudo docker rm + mettre l'ID (qu'on le trouve dans la liste des conteneurs)
```

Pour suppression d'image, il faut stopper le conteneur :
```
sudo docker stop / kill  + mettre id du conteneur
```

Suppression de l'image : 
```
sudo docker rmi + mettre l'ID (qu'on le trouve dans la liste des images)
```

Forcer la suppression :
```
sudo docker rmi -f + Id de l'image  (qu'on le trouve dans la liste des images)
```

---
`sudo docker image prune -a` → Supprime toutes les images inutilisées

#### **4️⃣ Supprimer plusieurs images en une seule commande** : 
```
sudo docker rmi imageID1 imageID2 imageID3
```

#### **5️⃣ Supprimer toutes les images inutilisées**

Si tu veux nettoyer ton système et supprimer toutes les images non utilisées par des conteneurs actifs :
```
docker image prune -a
```

# **Partie 2 : Création d’un Dockerfile pour un serveur Apache**

### **1️⃣ Préparer les fichiers nécessaires**

Crée un **nouveau dossier** pour ce projet et place-toi dedans :
```
mkdir TP && cd TP
```

Dockerfile dans le répertoire tout juste créer (TP)
```
sudo nano Dockerfile
```

y mettre les éléments suivants : 

```
# Utiliser l'image officielle d'Apache basée sur Alpine
FROM httpd:alpine

# Copier notre fichier HTML personnalisé dans le répertoire web d'Apache
COPY index.html /usr/local/apache2/htdocs/index.html

# Exposer le port 80 pour accéder au serveur web
EXPOSE 80
```

Créer le fichier index.html :
 ```
sudo nano index.html
```

y mettre les éléments suivants : 

```
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>TP Docker - Apache personnalisé</title>
</head>
<body>
  <h1>Bienvenue sur mon serveur Apache personnalisé !</h1>
  <p>Exercice Docker en ligne de commande.</p>
</body>
</html>
```

#### **Construire l’image Docker**

Assure-toi que les fichiers `Dockerfile` et `index.html` sont dans le même dossier, puis exécute la commande :

```
docker build -t mon_apache_personnalise .
```

#### **Lancer le conteneur Apache**

Exécute la commande suivante pour lancer un conteneur basé sur cette image :

```
docker run -d --name mon_apache -p 8080:80 mon_apache_personnalise
```
📌 Cela démarre le serveur Apache en arrière-plan (`-d` pour **detached mode**) et mappe le port 80 du conteneur sur le port **8080** de la machine hôte.

#### **Tester l'accès à la page web**

Ouvre un navigateur et entre l’URL suivante :

```
http://141.95.164.126:8080/
```

---
#### **Gérer le conteneur**

- **Lister les conteneurs actifs** :
```
docker ps
```

- **Arrêter le conteneur** :
```
docker stop mon_apache
```

- **Redémarrer le conteneur** :
```
docker start mon_apache
```
 
- **Supprimer le conteneur** :
```
docker rm mon_apache
```

- **Supprimer l’image Docker** :
```
docker rmi mon_apache_personnalise
```

### **📌 Résumé des étapes**

1️⃣ Crée un dossier `TP` et place `Dockerfile` + index.html` dedans.  
2️⃣ Construis l’image avec `docker build -t mon_apache_personnalise .`.  
3️⃣ Lance un conteneur avec `docker run -d --name mon_apache -p 8080:80 mon_apache_personnalise`.  
4️⃣ Accède à `http://localhost:8080` pour voir la page.




