
### 🛑 **Déni de service (DoS)**

Dans une attaque DoS, l’attaquant submerge complètement un appareil cible avec de fausses requêtes, créant ainsi un déni de service pour les utilisateurs légitimes.  
Un attaquant peut également **couper ou débrancher un câble réseau** connecté à un appareil critique pour provoquer une panne réseau.  
Les attaques DoS peuvent être **malveillantes** ou **utilisées en combinaison avec d'autres attaques**.

---
### 🌐 **Déni de service distribué (DDoS)**

Une attaque DDoS est une version amplifiée d’une attaque DoS, utilisant **de nombreux hôtes infectés** appelés _zombies_ pour submerger une cible.  
Les attaquants contrôlent ces zombies via un **ordinateur de commande** appelé _handler_.  
Un **botnet** est une armée de machines compromises.  
Les botnets peuvent :

- Rester inactifs jusqu’à réception d’un ordre.
    
- Être utilisés pour des attaques de **SPAM** ou de **phishing**.
    

---

### 🧠 **Empoisonnement DNS (DNS Poisoning)**

Dans une attaque DNS poisoning, l’attaquant a réussi à **infecter un hôte** pour qu’il accepte de **fausses entrées DNS** pointant vers des serveurs malveillants.  
Le trafic est ensuite redirigé vers ces serveurs afin de **capturer des informations confidentielles**.  
L’attaquant peut ensuite **récupérer ces données** depuis le serveur compromis.

---

### 👥 **Homme du Milieu (Man-in-the-Middle - MitM)**

Dans une attaque MitM sur TCP/IP, l’attaquant **intercepte les communications** entre deux hôtes.  
S’il réussit, il peut :

- **Capturer et lire les paquets**,
    
- **Les modifier**,
    
- **Les renvoyer**, créant ainsi un détournement silencieux.  
    Ces attaques peuvent être créées à l’aide de techniques de **spoofing ARP (ARP poisoning)**.
    

---

### 🔁 **Attaque par relecture (Replay Attack)**

Une attaque par relecture est un type d’attaque de **spoofing** où l’attaquant a :

- Capturé un paquet authentifié,
    
- Modifié son contenu,
    
- Renvoyé ce paquet à sa **destination d’origine**.  
    Objectif : **faire accepter ce paquet comme authentique** par la machine cible.
    

---

### 🎭 **Spoofing (usurpation d’identité)**

Dans une attaque TCP/IP de spoofing, l’attaquant **falsifie les adresses IP**.  
Exemple : un attaquant usurpe l’adresse IP d’un hôte de confiance pour **accéder à des ressources** sans autorisation.

---

### 🌊 **Attaque SYN Flood**

Une attaque SYN flood est un type d’attaque DoS qui **exploite le mécanisme de la poignée de main TCP en trois étapes (three-way handshake)**.  
L’attaquant envoie en continu de **fausses requêtes SYN** à la cible.  
La cible est submergée et **incapable de traiter les requêtes légitimes**, provoquant ainsi une **attaque de déni de service**.