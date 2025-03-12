
##### ACL Standard :
- Numérotée :  1 à 99 et 1300 à 1999
- Filtrage : IPv4 Source 
- Se positionne le plus proche de la destination 
#### Etendue : 
- Numérotée : 100 à 199 et 2000 à 2699
- Nommée :
- Filtrage : IPv4 Source & Destination | IPv6 Source et Destination
	- Ports
	- Protocoles
	- MAC adresses(options)
- Se positionne le plus proche de la source

#### Mots clés : 
- Any
- Host : 
- *Established (ACL Etendue)*

#### Wild Card (inverse du subnet mask)

Un masque de **wildcard** permet de spécifier quelle partie de l'adresse IP doit être comparée. Le masque **0.0.0.255** indique que seuls les 24 premiers bits (l'adresse réseau) doivent correspondre, et les 8 derniers bits (l'adresse d'hôte) peuvent varier.
##### Exemple calcul :

| 255. | 255. | 255. | 255. |     |
| ---- | ---- | ---- | ---- | --- |
| 255. | 255. | 255. | 0.   | /24 |
| 0.   | 0.   | 0.   | 255  |     |

| 255. | 255. | 255. | 255. |     |
| ---- | ---- | ---- | ---- | --- |
| 255. | 255. | 255. | 192. | /26 |
| 0.   | 0.   | 0.   | 64.  |     |

---

ACL sont composées d'ACE (Acces Controle Elements) *(règle qui est mis dans une liste)*

Access-list :
Ip access-list :

#### Vérification : 

Show access-list
Show ip interface

----

### Exercices ACL :

### 4.1.4 :

PC1 doit ping PC4 ou DNS Server
![[Pasted image 20250305094619.png]]

**Pour retirer une règle :**

Dans le Router (R1) -> CLI ;

(permet de voir les ACL en place)
```
sh access-lists
```

![[Pasted image 20250305095103.png]]

- First line : La première ligne de la liste de contrôle d'accès (ACL) bloque tous les paquets provenant du réseau 192.168.10.0/24, y compris les échos ICMP (requêtes ping).

- Second Line : permet à tout autre trafic IP, quelle que soit sa source, de traverser le routeur.

**Pour qu'une liste de contrôle d'accès (ACL)** ait un impact sur le fonctionnement du routeur, elle doit être appliquée à une interface dans une direction spécifique. 
Dans ce scénario, l'ACL est utilisée pour filtrer le trafic sortant d'une interface. 
Par conséquent, tout le trafic quittant l'interface spécifiée de R1 sera inspecté par l'ACL 11.

Bien qu'il soit possible d'afficher les informations IP avec la commande `show ip interface`, il peut être plus efficace dans certaines situations d'utiliser simplement la commande `show run`

```
show run | include interface|access 
``` 

![[Pasted image 20250305102606.png]]

#### Remove access list :

Sélection de l'interface :

```
interface s0/0/0
```

Supprimer l'ACL de l'interface sélectionné :

```
no ip access-group 11 out
```

En mode de configuration "normal" sans sélection de l'interface :

```
no access-list 11
```

PC1 pourra ainsi ping PC4 et DNS Server 

---
### 5.1.8 :

![[Pasted image 20250305104108.png]]

- Le réseau **192.168.11.0/24** **ne doit pas** avoir accès au **serveur Web** sur le réseau **192.168.20.0/24**.
- Tout autre accès est **autorisé**.
- une **ACL standard** doit être créée sur **R2**.  
- L'ACL doit être appliquée sur **l'interface sortante vers le serveur Web**.  
- Une **deuxième règle** doit être ajoutée pour **autoriser tout autre trafic**.
---
- Le réseau **192.168.10.0/24** **ne doit pas** pouvoir communiquer avec le réseau **192.168.30.0/24**.
- Tout autre accès est **autorisé**.
- une **ACL standard** doit être créée sur **R3**.  
- L'ACL doit être appliquée sur **l'interface sortante vers PC3**.  
- Une **deuxième règle** doit être ajoutée pour **autoriser tout autre trafic**.

Sur R2 : 

Création de l'ACL :

```
access-list <numéro_ACL> deny 192.168.11.0 0.0.0.255
```

