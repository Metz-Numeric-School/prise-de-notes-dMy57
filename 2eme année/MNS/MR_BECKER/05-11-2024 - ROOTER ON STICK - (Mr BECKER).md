int
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
show run 
show vlan brief

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

https://www.ciscomadesimple.be/2010/07/08/configuration-dun-trunk-entre-deux-switch/

Changer les "ports"
int range F0 XXX = selectionne les ports
switch mode accès (bascule en mode accès)
switch acces vlan 10 / 20 / 30 etc ... 

![[Pasted image 20241104163632.png]]

### Création interface virtuelle routeur

***Sous interface virtuelle (rooteur) = G0/0/1 = G0/0/1.10 (VLAN10) .20 (VLAN20) etc ... ***

Enable -> Configure terminal (conf t) -> Host R-1 -> int G0/0/1 -> no shut (permet d'activer) -> exit 

---
Création des sous interfaces : 

int G0/0/1.10 (vlan10)

![[Pasted image 20241105085903.png]]

SOUS INTERFACE : 

int G0/0/1.10 (vlan10) 
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



