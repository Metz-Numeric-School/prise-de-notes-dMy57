
## Question 1 : Quel est l’objectif principal de la supervision réseau ?
L'objectif d'une supervision réseau est de pouvoir garantir que les outils ont bien été configuré et ainsi superviser les signes vitaux du réseau (la disponibilité, la vitesse et l'utilisation).

## Question 2 : Quels protocoles sont couramment utilisés pour la supervision réseau ?
Les protocoles couramment utilisés sont :
- SNMP (Simple Network Management Protocol)
- WMI (Windows Management Instrumentation)
- Flow (IPFIX, NetFlow, Sflow,Jflow)
- Packet Sniffing 

## Question 3 : Quel est l’avantage principal de PRTG par rapport à d'autres outils de supervision ?
L'avantage de PRTG est qu'il s'agit d'un interface simple d'utilisation et intuitives.

## Question 4 : Que permet de superviser PRTG ?
PRTG permet de superviser le réseau dans son ensemble (Serveurs, imprimantes,pc, ...) également de surveiller le trafic, les disques dur, le CPU etc ... 

## Question 5 : Quels types de notifications PRTG peut-il envoyer ?
PRTG peut envoyer des notifications par e-mail, sms, via Teams, messages syslog ou SNMP Trap, notifications IOS ou android vers l'application PRTG.

## Question 6 : Dans PRTG, qu’est-ce qu’un capteur ?
Un capteur est un élément de supervision. Il surveille une valeur mesurée dans le réseau comme le trafic d'un port de commutateur, la charge d'un processeur, d'un serveur etc ...

## Question 7 : Quel protocole est recommandé pour surveiller l’utilisation de la bande passante avec PRTG ?
sFlow ou Netflow sont recommandé pour surveiller la bande passante.

## Question 8 : Comment PRTG peut-il détecter une anomalie ?
Grâce aux capteurs qui détectent une anomalie et lance une alerte.

## Question 9 : Que signifie "temps de disponibilité" dans un contexte de supervision ?
Le temps de disponibilité signifie la durée pendant laquelle un service / équipement est opérationnel.

## Question 10 : Quels types d’équipements peuvent être supervisés par PRTG ?
PRTG peux superviser les routeurs, les switchs, les workstations, les serveurs, les racks de serveurs, les systèmes NAS et le SANs
Des routeurs, commutateurs, serveurs, pare-feu, postes de travail, imprimantes, et bien d’autres.

## Question 11 : Quelle fonctionnalité n’est pas offerte par PRTG ?
L’analyse de vulnérabilités (PRTG est orienté supervision, pas sécurité).

## Question 12 : Quel rôle joue le SNMP dans la supervision ?
SNMP permet de supervisier l'infrastructure réseau et fournit aux admini une visiblité centrée sur les périphériques.
## Question 13 : Dans PRTG, que représente une "sonde"(probe) ?
Une sonde est l'endroit où la surveillance proprement dite a lieu

## Question 14 : Que signifie "MTTR" dans la supervision ?
MTTR signifie Mean Time To Repair (ou le temps moyen nécessaire pour réparer une panne.)

## Question 15 : Quelle est la limite de capteurs pour la version gratuite de PRTG ?
La limite de capteur en version gratuite est limitée à 100 capteurs.

## Question 16 : Que permet un tableau de bord personnalisé dans PRTG ?
Le tableau de bord personnalisé permet d’afficher des éléments spécifiques en temps réel selon nos besoins.

## Question 17 : Quelle commande permet de vérifier la connectivité réseau depuis PRTG ?
La commande Ping permet de vérifier la connectivité réseau.

## Question 18 : Que signifie une alerte "latence élevée" dans PRTG ?
Une alerte latence élevée signifie qu’un temps de réponse inhabituellement long a été détecté sur le réseau ou sur un service.

## Question 19 : Pourquoi utiliser un système de supervision ?
L'utilisation d'un outil de supervision permet de prévenir les pannes, optimiser les performances, et assurer la disponibilité des services critiques.

## Question 20 : Quels rapports peuvent être générés avec PRTG ?
Des rapports sur la disponibilité, l’utilisation de la bande passante, les performances, et les erreurs.

## Question 21 : Quelle méthode permet à PRTG de surveiller des sites web ?
Grâce à l'utilisation des capteurs HTTP ou HTTPs pour surveiller les sites web.

## Question 22 : Quelle est la différence entre un capteur et une sonde dans PRTG ?
Un capteur surveille un aspect spécifique d’un équipement alors qu’une sonde collecte les données de plusieurs capteurs.

## Question 23 : Quel est un exemple de métrique que PRTG peut surveiller ?
La charge CPU d’un serveur.

## Question 24 : Que signifie SLA en supervision réseau ?
SLA signifie Service Level Agreement ce qui veut dire définit les niveaux de service attendus.(réactivité, responsabilités, etc ...)

## Question 25 : Quels outils permettent une supervision basée sur des flux réseau ?
Les outils suivants permettent de superviser les flux du réseau par exemple : 
- NetFlow
- Flow
- jFlow

## Question 26 : Quel type d’anomalie peut être détecté avec des outils de supervision comme PRTG ?
Des anomalies comme des pannes, des pics de trafic, ou des latences anormales peuvent être détectés.

## Question 27 : Qu’est-ce qu’un "groupe" dans PRTG ?


## Question 28 : Quel protocole PRTG utilise-t-il pour superviser les performances d’un serveur Windows ?
Le protocole WMI (Windows Management Instrumentation) est utilisé.

## Question 29 : Pourquoi définir des seuils dans PRTG ?
Cela permettrait de détecter lorsque les limites qui ont été prédéfinies sont dépassées 

## Question 30 : Quelle métrique ne peut pas être supervisée directement par PRTG ?


## Question 31 : Que permet de faire la fonction "auto-discovery" dans PRTG ?
La fonction "auto-discovery" permet de détecter automatiquement les équipements.

## Question 32 : Comment PRTG peut-il superviser les performances d’une application spécifique ?
PRTG peut superviser les performances d'une application en utilisant des capteurs dédiés ou en analysant les métriques via des API.

## Question 33 : Quel élément est nécessaire pour configurer un capteur SNMP ?
Vérifier la comptabilité de l'équipement, les versions, etc ...  

## Question 34 : Que mesure un capteur Ping dans PRTG ?
Le capteur de ping mesure le temps de réponse du réseau et la disponiblité d'un appareil ou d'un service.

## Question 35 : Quel format de fichier PRTG peut-il utiliser pour exporter des rapports ?
Les rapports de PRTG peuvent être exportés au format PDF, XML ou CSV.
## Question 36 : Pourquoi utiliser des cartes (maps) dans PRTG ?
Les maps sont utiliser pour donner un bon aperçu du réseau en visualisant en temps réel sous forme de graphique.

## Question 37 : Que se passe-t-il lorsqu’un seuil critique est atteint dans PRTG ?
Lorsque qu'un seuil critique est atteint, une alerte est émis pour informer l'utilisateur.

## Question 38 : Quelle fonctionnalité de PRTG permet de surveiller des métriques personnalisées ?
La fonctionnalités des capteurs personnalisées permet cela.
## Question 39 : Quelle est l’utilité des dépendances dans PRTG ?
Les dépendances permettent de réduire les alertes inutiles en liant des capteurs entre eux.

## Question 40 : Que faut-il faire pour surveiller un réseau distant avec PRTG ?
Il faut installer une sonde distante pour collecter des données depuis le réseau distant.