Par défaut, une liste de contrôle d'accès (ACL) bloque tout le trafic qui ne correspond à aucune règle. Pour autoriser tout autre trafic, configurez l'instruction suivante :

```
access-list <numéro_ACL> permit any  
```

Avant d'appliquer une liste de contrôle d'accès (ACL) à une interface pour filtrer le trafic, il est recommandé de **vérifier le contenu de la liste d'accès** afin de s'assurer qu'elle filtrera le trafic comme prévu.

```
sh access-lists
```

![[Pasted image 20250305105643.png]]

Pour que l'ACL filtre réellement le trafic, elle doit être appliquée à une opération du routeur. Appliquez l'ACL en la plaçant pour le trafic **sortant** sur l'interface **GigabitEthernet 0/0** avec la commande suivante :

```
interface GigabitEthernet0/0  
```
```
ip access-group <numéro_ACL> out  
```

🔹 **Remarque :** Dans un réseau en production, **il n'est pas recommandé** d'appliquer une ACL non testée sur une interface active. Il est préférable de la tester dans un environnement contrôlé avant de l'implémenter.

### 5.1.9 :

![[Pasted image 20250305110734.png]]

- Le **serveur de fichiers** contient la **base de données** pour les applications Web.
- Seuls **le poste de travail du Web Manager (PC1)** et **le serveur Web** doivent pouvoir accéder au **serveur de fichiers**.
- **Tout autre trafic** vers le **serveur de fichiers** doit être **bloqué**.

Créez une ACL nommée **File_Server_Restrictions** :

```
ip access-list standard File_Server_Restrictions
```

Ajoutez une règle pour **autoriser PC1 (192.168.20.4)** à accéder au serveur de fichiers :

```
R1(config-std-nacl)# permit host 192.168.20.4
```

Ajoutez une règle pour **autoriser le SvWeb (192.168.100.100)** à accéder au serveur de fichiers :

```
R1(config-std-nacl)# permit host 192.168.100.100
```

Appliquer l'ACL nommée 

Appliquer l'ACL sortante sur l'interface Fast Ethernet 0/1 :

```
interface FastEthernet 0/1
```

```
ip access-group File_Server_Restrictions out
```
Cette commande applique l'ACL **File_Server_Restrictions** **en sortie** sur l'interface **FastEthernet 0/1**. Cela signifie que tout le trafic sortant de cette interface sera filtré en fonction des règles définies dans l'ACL (autoriser seulement les hôtes **192.168.20.4** et **192.168.100.100**, bloquer les autres).

### 5.2.7

![[Pasted image 20250305133311.png]]

- configurer des règles de filtrage pour deux sites d'entreprise, représentés par **R1** et **R3**.

La direction a établi certaines **politiques d'accès** entre les réseaux locaux (LAN) situés sur **R1** et **R3**, que vous devez implémenter. 
Le **routeur Edge** qui se trouve entre **R1** et **R3**, fourni par l'ISP, ne doit pas avoir d'ACL appliquées. Vous n'aurez aucun accès administratif au **routeur Edge**, car vous ne pouvez gérer que votre propre équipement.

### 1. access-list 1 remark Allow R1 LANs Access

- **`access-list 1`** : Cette commande crée une **ACL numérotée** (Access Control List) avec le numéro **1**. Les ACL numérotées dans le cas d'une ACL standard sont des ACLs qui filtrent en fonction de l'adresse source des paquets.
- **`remark`** : Il s'agit d'un **commentaire** qui permet de décrire ce que fait l'ACL. Ce commentaire ne sera pas exécuté, mais il est utile pour la documentation ou pour vous rappeler ce que l'ACL est censée faire.
- **`Allow R1 LANs Access`** : Ceci est le texte du commentaire. Dans ce cas, cela signifie que l'ACL est destinée à permettre l'accès des réseaux locaux de **R1**.


Access-list 1 permit 192.168.10.0 0.0.0.255 :

