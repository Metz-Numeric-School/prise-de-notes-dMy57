
# Configuration Switch Huawei SW_DIDIER
**Modèle :** Huawei CloudEngine S5735-S24S4TXE-V2  
**Adresse IP de management :** 192.168.0.1  
**Auteur :** Quentin W.  
**Date :** _(à compléter)_


---

## 🔧 Informations Générales

| Élément | Valeur |
|----------|--------|
| Nom du switch | `SW_DIDIER` |
| Adresse IP | `192.168.0.1/24` |
| VLAN Management | `Vlanif1` |
| Uplink principal | `10G1/0/1` |
| Interconnexion | Vers CDR |
| Firmware | VRP (Version selon modèle) |

---

## 🧱 VLANs configurés

| VLAN ID | Nom / Usage | Ports associés |
|----------|--------------|----------------|
| 1010 | TFT | G1/0/1 → G1/0/16 |
| 107 | Utilisateurs (partagé) | G1/0/17 → G1/0/22 |
| 402 | Utilisateurs (partagé) | G1/0/17 → G1/0/22 |
| 440 | CASTEL | G1/0/23 → G1/0/24 |

---

## ⚙️ Configuration VRP (Huawei CLI)

```bash
system-view
sysname SW_DIDIER

# VLANs
vlan batch 107 402 440 1010

# Interface de management
interface Vlanif 1
ip address 192.168.0.1 255.255.255.0
quit

# Ports 1 à 16 : TFT (VLAN 1010)
interface range gigabitethernet 1/0/1 to 1/0/16
port link-type access
port default vlan 1010
description TFT_(1010)
undo shutdown
quit

# Ports 17 à 22 : Combo ports (Utilisateurs VLAN 107 / 402)
interface range gigabitethernet 1/0/17 to 1/0/22
combo-port auto
port link-type trunk
port trunk allow-pass vlan 107 402
description USERS_(107_402)
undo shutdown
quit

# Ports 23 à 24 : Combo ports (CASTEL VLAN 440)
interface range gigabitethernet 1/0/23 to 1/0/24
combo-port auto
port link-type access
port default vlan 440
description CASTEL_(440)
undo shutdown
quit

# Port 10G1/0/1 : Uplink Interco vers CDR
interface 10gigabitethernet 1/0/1
port link-type trunk
port trunk allow-pass vlan all
description Uplink_CDR
undo shutdown
quit

# Sauvegarde
save
```


## 🔍 Commandes de vérification

```
display vlan
display interface brief
display combo-port
display port vlan
```

## 🧠 Notes techniques

- Les ports **17 à 24** sont **combo** : ils peuvent fonctionner en **cuivre (RJ45)** ou en **fibre (SFP)**, mais **jamais les deux à la fois**.
    
- Le mode `combo-port auto` détecte automatiquement le support connecté.
    
- Le port **10G1/0/1** sert d’interconnexion principale vers le **CDR** (cœur de réseau).
    
- Les VLAN 107 et 402 passent en **trunk** sur les ports utilisateurs.
    
- Les VLANs TFT et CASTEL sont en **access**.

