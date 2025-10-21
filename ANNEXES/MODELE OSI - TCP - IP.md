
# 📚 Cours sur les modèles OSI et TCP/IP

## 🔸 Introduction

Les modèles **OSI** (Open Systems Interconnection) et **TCP/IP** sont des **modèles de référence** permettant de **comprendre et standardiser** les communications réseau entre équipements informatiques.

---

## 🧱 Le modèle OSI (Open Systems Interconnection)

Le modèle **OSI** est composé de **7 couches**. Chacune a un rôle précis et interagit avec les couches adjacentes.

|Couche|Nom|Rôle principal|
|---|---|---|
|7|**Application**|Interface utilisateur, logiciels (ex: navigateur web)|
|6|**Présentation**|Encodage, chiffrement, compression|
|5|**Session**|Gestion des connexions, synchronisation|
|4|**Transport**|Transmission fiable, contrôle d'erreurs (ex: TCP/UDP)|
|3|**Réseau**|Routage des paquets, adressage IP|
|2|**Liaison de données**|Encapsulation en trames, détection d'erreurs, MAC|
|1|**Physique**|Transmission des bits (câbles, signaux, fibre, etc.)|

---

## 🌐 Le modèle TCP/IP

Le modèle TCP/IP est plus **réaliste** et **utilisé en pratique**. Il comporte **4 couches** principales.

|Couche TCP/IP|Équivalent OSI|Rôle principal|
|---|---|---|
|**Application**|Couches 5, 6, 7|Services applicatifs (HTTP, FTP, SMTP, DNS...)|
|**Transport**|Couche 4|Transmission des données (TCP ou UDP)|
|**Internet**|Couche 3|Adressage IP, routage (IP, ICMP)|
|**Accès réseau**|Couches 1 et 2|Transmission physique + liaison (Ethernet, WiFi, etc.)|

---

## 🔄 Comparatif OSI vs TCP/IP

|Aspect|Modèle OSI|Modèle TCP/IP|
|---|---|---|
|Nombre de couches|7|4|
|Créé par|ISO|DARPA / DoD|
|Utilisation|Théorique|Pratique|
|Développement|Plus structuré|Basé sur Internet|

---

## 💬 Exemple concret (HTTP)

1. **Application** : Un utilisateur tape une URL dans un navigateur (HTTP).
    
2. **Transport** : Les données sont découpées en segments (TCP).
    
3. **Internet** : Les segments sont encapsulés dans des paquets IP.
    
4. **Accès réseau** : Les paquets sont transmis sur le réseau via Ethernet ou Wi-Fi.
    

---

## 📌 À retenir

- Le modèle **OSI** est **théorique**, **TCP/IP** est **pratique**.
    
- Les **couches hautes** gèrent les **données utilisateur**, les **basses** gèrent la **transmission physique**.
    
- Bien connaître ces couches aide à **diagnostiquer** et **concevoir** des réseaux.