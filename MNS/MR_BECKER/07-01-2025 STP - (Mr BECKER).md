
Packet Tracer :

x 2 sw 2960

creation vlan 10 / 20  + repartir les interfaces (12/12)
Assignation des IP

![[Pasted image 20250107111629.png]]

(voir TOPO01)
Dans ce cas le STP ne désactive pas l'interface, il laisser passer les msg (pas de boucle)

---------------------------------------------------------

Génération de boucle : 
1x point reste orange (détection de boucle)
(topo2)
![[Pasted image 20250107112737.png]]
bid = identifiant du bridge (anciennement switch)

1 sw est prioritaire (comment savoir lequel ?)
par défaut le BID d'un sw est de 32 767 en binaire
adresse MAC fait la différence

pour voir quel sw : **sh ver** (show version) puis voir l'adresse MAC 

1ere adresse : 
![[Pasted image 20250107113226.png]]


2eme : 
![[Pasted image 20250107113308.png]]

Plus petite adresse MAC  qui est prioritaire 

----------------------------------------

topo03 : 

Root bridge = vert 

![[Pasted image 20250107114215.png]]

--------------------------------------------------

topo04 : 

![[Pasted image 20250107114908.png]]