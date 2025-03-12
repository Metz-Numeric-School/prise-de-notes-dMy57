
Vidéo : 

* Config noms d'users et les mdp (longueur mdp), privilèges 
* Config commande cryptage du mdp qui cryptera tous les mdp qui ne sont pas déjà cryptés 
	* config délai d'inactivité, blocage de connexion (utile contre les atq par force brute et par dictionnaire) 
	* Création de bannière, très utile à des fins juridique
+ Config accès Telnet (not a good idea) car Telnet est en texte clair et nous allons configurer l'accès SSH, beaucoup mieux car il utilise un cryptage très fort
+ Config de la sécurité du port Switchport

### MOTS DE PASSE :  

Rooter : 

```
sh privilege (permet de voir les privileges)
```

passer en "conf t" 

```
 line console 0 (car il n'y qu'un seul port de console sur le routeur)
```

```
(config-line) password Cisco123!
```

```
login
```

^z 

#### CONFIGURATION DU MDP 

Longueur du mdp : (entre 0 et 16 caractères)

```
passwords min-length 8
```







---
#### Supprimer le mdp : 

On retourne dans le routeur : -> en -> conf t -> line con 0 

```
no password Cisco123!
```

---

6min26




















**Protection contre les attaques**  

- **Timeout automatique** (exec-timeout 1 30) : déconnexion après **1 min 30 sec** d’inactivité.  
    
- **Blocage après plusieurs tentatives échouées** :  
    
- login block-for 120 attempts 5 within 45  
    
- Bloque les connexions après **5 échecs en 45 sec** pendant **2 min** (protection contre les attaques bruteforce).  
    
- **Bannière d’avertissement** :  
    
- banner motd "Accès interdit aux personnes non autorisées"  
    
- Utile pour des raisons **légales** en cas d'intrusion.  
    

**Sécurisation des accès distants**  

- **Telnet** (non sécurisé, en clair) → **désactivé** (transport input ssh).  
    
- **SSH** (sécurisé, chiffré) → **activé** :  
    
- Nécessite un **nom de domaine** (ip domain-name [monentreprise.com](http://monentreprise.com)).  
    
- Génération d’une **clé RSA** (crypto key generate rsa modulus 2048).  
    
- Configuration des **VTY lines** pour exiger SSH (line vty 0 4 login local).  
    

**Protection des ports switch**  

- **Activation de Switchport Security** (switchport port-security).  
    
- **Apprentissage automatique de l’adresse MAC** (switchport port-security mac-address sticky).  
    
- **Détection des appareils non autorisés** :  
    
- violation shutdown → désactive le port si un **MAC inconnu** est détecté.  
    
- **Remise en service manuelle** (shutdown puis no shutdown).  
    

**Conclusion**  
Cette vidéo pose les bases de la **sécurité des équipements Cisco**, couvrant :  

- La **gestion des accès** et **chiffrement des mots de passe**.  
    
- Les **protections contre attaques bruteforce**.  
    
- La **sécurisation des accès distants** avec SSH.  
    
- La **protection des ports switch** contre les périphériques inconnus.