- **`permit`** : Cette instruction signifie que l'ACL **autorise** le trafic correspondant à cette règle.
- **`192.168.10.0`** : C'est l'adresse réseau **source** que cette règle concerne, ici le réseau **192.168.10.0/24**.
- **`0.0.0.255`** : Le **masque de wildcard**. Le masque **0.0.0.255** est l'inverse du masque de sous-réseau **255.255.255.0**. Cela signifie que seuls les 24 premiers bits (c'est-à-dire l'adresse du réseau) doivent correspondre, et les 8 bits restants (l'adresse de l'hôte) peuvent varier. En d'autres termes, cela permet à **tous les hôtes du réseau 192.168.10.0/24** d'être autorisés à accéder à la destination.

Access-list 1 permit 192.168.20.0 0.0.0.255 :

- **`permit`** : Comme la commande précédente, cette règle autorise le trafic.
- **`192.168.20.0`** : L'adresse réseau **source** concernée, ici le réseau **192.168.20.0/24**.
- **`0.0.0.255`** : Encore une fois, le **masque de wildcard** permet à **tous les hôtes** du réseau **192.168.20.0/24** d'accéder à la destination, en permettant toute variation des derniers 8 bits (les adresses d'hôte).

### **`R3(config)# access-list 1 deny any`**

- **`deny`** : Cette instruction signifie que l'ACL **refuse** le trafic qui correspond à cette règle.
- **`any`** : Le mot-clé **any** fait référence à **tout** le trafic, quel que soit l'adresse source ou la destination.

![[Pasted image 20250305140321.png]]

### **1. Créer une ACL nommée standard qui respecte la politique suivante** :

**Politique** :

- Permettre à tout le trafic provenant du réseau **192.168.40.0/24** d'accéder au réseau **192.168.10.0/24**.
- Permettre uniquement à **l'hôte PC-C** d'accéder au réseau **192.168.10.0/24**.

Le nom de cette liste d'accès doit être **BRANCH-OFFICE-POLICY**.

```
R1(config)# ip access-list standard BRANCH-OFFICE-POLICY
R1(config-std-nacl)# permit host 192.168.30.3
R1(config-std-nacl)# permit 192.168.40.0 0.0.0.255
R1(config-std-nacl)# end
R1#
```

**Explication des commandes** :

1. **`ip access-list standard BRANCH-OFFICE-POLICY`** : Crée une ACL nommée **BRANCH-OFFICE-POLICY** de type **standard**, ce qui signifie qu'elle filtre le trafic uniquement sur la base de l'adresse source.
    
2. **`permit host 192.168.30.3`** : Permet à l'hôte **PC-C** (dont l'adresse est **192.168.30.3**) d'accéder à tout le réseau **192.168.10.0/24**.
    
3. **`permit 192.168.40.0 0.0.0.255`** : Permet à **tous les hôtes** du réseau **192.168.40.0/24** d'accéder au réseau **192.168.10.0/24**. Le masque de **wildcard** **0.0.0.255** signifie que tous les hôtes de ce sous-réseau sont autorisés.
    
4. **`end`** : Termine la configuration de l'ACL.


### **2. Appliquer l'ACL sur l'interface appropriée dans la bonne direction**

Nous appliquons l'ACL sur l'interface **g0/0/0** du routeur **R1**, dans le sens **sortant** (out), pour filtrer les paquets qui quittent cette interface.

```
R1# config t
R1(config)# interface g0/0/0
R1(config-if)# ip access-group BRANCH-OFFICE-POLICY out
```

**Explication** :

1. **`interface g0/0/0`** : Sélectionne l'interface **GigabitEthernet0/0/0** du routeur.
2. **`ip access-group BRANCH-OFFICE-POLICY out`** : Applique l'ACL **BRANCH-OFFICE-POLICY** dans le sens sortant (**out**) de l'interface **g0/0/0**, ce qui signifie que le trafic sortant de cette interface sera filtré selon les règles définies dans l'ACL.

### **3. Vérifier l'ACL**

Pour vérifier que l'ACL est correctement appliquée et que ses règles sont bien enregistrées, on peut utiliser les commandes suivantes.

#### **Commande pour afficher les ACLs configurées** :

