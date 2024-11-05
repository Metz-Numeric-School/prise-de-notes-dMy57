Plusieurs niveaux de maintenance qui ont été définit par (AFNOR -  association françaises de normalisation)  - 60-010 et 60-11 


Plusieurs nv de maintenance : (1 à 5) 

1 = action simple *(changer un écran)*
2 = opération mineure *(changer une connectique ou autres)*
**1 et 2 = pas besoin de test ou diagnostic**

3 = opération avec diagnostics *(changement DD, mémoire, etc ...)*
4 = travaux importants de maintenance *(configuration routeur à distance en système de réseaux NAT car engendre un redémarrage du serveur - en équipe, encadré par un tech*
5 = Travaux et rénovation et de réparation *(changement de serveur, rénovation, réparation)*


# Les types de maintenances 

Les normes française ont été définis par AFNOR
**Corrective** = qui sont consécutives à une défaillance et les actions (panne à eu lieu) 
**Préventive** = destinées à réduire la probabilité d'une défaillance (anticipation de la panne)

![[Pasted image 20241006145533.png]]

Les maintenances **préventives** peuvent être divisé par 2 catégories : 

- **Systématique** : effectuée selon un planning ou échéancier construit selon le temps de l'utilisation du bien ainsi que sur les données statistiques ou historiques des défaillances, fiabilités, etc ...

*  **Conditionnelle** : qui est subordonnée à la survenue d'un évènement (déclencheur)  qui peut être un diagnostic, une alarme, un niveau d'usure, etc ...

**Règle du 3 2 1** = *3 copies dont 2 support différent et 1 externe*
**Depuis 2013** : *3 2 1 1 0 = 3 copies dont 2 support différent - 1 externe - 1 en dehors du réseau - 0*

Maintenance corrective = réparation ou dépannage 

	dépannage = maintenance palliative ou dépannage pour solution provisoire 
	réparation = maintenance curative qui répare de manière définitive les causes et conséquences de la défaillance 



# LE COUT D'UNE PANNE 


**Coûts direct** :   Temps passé au cout de main d'œuvre des technicien 
			Intervention éventuelle d'expert externes 
			Pièces de rechanges 

**Coûts indirect** : Pièces rebutées à cause de la panne
			 Reprise ou retouche de ces pièces
			 Remplacement des pièces rebutées
			 Perte de production durant l'arrêt 
			 Pénalités éventuelles liées au retard de livraison 
			 Coût de la main d'œuvre inoccupée par la panne ..

Ces coûts seront d'autant plus important que la machine est une ressource critique dans le processus.

# LES CRITERES DE CHOIX : 


Il faut définir les critères de choix : 

* Il faut vérifier si certaines machines n'en sont pas exclus d'office, du fait d'actions à venir, comme par exemple : la machine sera ferraillée ou rénovée sous peu.

#### L'APPRECIATION DU RISQUE : 

**Le premier critère de choix** est l'importance des conséquences ou répercutions d'une panne.
Certains équipements ou machines ne doivent pas tomber en panne, car les conséquences économiques, qualitatives ou environnementales sont importantes :

**Economique** = perte d'exploitation et pénalités de retard pour un fournisseur de l'industrie auto

**Qualitative** = l'arrêt et le redémarrage ont une incidence sur la qualité des produits sans que la détérioration soit directement visible 

**Environnementale** = le retraitement d'effluent (fumées, fluides, ...) ne peut se faire durant la panne, libérant ces effluents dans l'environnement 

**Risque inacceptable** (PCA) : supprimer les causes de panne et supprimer les effets des pannes résiduelles

**Risque ~~acceptable si limité** : choisir entre maintenance préventive systématique~~ et maintenance conditionnelle

**Risque acceptable** : prévention inutile 

Plan de continuité d'activité (PCA), **a pour but de garantir la survie de l'entreprise en cas de sinistre important touchant le système informatique**. 
Il s'agit de redémarrer l'activité le plus rapidement possible avec le minimum de perte de données.

#### L'IMPORTANCE DE LA MACHINE

**Le second critère** de choix et l'importance de a machine ou de l'équipement considéré.

Si cette ressource est rare et **"précieuse"** , stratégique pour l'entreprise, si on ne peut délester sa charge sur d'autres machine ou recourir à la sous-traitance, l'entreprise est fortement dépendante de cette ressource, qui est donc très importante. 

A l'opposé, si la machine est banale, que sa charge peut aisément être transférée vers une autre machine ou vers la sous-traitance, cette ressource sera considérée peu importante. 
Il est clair que la politique de maintenance sera radicalement différente entre ces deux cas.

####  LA CHARGE DE LA MACHINE 

**Le troisième critère** à prendre en compte est la charge relative de la machine.

Si la machine est saturée, chargée à 100% l'impact d'un arrêt n'est pas le même que pour une machine dont la charge est faible.

Cette dernière affirmation étant à relativiser en fonction de la capacité à rattraper le retard généré par la panne.

# ANALYSE MULTICRITERES 

Echelle de valeur allant de 1 à 4 par exemple : 

| Critère / valeur       | 4            | 3                                       | 2                                                  | 1                             |
| ---------------------- | ------------ | --------------------------------------- | -------------------------------------------------- | ----------------------------- |
| Risque (R)             | innaceptable | répercution graves sur qualité / délais | Répercutions rattrapables (retouches, retards... ) | Risque faible ou aucun risque |
| Importance machine (I) | stratégique  | importante                              | banale                                             | peu importante                |
| Charge machine (C)     | saturée      | forte > 95 %                            | moyenne (80-95%)                                   | faible < 80 %                 |
**On calcule son facteur machine : facteur machine = R x I x C**


Il est alors possible d'établir 3 classes en fonction du facteur machine

- A = équipement critiques = maintenance conditionnelle
- B = ordinaires = maintenance préventive 
- C = banales = Maintenance curative 


# LA DISPONIBLITE DE LA MACHINE 

Dans la terminologie normative, l temps requis d'aptitude d'un bien désigne le temps durant lequel l'utilisateur exige quel le bien (machine, équipement) soit apte à remplir une fonction requise. 
![[Pasted image 20241006150922.png]]

Or durant ce temps, plusieurs phénomènes peuvent affecter la disponibilité sans que cela soit nécessairement du à un manquement du service de maintenances.

**Exemple :** la non sollicitation du moyen bien qu'il soit apte (temps d'attente) ou le temps d'indisponibilité pour causes externes (panne sur réseau de distribution électrique) bien que le bien ou le moyen soit lui même apte à remplir sa fonction.

