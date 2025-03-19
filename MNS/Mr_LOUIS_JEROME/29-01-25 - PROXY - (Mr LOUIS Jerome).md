
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
faire les mise à jour (suivre procédure Word)









et télécharger les acls et les appliquer : 
![[Pasted image 20250312111113.png]]

amazon : 
![[Pasted image 20250312111251.png]]



