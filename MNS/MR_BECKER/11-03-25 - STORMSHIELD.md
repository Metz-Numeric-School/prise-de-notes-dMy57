
Installer la VM sur VM Ware

Sélectionner pour le keyboard : 4 

- ajout  4 carte réseau 1ere vm (vmnet 0 - 1 - 3 - 4 ) et 2eme machine (vmnet 0 - 2 -  5 - 6 )
- config avec ip fixe 1er VM 172.16.10.254 / 24 
-  config avec ip fixe 2er VM 172.16.20.254 / 24

Config du mdp : ``Pa$$word``

![[Pasted image 20250402085842.png]]

Config :
Système : Maintenance (mettre le fichier de MAJ 0639A9)
License : (mettre le fichier de Licence 0639A9)

Dans la 2eme VM mettre les autre licences (1212A9)

Dans politique de sécurité : 
Filtrage et NAT
Allez dans l'onglet "10 PASS ALL"

Dans l'onglet NAT -> Nouvelle règle "Règle de partage d'adresse source (masquerading)

Ajout d'une règle : (mettre source "Firewall out" dans trafic après translation)
![[Pasted image 20250311115138.png]]
Appliquer puis test en ouvrant un onglet (on devrait avoir de la connectivité) 