# LA RESPONSABILITE DE LA MAITENANCE 

La responsabilité de la maintenance est encadrée dans le schéma précèdent à l'indisponibilité pour cause de panne ou d'intervention.

Les leviers à disposition de la maintenance pour améliorer la disponibilité sont la fiabiltié et la réactivité d'intervention en cas de défaillance.

Ces deux leviers s'apprécient respectivement au travers des indicateurs MTBF et MTTR

# L'INDICE DE FIABILITE MTBF

MTBF = le temps moyen entre défaillance con consécutives  
 = somme des temps de bon fonctionnement / nombre de défaillances 

La somme des temps de bon fonctionnement inclut les temps d'arrêt hors défaillance et les temps de micro arrêts.

Le MTBF peux s'exprimer en unités plus parlantes pour les opérationnels, 
par exemple : nbr de pannes pour 100h de production.

# L'INDICE DE FIABILITE MTTR 

MTTR = Mean Time To Repair (temps moyen pour réparer) exprime la moyenne des temps de tâches de réparation.

Il est calculé en additionnant les temps actifs de maintenance ainsi que les temps annexes de maintenance, le tout divisé par le nbr d'interventions.

**MTTR = temps d'arrêt total / nbr d'arrêts

![[Pasted image 20241006152709.png]]

La maintenabilité s'entend pour une entité utilisée dans des conditions données comme la probabilité pour qu'une opération donnée de maintenance puisse être effectuée sur une intervalle de temps donné, lorsque la maintenance est assurée dans les conditions données avec l'utilisation de procédure et moyens prescrits. 

# LE TAUX DE DISPONIBILTE 

