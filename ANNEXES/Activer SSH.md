
## 🔐 Configuration de SSH sur un commutateur Cisco – Résumé des étapes

### 📌 **Pré-requis :**

Le switch doit avoir :

- Un **nom d’hôte unique**    
- Une **configuration IP de base** (adresse IP, VLAN actif, passerelle)

### ✅ **Étapes de configuration SSH**

### **1. Vérifier la prise en charge de SSH**

```
show ip ssh
```

> Si la commande est inconnue, l’IOS ne supporte pas SSH (version sans crypto).

### **2. Définir le nom de domaine**

```
ip domain-name cisco.com
```

> Le nom de domaine est nécessaire pour générer les clés RSA.

### **3. Générer une paire de clés RSA**

```
crypto key generate rsa
```

> Indique une taille de clé (recommandé : **1024 bits ou plus**).  
> Cela active automatiquement le serveur SSH.

### **4. Forcer la version SSH 2**

```
ip ssh version 2
```

> Plus sécurisée que la version 1, qui est vulnérable.


### **5. Créer un compte utilisateur local**

```
username <admin> secret <ccna>
```

> Ce compte sera utilisé pour l’authentification SSH.

## **6. Configurer les lignes VTY (accès distant)**

```
line vty 0 15
password inutile (car login local)
login local
transport input ssh
```

> Active l’accès uniquement en SSH et exige l’authentification via les comptes locaux.


### 🧪 **Vérification** :

```
show ip ssh
show running-config
```

> Pour vérifier que SSH est activé, et que les lignes VTY utilisent bien `login local` et `transport input ssh`.


### 🧹 **Commande utile (pour réinitialiser les clés RSA)** 

```
crypto key zeroize rsa
```

> Supprime les clés RSA et **désactive SSH** automatiquement.

---

```
S1# show ip ssh
SSH Disabled - version 1.99
%Please create RSA keys (of at least 768 bits size) to enable SSH v2.
Authentication timeout: 120 secs; Authentication retries: 3
S1# configure terminal
S1(config)# ip domain-name cisco.com
S1(config)# crypto key generate rsa
The name for the keys will be: S1.cisco.com
...

How many bits in the modulus [512]: 1024
...

S1(config)# username admin secret ccna
S1(config-line)# line vty 0 15
S1(config-line)# transport input ssh
S1(config-line)# login local
S1(config-line)# exit
S1(config)# ip ssh version 2
S1(config)# exit
S1#
```


---

### SE CONNECTER EN SSH : 

```
ssh -l (L) <user> + ip 
<mdp >
```
