
172.16.0.0/23 (global)

SALES x200
R&D x50 
MGT x25
IT x10
PRINTERS x10
SERVERS x10 

# Découpage adresse IP 

SALES : 172.16.0.0 - 172.16.0.255
R&D : 172.16.1.0   - 172.16.1.63
MGT : 172.16.1.64  - 172.16.1.95
IT : 172.16.1.96  - 172.16.1.111
PRINTERS : 172.16.1.112 - 172.16.1.127
SERVEURS : 172.16.1.128 - 172.16.1.145

---
### CORRECTION

Décimal : 4 bloc avec des symboles de 0 à 9 
	soit 10 symboles = 10 puissance 4 = 10 000 (9999 + 0)

Binaire : 4 bloc avec 2 symboles (0 et 1)
	soit 2 symboles différents = 2 puissance 4 = 16 

Conversion : 
1 0 1 0 1 1 0 1 (bit) = 128 64 32 16 8 4 2 1 = 1x128 + 1x32 + 1x8 + 1x4 + 1x1

1234 en décimal = 1000 100 10 1 = 1x1000 + 2x100 + 3x10 + 4 

1234(10) =

| 1024 | 512 | 256 | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| ---- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1    | 0   | 0   | 1   | 1   | 0   | 1   | 0   | 0   | 1   | 0   |
1234 - 1024 = 210 - 128 = 82 - 64 = 18 - 2 = 16 (combien de fois y a t-il la somme dans le chiffre)

	= 4 D 2 (0 1 0 0 = 4 / 1 1 0 1 = D / 0 0 1 0 = 2 )
---

| 0   | 0   | 0   | 0   | 0   |
| --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 1   | 1   |
| 0   | 0   | 1   | 0   | 2   |
| 0   | 0   | 1   | 1   | 3   |
| 0   | 1   | 0   | 0   | 4   |
| 0   | 1   | 0   | 1   | 5   |
| 0   | 1   | 1   | 0   | 6   |
| 0   | 1   | 1   | 1   | 7   |
| 1   | 0   | 0   | 0   | 8   |
| 1   | 0   | 0   | 1   | 9   |
| 1   | 0   | 1   | 0   | A   |
| 1   | 0   | 1   | 1   | B   |
| 1   | 1   | 0   | 0   | C   |
| 1   | 1   | 0   | 1   | D   |
| 1   | 1   | 1   | 0   | E   |
| 1   | 1   | 1   | 1   | F   |

---
## MODELE OSI

**7 - Applications**
**6 - Présentation**
**5 - Session** ()
**4 - Transport** (Firewall / port(16bits) / Segment)
**3 - Réseau** (rooteur / IPv4 (32bits) et Ipv6(128bits) / Paquets (packet))
**2 - Liaison** (switch / adresse MAC 48bits(24bits +fort numéro constructeur + 24bits + faible numéro de carte unique) / Trame (frame))
**1 - Physique** (câble / fibre / onde électromagnétique / hub (concentrateur))

**4 bits = 16**
**8 bits = 256**
**16 bits = 65 536**
**24bits = 16M**
**32bits = 4Milliards** 

---

IPV4 :

![[Pasted image 20241104105320.png]]

## DECOUPAGES DE PLAGES D'ADRESSE IPv4

**22 = 1024**
**23 = 512**
**24 = 256** 
**25 = 128**
**26 = 64**
**27 = 32**
28 = 16
29 = 8
30 = 4
31 = 2
32 = 1
33 = 0 ? 

172.16.0.0/23 - 172.16.0.0 >> 172.16.1.255 (global)

==**Sous réseaux :**== 
SALES x200 adresses
R&D x50 adresses
MGT x25 adresses
IT x10 adresses
PRINTERS x10 adresses
SERVERS x10 adresses

![[thumbnail_IMG_3618 1.jpg]]

---

Il faut un bloc de 256 adresses (pour les 200 postes / 50 postes = 64 / 25 = 32 / 10 = 16)

SALES 200 postes  : **172.16.0.0 -> 172.16.0.255** / **24**
**R&D 50 postes  : 172.16.1.0   - 172.16.1.63 / 26**
MGT 25 postes  : **172.16.1.64  - 172.16.1.95 / 27**
IT 10 postes : **172.16.1.96  - 172.16.1.111 / 28** 
PRINTERS 10 postes : **172.16.1.112 - 172.16.1.127 / 28**
SERVEURS 10 postes  : **172.16.1.128 - 172.16.1.143 / 28**