La notion de disponibilité exprime la probabilité qu'une entité soit en état de "disponibilité" dans des conditions données à un instant donné en supposant que la fourniture des moyens extérieurs soit assurée (NFX 60-010 - permet de classifier les actions de maintenance industrielle en différents niveaux)

La disponibilité ou taux de disponibilité est le rapport du "temps effectif de disponibilité" / temps requis

Ou encore le rapport du temps de fonctionnement / (temps de fonctionnement + temps propre d'indisponibilité ) 

La disponibilité s'exprime en fonction des indicateurs précédents de la manière suivante : 

Disponibilité = MTBF / (MTTR + MTBF) 


# BESOIN EN DISPONIBILITE 

1. Faible : taux de disponibilités > 95%
		36h par mois ou de 18j par an
2. Significatif : taux de dispo > 99%
		7h par mois ou de 3.5j par an
3. Important : taux de dispo > 99.5 %
		3h30 par mois ou de 2j par an
4. Critique : taux de disponibilité > 99.9 %
		40 min par mois ou de 08h30 par an

Le Service Level Agreement (SLA) est **une partie de contrat de service entre un prestataire informatique et son client qui définit le niveau de service attendu et les garanties associées**. C'est donc un élément à ne pas négliger lors du choix d'une offre de service managé ou de simple maintenance informatique.

![[Pasted image 20241006153539.png]]

### RECAPITULATIF :

![[Pasted image 20241006153637.png]]

# LES METHODES D'ANALYSE DE RESOLUTION DE PROBLEMES

### Diagramme d'Ishikawa basé sur la règle des 5 M

	- méthode
	- machine
	- main d'œuvre
	- matériel
	- management 


![[ISHIKAWA.png]]

---
### QQOQCCP

moyen mnémotechnique : **CQQCOQP** **(c q q c o q p)**

| Lettre | Question                                                | Exemples                                       |
| :----- | :------------------------------------------------------ | :--------------------------------------------- |
| Q      | de qui, avec qui, pour qui                              | Responsable, acteur, sujet, cible              |
| Q      | Quoi, avec quoi                                         | Outil, objet, résultat, objectif               |
| O      | Ou                                                      | Lieu, service                                  |
| Q      | Quand, tous les quand, à partir de quand, jusqu'à quand | Dates, périodicité, durée                      |
| C      | Comment, par quel procédé                               | Procédures, technique, acttion, moyen matériel |
| C      | Combien                                                 | Quantités, budget                              |
| P      | Pourquoi                                                | Justification, raison d'être                   |
|        |                                                         |                                                |
![[QQCOQP.png]]

---
### PARETO

Courbe de Pareto ou Diagramme 80/20 (seulement possible après avoir récupérés les données)

![[Pasted image 20241006153751.png]]

Méthode ABC :

![[Pasted image 20241006153934.png]]

Cas particulier : 

![[Pasted image 20241006153958.png]]

---
### LA ROUE DE DEMING (PDCA)

Planification -> utilisation de QQOQCP / Brainstorming / Ishikawa / Pareto
Faire -> Réaliser des tâches prévues, Il peut être intéressant de limiter l'ampleur et la portée des tâches à exécuter afin de disposer d'un meilleur controle
Vérifier -> Contrôler, comparer avec les prévisions
Action -> Agir, corriger, prendre les décisions qui s'imposent. Identifier les causes des dérives entre le réalisé et l'attendu. Identifier les nouveaux points d'intervention, redéfinir les processus si nécessaire 

![[ROUE DE DEMING.png]]

Popularisée par **William Edward Deming**, promoteur de la qualité "made in japan" 
4 phases à enchainer afin de s'inscrire assurément dans une logique d'amélioration continue.

Selon l'illustration de Demoing, on représente une cale sous la roue pour éviter de revenir en arrière. Cette dernière symbolise l'entretien d'un systeme formel avec des procédure claire.

#plan
![[Pasted image 20241007162319.png]]

#do 
![[Pasted image 20241007162344.png]]

#act 
![[Pasted image 20241007162427.png]]
 #résumé 
![[Pasted image 20241007162507.png]]

# CALCULS
## EXEMPLE DE GAIN (calculs)

![[Pasted image 20241007162543.png]]

![[Pasted image 20241007162741.png]]