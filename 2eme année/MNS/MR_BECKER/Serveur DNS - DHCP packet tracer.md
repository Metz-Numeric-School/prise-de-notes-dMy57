
depuis un serveur -> services -> activer le DHCP 

Création des pool :

pool name : vlan10
default gateway : 172.16.1.254
DNS server : 172.16.1.129 (config à faire)
Start IP 172.16.1.80 (laisse les 80 premiere adresses de libres)
Subnet : 255.255.255.0

Maximum d'users (dans ce TP : 20)

faire de même pour l'ensemble des VLAN

Depuis le routeur : 

Sélectionner l'interfaces :

```
ip helper-adress (adresse du serveur)
```

![[Pasted image 20250304112131.png]]

faire de même pour l'ensemble des vlan

#### **DNS**

Depuis le serveur du DHCP (172.1.2.129)

![[Pasted image 20250304111858.png]]

172.16.2.130 correspond à mon site web 