---

## CONFIGURATION PACKET TRACER

![[Pasted image 20241104160024.png]]

VTP (virtual tracking protocol)

Un lien qui véhicule plusieurs infos de plusieurs VLAN 
Les interfaces peuvent entre en mode "accès" (pc,serveurs, etc ...)
Entre routeur et switch ne peux pas être en mode accès mais en mode trunk

protocole IEEE (802.1q) 

	Il permet de modifier la trame Ethernet au niveau de la [couche MAC](https://fr.wikipedia.org/wiki/Mod%C3%A8le_OSI "Modèle OSI") afin de fournir un mécanisme d'étiquetage de trame très répandu et implanté dans de nombreux équipements de marques différentes. Il permet de propager plusieurs [VLAN](https://fr.wikipedia.org/wiki/VLAN "VLAN") sur un même lien physique (trunk). [Shortest Path Bridging](https://fr.wikipedia.org/wiki/Shortest_Path_Bridging "Shortest Path Bridging") (IEEE [802.1aq](https://fr.wikipedia.org/wiki/802.1aq "802.1aq")) Incorporé dans l'IEEE 802.1Q-2014[1](https://fr.wikipedia.org/wiki/IEEE_802.1Q#cite_note-1)

Ce standard succède à l'encapsulation [ISL](https://fr.wikipedia.org/wiki/Cisco_Inter-Switch_Link "Cisco Inter-Switch Link") [propriétaire](https://fr.wikipedia.org/wiki/Logiciel_propri%C3%A9taire "Logiciel propriétaire") [Cisco](https://fr.wikipedia.org/wiki/Cisco_Systems "Cisco Systems"). L'en-tête de trame est complété par une balise de 4 octets.

Le standard IEEE 802.1Q définit le contenu de la balise de [VLAN](https://fr.wikipedia.org/wiki/Virtual_LAN "Virtual LAN") (VLAN tag) avec laquelle on complète l'en-tête de [trame](https://fr.wikipedia.org/wiki/Trame_(informatique) "Trame (informatique)") [Ethernet](https://fr.wikipedia.org/wiki/Ethernet "Ethernet"). 


ctrl+z / wr (pour save)
configure terminale - conf t (pour rentrer mode modif)
enable - en (activer les modif)

### Config switch : 
(à faire sur tous les switchs)

![[Pasted image 20241104160809.png]]

Configuration autre sw (non principal)

![[Pasted image 20241105095421.png]]

Retour switch 1 (serveur) saisit VLAN 

![[Pasted image 20241104161512.png]]

Vérif des VLAN :

![[Pasted image 20241104161622.png]]

mode trunk : (à faire sur tous les switch) 

![[Pasted image 20241104162201.png]]

Changer les "ports"
int range F0 XXX = selectionne les ports
switch mode accès (bascule en mode accès)
switch acces vlan 10 / 20 / 30 etc ... 

![[Pasted image 20241104163632.png]]

### Création interface virtuelle routeur

***Sous interface virtuelle (rooteur) = G0/0/1 = G0/0/1.10 (VLAN10) .20 (VLAN20) etc ... ***

Enable -> Configure terminal (conf t) -> Host R-1 -> int G0/0/1 -> no shut -> exit 

---
Création des sous interfaces : 

int G0/0/1.10 (vlan10)

![[Pasted image 20241105085903.png]]

Ip add (vlan10) : 

SOUS INTERFACE : 

int G0/0/1.10
encapsulation dot 10
remettre ip add : 172.16.0.254 255.255.255.0
exit 

![[Pasted image 20241105094026.png]]

int G0/0/1.20 
enc dot 20
ip add 
exit 

![[Pasted image 20241105094435.png]]

**creation bloc note** puis copier / coller (dans CLI routeur)

![[Pasted image 20241105094449.png]]

faire ping les différents appareils entre eux pc / imprimantes /  etc .. 

ipconfig -> ping la passerelle de chq vlan
ping les ip des imprimantes depuis un cmd