```
`R1# show access-lists`
```

**Résultat attendu** :

```
`Standard IP access list BRANCH-OFFICE-POLICY 10 
permit host 192.168.30.3 20 
permit 192.168.40.0 0.0.0.255`
```

---

### MODIFIER UNE ACL STANDARD


- **Tester la connexion**
    
    - Essayez d’envoyer un **ping** depuis **PC-A** vers le serveur **209.165.200.254**.
    - Vous constaterez que le ping **échoue**.
    - La raison est que l’ACL sur **R1** bloque le trafic Internet de retour vers **PC-A**, car l’adresse source des paquets retournés ne fait pas partie de la plage d’adresses autorisées.
    
- **Nouvelle politique de gestion**
    
    - La **direction** a décidé que le **trafic de retour** provenant du réseau **209.165.200.224/27** doit être **autorisé** à accéder entièrement au réseau **192.168.10.0/24**.
    - Tous les **routeurs** doivent suivre des **règles cohérentes**, et donc une **règle "deny any"** doit être ajoutée à la fin de toutes les ACL.
    - Vous devez **modifier l’ACL existante** appelée **BRANCH-OFFICE-POLICY**.


### **Deux options pour modifier l’ACL :**

#### **Option 1 : Supprimer et recréer l’ACL**

- Utiliser la commande :
    
```
    `no ip access-list standard BRANCH-OFFICE-POLICY`
```
    
- Cette commande **supprime complètement** l’ACL du routeur.

- Selon la version de l’IOS Cisco :

    - **Soit** tout filtrage est supprimé et tout le trafic passe librement.
    - **Soit** le filtrage reste actif si l’ACL est encore référencée sur l’interface (**ip access-group** toujours en place).
    
- Une fois l’ACL supprimée, vous devrez **la recréer manuellement** ou **copier-coller depuis un éditeur de texte**.

 ⚠️ **Cette méthode est risquée**, car elle peut temporairement interrompre le filtrage de sécurité.

#### **Option 2 : Modifier l’ACL en place**

- Cette méthode est **plus efficace et plus sûre**, surtout pour des ACL longues.
- Vous pouvez **ajouter ou supprimer des lignes spécifiques** sans devoir tout réécrire.
- **C’est cette option que vous devez utiliser pour cette activité.**

### **Étape 1 : Modifier une ACL standard nommée**

#### **a. Vérification de l’ACL existante sur R1**

Avant toute modification, affichez les ACL configurées avec :

```
R1# show access-lists
```

**Sortie attendue :**

```
`Standard IP access list BRANCH-OFFICE-POLICY 10 permit 192.168.30.3 (8 matches) 20 permit 192.168.40.0 0.0.0.255 (5 matches)`
```

👉 **Cela montre que seuls les hôtes 192.168.30.3 et le réseau 192.168.40.0/24 sont autorisés.**

#### **b. Ajout de nouvelles règles à l’ACL BRANCH-OFFICE-POLICY**

Passez en mode de configuration globale et modifiez l’ACL :

```
R1(config)# ip access-list standard BRANCH-OFFICE-POLICY
R1(config-std-nacl)# 30 permit 209.165.200.224 0.0.0.31
R1(config-std-nacl)# 40 deny any
R1(config-std-nacl)# end
```

✔️ **Explication des commandes :**

- **`30 permit 209.165.200.224 0.0.0.31`**  
    → Autorise le trafic provenant du réseau **209.165.200.224/27** (ce qui inclut **209.165.200.254**, le serveur).
- **`40 deny any`**  
    → Ajoute un **refus explicite** de tout autre trafic.

#### **c. Vérification de la modification**

Exécutez à nouveau :

```
`R1# show access-lists`
```

**Sortie attendue :**

```
`Standard IP access list BRANCH-OFFICE-POLICY 10 permit 192.168.30.3 (8 matches) 20 permit 192.168.40.0, wildcard bits 0.0.0.255 (5 matches) 30 permit 209.165.200.224, wildcard bits 0.0.0.31 40 deny any`
```

👉 **L’ACL a bien été mise à jour avec les nouvelles règles.**

### **Question : Faut-il appliquer l’ACL à l’interface G0/1 sur R1 ?**

❌ **Non**, car l’ACL **BRANCH-OFFICE-POLICY** est **déjà appliquée** sur l’interface. Une modification d’une ACL existante prend effet immédiatement sans avoir besoin de la réappliquer.

### **Test de l’ACL : Vérifier si le trafic du réseau 209.165.200.224/27 est bien autorisé**

1. Depuis **PC-A**, essayez de **pinguer** le serveur à **209.165.200.254** :
    
```
    `PC-A> ping 209.165.200.254`
