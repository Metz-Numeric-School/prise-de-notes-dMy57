
Permet la gérance/le suivi/une vision de l'ensemble des équipement informatique 

Installer un "agent" pour faire "remonter" les postes dans le GLPI.

Pour le matériel dont on ne peux pas télécharger un agent il faut les "rentrer manuellement" (ecran, scanner, etc ..)
		**Créer un fichier CSV pour insérer les données de manières plus efficaces**

OCS inventory pour la gestion de l'inventaire informatique.

GLPI permet également la création de "ticket" pour toutes anomalies des utilisateurs.

	*principe "d'escalade" pour remontage des problèmes en fonction de l'incident*
			probleme interne : si pas resolvable -> au dessus puis ainsi de suite
				service IT interne puis scté de maitenance.


GLPI permet aussi le suivi :

* des licences 
* budget (3eme année-4eme)
* fournisseurs 
* contrats de maintenance/support- alerte date de fin (renouvellement automatique)
* documents (procédure, etc ...)
* Annuaire téléphonique
* Certificats
* Bdd 
* Domaines
* Garantie matériel (alerte avant date de fin)

# LES OUTILS :

* Projets
* Notes
* Base de connaissance (voir des incident qui ont déjà eu lieu) 
* Réservation matériel (voiture, téléphone, etc ...) *planning de réservation*

Utilisateurs on accès seulement à "Assistance" pour créer et suivre ses tickets.

---

VMWARE : (problème connexion)
- supp tt les cartes réseaux
- créer un nouveau reseau VMNET 0
- Affecter VNNET 0 -> Nat
- Vérifier connexion DHCP -> coché
- Adresse du réseau NAT -> 10.10.10
- Appliquer

Setting VMS : choisir custom -> VMNAT0 (NAT)


IP static : /etc/network/interfaces

iface ens33 = carte réseau
adress : 10.10.10.100
netmask : 255.255.255.0
gateway : 10.10.10.2
dns-nameservers 8.8.8.8 4.4.4.4

