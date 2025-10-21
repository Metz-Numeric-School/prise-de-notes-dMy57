
## 🧑‍💻 Accès aux périphériques Cisco

Pour configurer un **switch** ou un **routeur Cisco**, plusieurs méthodes d’accès existent. Ces accès permettent de manipuler la configuration du périphérique via **l’interface CLI** (ligne de commande).

### 🔌 1. Accès local – Port Console

- Le **port console** est un port physique sur l’équipement utilisé pour un accès direct via un câble console (souvent RJ45–DB9 ou USB–RJ45).    
- Cet accès est **essentiel pour la première configuration**, avant que l’équipement soit connecté au réseau.    
- Il ne nécessite **aucune configuration réseau préalable**.

#### 🔐 Configuration du mot de passe console :

```
Switch(config)# line console 0
Switch(config-line)# password <cisco>
Switch(config-line)# login
```

- `line console 0` : entre dans la configuration de la ligne console.
*  password cisco` : définit le mot de passe (remplaçable par n’importe quel mot).
- `login` : active la demande de mot de passe à la connexion.

---

### 🌐 2. Accès distant – Connexions VTY (SSH/Telnet)

- Une fois le périphérique connecté au réseau, on peut y accéder à distance via **SSH** (sécurisé) ou **Telnet** (non sécurisé).    
- Cet accès utilise les **lignes VTY** (Virtual Teletype), souvent de 0 à 15 (16 lignes).
#### 🔐 Configuration du mot de passe VTY :

```
Switch(config)# line vty 0 15
Switch(config-line)# password <cisco>
Switch(config-line)# login
Switch(config-line)# transport input ssh
```

- `line vty 0 15` : configure toutes les lignes VTY (0 à 15).    
- `password cisco` : définit le mot de passe requis.    
- `login` : impose la demande du mot de passe.    
- `transport input ssh` : limite l'accès à SSH uniquement (plus sécurisé que Telnet).   

 Sur un routeur, il est courant d’avoir seulement `line vty 0 4`, soit 5 lignes.
### 🧠 Que sont les "lignes VTY" ?

- **VTY** = _Virtual Teletype Line_    
- Ce sont **des lignes logiques** utilisées pour les connexions à distance (Telnet ou SSH).    
- Chaque ligne VTY permet **une session distante simultanée**. Donc :    
    - `line vty 0 4` → 5 utilisateurs max en même temps        
    - `line vty 0 15` → 16 utilisateurs max en même temps


### 📌 Exemple pratique :

```
Switch(config)# line vty 0 15 
Switch(config-line)# password monpass 
Switch(config-line)# login 
Switch(config-line)# transport input ssh
````

Cela veut dire :

> "Je définis un mot de passe pour toutes les connexions à distance SSH, et j’autorise jusqu’à 16 sessions simultanées."

---
## 🔐 Chiffrement des mots de passe

Par défaut, les mots de passe apparaissent en **texte clair** dans la configuration (commande `show running-config`).

Pour éviter cela, activez le chiffrement :

```
Switch(config)# service password-encryption
```

- Chiffre tous les mots de passe en clair avec un chiffrement **type 7** (simple, réversible).    
- Il est **fortement recommandé** d'utiliser `enable secret` pour le mode privilégié, qui applique un chiffrement plus fort (type 5 ou 9).

#### Exemple :

```Switch(config)# enable secret itsasecret```

---

## 🧪 Vérification

Pour s'assurer que tout est configuré correctement :

```
show running-config
```

- Vérifie la présence des mots de passe sur les lignes console et VTY.    
- Vérifie que le mot de passe `enable secret` est chiffré.    
- Vérifie que la commande `service password-encryption` est présente.

---

## ✅ Résumé des bonnes pratiques

| Élément à protéger     | Commandes clés                          | Sécurité        |
| ---------------------- | --------------------------------------- | --------------- |
| Accès local (console)  | `line console 0` + `password` + `login` | Moyen           |
| Accès distant (VTY)    | `line vty 0 15` + `password` + `login`  | Moyen à élevé   |
| Accès privilégié       | `enable secret`                         | Fort (type 5/9) |
| Chiffrement global     | `service password-encryption`           | Faible (type 7) |
| Accès sécurisé distant | `transport input ssh`                   | Fort            |