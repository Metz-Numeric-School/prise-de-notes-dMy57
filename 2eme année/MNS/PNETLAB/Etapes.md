Voici une topologie réseau basée sur le thème d'une **entreprise** avec plusieurs services répartis en **VLANs** pour différents départements. Je vais détailler les équipements, les VLANs, et les étapes pour configurer cette infrastructure.

---

### **Objectif** : Configurer une topologie réseau avec plusieurs VLANs, 3 switchs, et le VTP.

---

### **Matériel requis** :

- **1 Routeur**
- **3 Switchs**
- **6 PC** (2 par switch pour représenter différents départements/services)
- **1 Serveur**
- **1 Imprimante**

---

### **Étapes détaillées**

---

#### **1. Configuration matérielle et câblage**

1. **Reliez les switchs entre eux** :
    - **Switch 1 (serveur VTP)** connecté à **Switch 2** via un câble.
    - **Switch 1** connecté à **Switch 3** via un autre câble.
2. **Reliez les PC, le serveur et l’imprimante** aux ports des switchs :
    - **2 PC** sur **Switch 2** pour le VLAN Commercial.
    - **2 PC** sur **Switch 3** pour le VLAN Technique.
    - **1 Serveur** et **1 Imprimante** sur **Switch 1** pour le VLAN Imprimantes_Serveurs.

---

#### **2. Définition des VLANs et des adresses IP**

| **VLAN ID** | **Nom**              | **Plage IP**    | **Utilisation**        |     |
| ----------- | -------------------- | --------------- | ---------------------- | --- |
| VLAN 10     | Administratif        | 192.168.10.0/24 | Administration         |     |
| VLAN 20     | Commercial           | 192.168.20.0/24 | Département Commercial |     |
| VLAN 30     | Technique            | 192.168.30.0/24 | Département Technique  |     |
| VLAN 40     | Imprimantes_Serveurs | 192.168.40.0/24 | Serveur et Imprimantes |     |

---

#### **3. Configuration des trunks entre les switchs**

Sur chaque switch, configurez les ports de liaison entre les switchs en mode **trunk** pour permettre la propagation des VLANs via le protocole VTP.

##### **Exemple sur Switch 1 (vers Switch 2 et Switch 3)**

```plaintext
Switch> enable
Switch# configure terminal
Switch(config)# interface gi0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit

Switch(config)# interface gi0/2
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
```

Répétez pour **Switch 2** et **Switch 3** sur leurs ports respectifs.

---

#### **4. Configuration du VTP**

##### **Sur Switch 1 (Serveur VTP)**

1. Configurez le switch comme serveur VTP :
    
    ```plaintext
    Switch> enable
    Switch# configure terminal
    Switch(config)# vtp mode server
    Switch(config)# vtp domain EntrepriseVLAN
    Switch(config)# vtp password MonMotDePasse
    ```
    
2. Ajoutez les VLANs sur ce switch uniquement :
    
    ```plaintext
    Switch(config)# vlan 10
    Switch(config-vlan)# name Administratif
    Switch(config-vlan)# exit
    
    Switch(config)# vlan 20
    Switch(config-vlan)# name Commercial
    Switch(config-vlan)# exit
    
    Switch(config)# vlan 30
    Switch(config-vlan)# name Technique
    Switch(config-vlan)# exit
    
    Switch(config)# vlan 40
    Switch(config-vlan)# name Imprimantes_Serveurs
    Switch(config-vlan)# exit
    ```
    

##### **Sur Switch 2 et Switch 3 (Clients VTP)**

Configurez-les en mode **client** pour recevoir les VLANs propagés par le serveur :

```plaintext
Switch> enable
Switch# configure terminal
Switch(config)# vtp mode client
Switch(config)# vtp domain EntrepriseVLAN
Switch(config)# vtp password MonMotDePasse
```

---

#### **5. Configuration des ports en mode access**

##### **Sur Switch 1**

Attribuez les ports à leurs VLANs respectifs :

```plaintext
! Port pour les PC ADMIN (VLAN 10)
Switch(config)# interface fa0/1 - 18
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

```

##### **Sur Switch 2**

Attribuez les ports aux VLANs :

```plaintext
! Ports pour VLAN 20 (Commercial)
Switch(config)# interface range fa0/1 - 18
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

Switch(config)# interface fa0/19 - 24
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 40
Switch(config-if)# exit
```

##### **Sur Switch 3**

Même logique pour le VLAN Technique :

```plaintext
! Ports pour VLAN 30 (Technique)
Switch(config)# interface range fa0/1 - 18
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
Switch(config-if)# exit

OU Pour une seule machine


Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
Switch(config-if)# exit
```

---

#### **6. Configuration du routeur (Routage inter-VLANs)**

Ne pas oublier de not shut le port car il est désactivé par défaut

```plaintext
Router(config)# int g0/0/0
Router(config)# no shut

```




Créez des sous-interfaces sur le routeur pour permettre la communication entre les VLANs :

```plaintext
Router> enable
Router# configure terminal

! Configurer gig0/0 port du routeur
Router (config)#interface gi0/0/0
Router (config)#no ip address


! Sous-interface pour VLAN 10
Router(config)# interface gi0/0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.254 255.255.255.0
Router(config-subif)# exit

! Répétez pour les autres VLANs
Router(config)# interface gi0/0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.254 255.255.255.0
Router(config-subif)# exit

Router(config)# interface gi0/0/0.30
Router(config-subif)# encapsulation dot1Q 30
Router(config-subif)# ip address 192.168.30.254 255.255.255.0
Router(config-subif)# exit

Router(config)# interface gi0/0/0.40
Router(config-subif)# encapsulation dot1Q 40
Router(config-subif)# ip address 192.168.40.254 255.255.255.0
Router(config-subif)# exit
```

---
#### DHCP

Créer un dhcp sur le routeur pour chaque vlan

```plaintext
Router(config)# ip dhcp pool VLAN10
Router(config-dhcp)# network 192.168.10.0 255.255.255.0
Router(config-dhcp)# default-router 192.168.10.254
Router(config-dhcp)# exit

Router(config)# ip dhcp pool VLAN20
Router(config-dhcp)# network 192.168.20.0 255.255.255.0
Router(config-dhcp)# default-router 192.168.20.254
Router(config-dhcp)# exit

Router(config)# ip dhcp pool VLAN30
Router(config-dhcp)# network 192.168.30.0 255.255.255.0
Router(config-dhcp)# default-router 192.168.30.254
Router(config-dhcp)# exit

Router(config)# ip dhcp pool VLAN40
Router(config-dhcp)# network 192.168.40.0 255.255.255.0
Router(config-dhcp)# default-router 192.168.40.254
Router(config-dhcp)# exit
```


-----

#### **8. Vérifications finales**

- Testez la propagation des VLANs sur les clients VTP avec :
    
    ```plaintext
    Switch# show vlan brief
    ```
    
- Testez la connectivité entre les VLANs avec des commandes **ping** entre PC.

---

Avec cette méthode, vous avez une configuration fonctionnelle et centralisée grâce au VTP. Si besoin, je peux vous aider à automatiser certaines parties ! 😊