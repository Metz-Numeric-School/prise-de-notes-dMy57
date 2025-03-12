
Proxy = Intermédiaire qui fait les requête à notre place

Permet de stocker les cookies de tous les users sur un serveur proxy et ainsi les gérer (entreprise)

Reverse Proxy 
Interne ou externe

Regle de filtrage (ACL)
Certificat SSL 

Proxy de manière logiciel et physique

WinScp = adrese ip du pnet = root / pnet

Putty (SSH)  = adress IP pnet = root / admin

cd /opt/unetlab/addons/qemu/opnsense-24.7/ (se rend dans le dossier créer au préalable)
/opt/qemu/bin/qemu-img create -f qcow2 virtioa.qcow2 10G (créer le DD virtuel 25GO)

cd (reviens à la racine)

/opt/unetlab/wrappers/unl_wrapper -a fixpermissions 

----

# 12-03-2025 - PROXY

Sur VMware, ajout de deux carte réseau (NAT) + un autre au choix 

Pour l'installation : 

se login avec "installer" et mettre mdp "opnsense" 

- ZFS
- STRIPE (no redundancy) / ``Mirror = copie sur deux disques ``
- Choisir le disque 
- Yes
- Procédure d'installation se lance
- Apres l'install, desactive l'iso dans : 
![[Pasted image 20250312091139.png]]
désactiver "connected"
faire les mise à jour (suivre procédure word)

## CERTIFICAT 

Système -> Gestion des certificats -> autorités 

![[Pasted image 20250312092517.png]]

Télécharger le certificat :

renommer en .**crt**

Ouvrir le certificat et installer sur l'ordinateur :

Placer dans le "magasin" puis autorités de certification racines de confiance 
![[Pasted image 20250312092910.png]]

Systèeme ->Firmaware -> Greffons (plugins)

rechercher squid puis installer 

redémarer le serveur

Installation du proxy :

Services - proxy web squid - admin - forward proxy 

Choisir l'interface LAN + mettre certificat SSL  dans "AC" à use puis choisir paramètre cache local et cocher "activer le cache local" puis appliquer 

cocher aussi activer le proxy dans reglages proxy généraux 

Pare feu -> regle -> LAN -> nv regles 

![[Pasted image 20250312094844.png]]

mettre decription :  HTTP Bloquée pour forcer le PROXY puis save 

la dupliquer et changer HTTP par HTTPS 

monter les règles en les cochant et les faire "monter" puis appliquer les changement 

![[Pasted image 20250312095221.png]]
![[Pasted image 20250312095251.png]]


Dans windoxs : activer proxy 

cocher utiliser un server proxy :  et mettre l'ip + port 3128  puis enregistré 

![[Pasted image 20250312102356.png]]