```
    
2. **Résultat attendu :**
    - ✅ **Si l’ACL est bien configurée**, le **ping réussit**.
    - ❌ **Si l’ACL est mal configurée**, le **ping échoue**.

### **Conclusion**

✔️ **L’ACL a été modifiée avec succès pour permettre le trafic de retour depuis Internet** (209.165.200.224/27).  
✔️ **Le test de ping vérifie que la nouvelle règle fonctionne bien.**

---

# Etendue

![[Pasted image 20250305155233.png]]
#### Step 1: Configure an ACL to permit FTP and ICMP from PC1 LAN.

```
access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp
```

### Explication des éléments de la commande :

1. **access-list 100** → Crée ou modifie une liste d'accès étendue numérotée **100**.
2. **permit tcp** → Autorise le trafic **TCP**.
3. **172.22.34.64 0.0.0.31** → Définit la plage d'adresses source :
    - **172.22.34.64** est l'adresse réseau.
    - **0.0.0.31** est le **masque générique** (wildcard mask), correspondant au sous-réseau **172.22.34.64/27**.
    - Cela inclut les adresses **172.22.34.65 à 172.22.34.94** (PC1 appartient à ce réseau avec l'IP **172.22.34.66**).
4. **host 172.22.34.62** → Désigne une seule destination, en l'occurrence **le serveur FTP (172.22.34.62)**.
5. **eq ftp** → Spécifie que seuls les paquets à destination du **port FTP (21)** sont autorisés.

### Interprétation avec le schéma :

- Cette règle permet aux hôtes du **sous-réseau 172.22.34.64/27** (dont **PC1**) d'établir une connexion **FTP** vers le **serveur 172.22.34.62**.
- D'autres types de connexions (HTTP, SSH, etc.) ou des connexions depuis d'autres sous-réseaux (comme celui de **PC2**) ne seront pas autorisées.

👉 **En résumé :**

- **PC1** (172.22.34.66) pourra **accéder au serveur FTP** (172.22.34.62).
- **PC2** (172.22.34.98) ou d'autres sous-réseaux **ne pourront pas accéder au serveur FTP**.

#### Step 2: Apply the ACL on the correct interface to filter traffic.

```
R1(config)# interface gigabitEthernet 0/0
R1(config-if)# ip access-group 100 in
```

- **`ip`** : fait référence à l'IPv4, ce qui signifie que la commande concerne le filtrage du trafic IP.
- **`access-group`** : cette partie de la commande permet d'appliquer une ACL à une interface réseau. Cela détermine quel trafic IP est autorisé ou rejeté.
- **`100`** : il s'agit du numéro de l'ACL (dans ce cas, 100). Cela signifie que l'ACL 100 est appliquée. Ce numéro peut être entre 1 et 199 pour les ACL standards ou entre 100 et 199 pour les ACL étendues.
- **`in`** : cela spécifie que l'ACL doit être appliquée au trafic entrant sur l'interface réseau.

#### Step 3: Verify the ACL implementation.

a. Ping from PC1 to Server. If the pings are unsuccessful, verify the IP addresses before continuing.
b. FTP from PC1 to Server. The username and password are both cisco.
PC> ftp 172.22.34.62
c. Exit the FTP service.

---

### Part 2: Configure, Apply and Verify an Extended Named ACL
#### Step 1: Configure an ACL to permit HTTP access and ICMP from PC2 LAN.

```
ip access-list extended HTTP_ONLY
```

```
permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www
```

Create a second access list statement to permit ICMP (ping, etc.) traffic from PC2 to Server. Note: The prompt remains the same and a specific type of ICMP traffic does not need to be specified.

```
permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62
```

Sélection de l'interface : 

```
interface gigabitEthernet 0/1
```

```
ip access-group HTTP_ONLY in
```


 
