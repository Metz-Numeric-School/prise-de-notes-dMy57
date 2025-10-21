les tâches suivantes doivent être traitées lors de la configuration des paramètres initiaux d'un routeur.

**Étape 1.** Configurer le nom de l'appareil.

```
Router(config)# hostname <nom_de_l_appareil>
```

**Étape 2.** Sécuriser le mode d'exécution privilégié.

```
Router(config)# enable secret <mot_de_passe>
```

**Étape 3.** Sécuriser le mode d'exécution utilisateur.

```
Router(config)# line console 0
Router(config-line)# password <mot_de_passe>
Router(config-line)# login
```

**Étape 4.** Sécuriser Telnet à distance / accès SSH.

```
Router(config-line)# line vty 0 4
Router(config-line)# password <mot_de_passe>
Router(config-line)# login
Router(config-line)# transport input {ssh | telnet | none | all}
```

**Étape 5.** Sécuriser tous les mots de passe dans le fichier de configuration.

```
Router(config-line)# exit
Router(config)# service password-encryption
```

**Étape 6.** Fournir un avertissement légal.

```
Router(config)# banner motd delimiter message delimiter
```

**Étape 7.** Enregistrer la configuration.

```
Router(config)# copy running-config startup-config
```

**Étape 8.**  Afficher le contenu de la mémoire NVRAM

```
show startup-configuration ou show start
```

---

# 🔒 Sécurisation des accès d’un routeur Cisco

Tous les accès d’un routeur doivent être **sécurisés**, en particulier le **mode d’exécution privilégié**, qui permet un contrôle total de l’appareil et de sa configuration. Il est donc essentiel d’utiliser des **mots de passe forts** pour limiter l’accès à ces modes.

---

## 🔹 Commandes de sécurisation

Les commandes suivantes permettent de sécuriser les accès :

```
R1(config)# enable secret <mot_de_passe>                 
	# Mot de passe du mode privilégié
R1(config)# line console 0                         
	# Sécurisation de la console
R1(config-line)# password <cisco>
R1(config-line)# login
R1(config-line)# exit

R1(config)# line vty 0 4                           
	# Sécurisation de l’accès distant
R1(config-line)# password <cisco>
R1(config-line)# login
R1(config-line)# transport input ssh telnet        
	# Autoriser SSH et Telnet
R1(config-line)# exit

R1(config)# service password-encryption            
	# Chiffrement des mots de passe
```

---

 ⚠️ Bannière d’avertissement légal :

L’avertissement légal informe les utilisateurs que seul le personnel autorisé est autorisé à accéder à l’équipement.

```
R1(config)# banner motd # <le message ("Authorized Access Only!")>) #
```

![[Pasted image 20250508152109.png]]

---
## 💾 Sauvegarde de la configuration

En cas de coupure de courant, toutes les configurations non sauvegardées sont perdues. Il est donc **indispensable d’enregistrer** la configuration en NVRAM :

```
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
```

## Examinez le contenu de la mémoire Flash

```
R1# **show flash**
```

## Enregistrez le fichier de configuration initiale dans la mémoire Flash

```
R1# **copy startup-config flash**

Destination filename [startup-config]
```



---

✅ **Conclusion** : La sécurisation des accès et la sauvegarde de la configuration sont des étapes **fondamentales** pour garantir la protection du réseau et la stabilité de l’infrastructure.