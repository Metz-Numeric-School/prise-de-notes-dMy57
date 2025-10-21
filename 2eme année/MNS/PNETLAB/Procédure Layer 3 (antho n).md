
# 1/ changer les ports sur les Switchs

Après avoir placé chaque composant du réseau, on peut commencer la configuration.
Il est préférable **d'enlever les liaisons** entre chaque switch pour éviter des erreurs de récupération lors de la configuration VTP que nous verrons prochainement.

On effectuera les étapes suivantes **pour chaque switch ainsi que pour le switch layer 3**

## Renommer un switch

```
enable
conf t
hostname SW-L3
```

## Mettre ses ports en mode TRUNK

```
enable
conf t
int range e0/0-1               // selectionne plusieurs interfaces avec range
sw tr encapsulation dot1Q
switchport mode trunk
^c
wr                              // On applique les changement / sauvegarde

```


----


# 2/ Création des VLANs

il faut à présent créer l'ensemble des vlans que l'on à défini au préalable de la configuration.
Ces vlan nous les créerons dans le switch Layer 3 , et ce layer 3 les partagera aux autres switch avec le protocol VTP.

## Créer une VLAN

Sur le Layer 3 : 

```
enable 
conf t
Switch(Config)# vlan 10
Switch(config-vlan)# name Administratif
Switch(config-vlan)# exit
    
Switch(config)# vlan 20
Switch(config-vlan)# name Commercial
Switch(config-vlan)# exit
    
Switch(config)# vlan 30
Switch(config-vlan)# name Technique
Switch(config-vlan)# exit
    
Switch(config)# vlan 40
Switch(config-vlan)# name Imprimantes_Serveurs
Switch(config-vlan)# exit
```


----

# 3/ Configurer le VTP

Pour transmettre les VLANs que nous venons de créer sur le SW-L3 aux autres switch nous devons configurer le vtp mode . Nous mettrons le SW-L3 en **VTP server** et les autres switch en **VTP client**


## Sur le SW-L3

```
enable
conf t
vtp mode server
vtp domain BSRC2
vtp password BSRC2
^c
wr
```

## Sur les autres switchs

```
enable
conf t
vtp mode client
vtp domain BSRC2
vtp password BSRC2
^c
wr
```


Après ça on peut brancher les switch entre eux pour que les vlan puissent être transmise et éviter des délais.



----

# 4/ Configuration des ports en mode access

Pour chaque switch on va définir les port attribué à chaque vlan. Si je veux qu'une vlan 10 occupe 3 ports sur le switch c'est à ce moment que je le définis. 

Je répète cette étape pour chaque vlan sur le switch.

```plaintext
enable
conf t
! Port pour les PC (VLAN 10)
Switch(config)# interface e0/0 - 3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit
```



----

# 5/ Configuration du routage interVLAN

Pour chaque VLAN nous devrons configurer l'adresse ip du sous réseau associé à la VLAN dans le switch Layer 3


## Activer l'IP Routing sur SW-L3

Il est nécessaire de désactiver l'interface de type switch entre le routeur et le SW-L3

```
enable
conf t
interface e0/3
no switchport  // changement le type de port entre le L3 et le routeur
^c
ip routing  // activer l'ip routing
```


## Configurer le routage pour chaque vlan


```
enable
conf t

// pour chaque vlan
Switch(config)# interface vlan 10
Switch(config-if)# no shutdown   // On active l'interface grâce à cette commande

Switch(config-if)# ip address 192.168.10.254 255.255.255.0
Switch(config-if)# exit

// Sauvegarder a la fin NE PAS OUBLIER
^c
wr
```



----

# 6/ Définir les ip pour chaque machine / DHCP


## Définir manuellement 

Il fait maintenant définir les ip pour chaque machine du réseaux connecté aux switchs afin qu'ils puissent se pinger.

```
ip 172.16.0.1/24 172.16.0.254  // ip adresseipMachine adresseipPasserelle
```

après avoir configuré les adresses ip pour chaque machine , il est normalement possible de pinger n'importe quel machine de ce réseaux.



## Définir grâce au DHCP


Sur le SW-L3 : 

```
// à faire pour chaque vlan

Switch(config)# ip dhcp pool VLAN10
Switch(config-dhcp)# network 192.168.10.0 255.255.255.0
Switch(config-dhcp)# default-router 192.168.10.254
Switch(config-dhcp)# exit

// sauvegarder à la fin
^c
wr
```

Après ça , il faut que les machines de chaque vlan respectif soient connectées aux **bon ports du switch sur lequel elle est relié.**

en effet, si dans un switch on définit que les machines connectées sur les ports de e0/0 à e0/3 appartiennent à la vlan 10 alors **les machines connectées sur ces ports recevront une adresse IP de la VLAN grâce au DHCP.**

Pour activer le DHCP il faut se rendre sur le poste en question et effectuer la commande 


```
dhcp -r
save   // important pour que la machine garde l'adresse ip
```

et ensuite la machine reçoit une adresse ip.