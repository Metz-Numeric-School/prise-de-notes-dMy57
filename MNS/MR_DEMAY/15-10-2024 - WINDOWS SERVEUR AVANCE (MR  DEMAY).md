
# DNS (Domain Name System)

Pour qu'un DNS fonctionne il faut un serveur.

L'ICANN est un organisme qui gère la liste des **Top Level Domain (TLD)**
	Il existe une TLD par pays
		fr (france) / it (italie) / de (allemagne) / et qlq TLD générales (.com, .net,.org, .mil, .biz)
		
L'ICANN délègue la gestion de chaque TLD à un organisme **(registry)**

Les registry doivent tenir à jour la liste des domaines définis sur sa ou ses TLD.

	AFNIC tient le registre des .fr
		VeriSign tient le registre des .com/.net/.org/.name/.info/.biz
		
Chaque registry peut gérer comme bon lui semble l'attribution des noms de domaine sur sa TLD.

Les **registry** ont un **rôle technique**.
Chaque **registry** et ils autorisent des **registrars** à vendre des noms de domaines.
Les **registrars** ont un **rôle commercial**.

![[Pasted image 20241015114644.png]]

Chaque pays possède un **TLD** qui correspond à son code pays ISO on les appelle **ccTLD (Country-code TLD)**

La gestion des TLD repose sur des serveurs racines (appelées DNS root servers) 

![[Pasted image 20241015114659.png]]

Les serveurs racines sont reliées entre eux (fibre) (nœuds optiques qui traversent les océans)

 (serveur racine emplacement + IP + société qui gère + logiciel) ![[Pasted image 20241015114733.png]]

RACINE - > TLD -> NOM DE DOMAINES -> SERVICES
![[Pasted image 20241015114749.png]]

---

# DNS (Domain Name Service)

**Permet la correspondance entre un nom de domaine qualifié FQDN** (*Fully Qualified Domain Name*) et une adresse IP (ex : www.google.fr = 74.125.230.82)

un nom FQDN doit tjrs se terminer par un "point" qui représente la racine DNS.

Résolution d'une adresse IP en nom de domaine avec l'ajout d'un domaine spécial **in-addr.arpa à la fin** (ex : réseau 10.1.0.0. adresse inversé : 1.10.in-addr.arpa  - réseau 192.168.1.0 adresse inversé : 1.168.192.in-addr.arpa)

## DELAGATION :

Transfet de responsabilité dans l'adminsitration d'une zine DNS avec autorisé pour les serveurs de la zone de résolutions DNS

## ZONE PRIMAIRE & SECONDAIRE :

Transfert de zones entre serveur maître (primaire) et un aiutre serveur (secondaire) chacun ayant autorité sur la zone.
Vis-à-vis d'un client, l'un ou l'autre répond en fonction de la vitesse du réseau.

#### **4 Scénarios possible :**

- Serveur CACHE - 
					But :  ***effectue des requêtes DNS pour se rappeler de la réponse pour la prochaine requête***
					Avantages : *Réduction de la bande passante / réduction du temps de latence*

- Serveur primaire
					But :  **Contenir des enregistrements DNS d'un nom de domaine enregistré**
					Un ensemble d'enregistrements DNS pour un nom de domaine est appelée une ***"zone"***
					Le nom de domaine peut être imaginaire, mais seulement sur un réseau local fermé, non connecté à internet.
				
					
- Serveur secondaire
					But :  **Contenir une copie des zones configurées sur le serveur maître**
					Avantages : Recommandé sur les réseaux importants
					Assure la disponibilité de la zone DNS si le serveur maître n'est pas disponible

- Serveur stub
					Idem que le serveur esclave (secondaire), mais copie uniquement les données du serveur et pas les données de l'hôte (sorte de copie des données)


#### ENREGISTREMENT DNS

**But** : mapper nom d'hôte / adresse IP et adresse IP / nom d'hôte

|       ENREGISTREMENTS       |                         MAPPAGES                          |
| :-------------------------: | :-------------------------------------------------------: |
| 1 - SOA (Start of autority) | Serveur DNS de la zone principale (primaire) / adresse IP |
|    2 - NS (Name server)     |                 Serveur DNS / Adresse IP                  |
|            3 - A            |                   Hôte / Adresse IP v4                    |
|          4 - AAAA           |                   Hôte / Adresse IP v6                    |
|      5 - PTR (PoinTeR)      |          Adresse IP / Hôte (recherche inversée)           |
| 6 - CNAME (Canonical NAME)  |                    Hote / Hôte (alias)                    |
|   7 - MX (Mail eXchanger)   |            Serveur de messagerie / Adresse IP             |

1 - 2 - 3 - 5 (entreprise)


### CONFIG WSERV

1 - IP statique + changement de nom 
2 - Gestionnaire de serv -> (gérer et outils) -> cocher seveur DNS + fonctionnalités 
3 - Outils -> DNS -> (zone de recherche directs) -> Zone principale 
4 - Nom de domaine : qw.local
5 - autoriser les MAJ dynamiques (première config)
6 - "terminer" -> création de la zone primaire

Vérification : priorités zone primaires puis check les onglets 
	(SOA : rajouter .cd.local.) - même chose pour serveurs de noms

Zone de recherche inversée IPv4 -> inversement de l'IP 
	autorisation des MAJ dynamiques puis terminer.

Vérification : SOA + Serveurs de noms 

- Création deuxième serveur (zone secondaire)
- nom de la zone + ip du serveur maitre

Retour serveur primaire : transfert de zone : "autorise les transferts de zone" / "uniquement vers les servs listés dans l'onglet serveurs de nom"

Mettre en place "les redirecteurs" permet de gérer les accès hors local (NEXTGENAD = redirecteur)


# DHCP (Dynamic Host Configuration Protocol)

### ROLE DU DHCP

Permets aux serveurs d'attribuer des adresse IP aux ordinateurs et autre périphériques reconnus comme client DHCP

Le déploiement d'un serveur DHCP sur le réseau fournit aux ordinateurs et autres périphériques réseaux TCP / IP  


### Installation du rôle DHCP 

### Configuration du rôle DHCP 

clic droit IPV4 -> nvl étendue (donner nom + description )
Mettre l'adresse IP de début et de fin (24 = 255.255.255.0)
(adresse IP à exclure si besoin (serveurs/ imprimante/ switch / etc ...))

Régler le "bail" / 1 journée / 1 semaine 

Config des options : 

### DHCP de secours : 

Installer le role DHCP sur le 2eme serveur
retour sur srv1 puis clic droit sur l'étendue puis config un basculement : 
ajout du 2eme serveur 

Mode : équilibrage de charge / secours 
Secret partagé : mdp pour cryptages de données entre les 2 serv

















