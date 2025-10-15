
## Introduction

Une adresse IPv4 est une adresse de 32 bits, généralement représentée en **notation décimale** sous la forme de quatre octets séparés par des points. Chaque octet est composé de 8 bits. Nous allons ici apprendre à convertir une adresse IPv4 donnée en **notation binaire** en **notation décimale**.

Prenons l'exemple de l'adresse IPv4 suivante :  
**11001011.00000000.01110001.11010011**

## Étapes de conversion

### 1. Séparer l'adresse en quatre octets :

L'adresse IPv4 en binaire est déjà divisée en quatre parties :

- **11001011** (octet 1)
- **00000000** (octet 2)
- **01110001** (octet 3)
- **11010011** (octet 4)

### 2. Convertir chaque octet binaire en notation décimale :

Pour chaque octet, nous devons convertir le nombre binaire en un nombre décimal. Cela se fait en calculant la valeur de chaque bit selon sa position. L'octet binaire est évalué comme une somme de puissances de 2, de droite à gauche, où chaque bit représente une puissance de 2 (0 ou 1).

#### Octet 1 : **11001011 (binaire)**

Le calcul pour cet octet est le suivant :

| Bit         | 1   | 1   | 0   | 0   | 1   | 0   | 1   | 1   |
| ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
| Poids (2^n) | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
Calcul :  
128 + 64 + 0 + 0 + 8 + 0 + 2 + 1 = 203

---

**Octet 2 : 00000000**

Tous les bits à 0 → 0

---

**Octet 3 : 01110001**

|Bit|0|1|1|1|0|0|0|1|
|---|---|---|---|---|---|---|---|---|
|Poids (2^n)|128|64|32|16|8|4|2|1|

Calcul :  
0 + 64 + 32 + 16 + 0 + 0 + 0 + 1 = 113

---

**Octet 4 : 11010011**

|Bit|1|1|0|1|0|0|1|1|
|---|---|---|---|---|---|---|---|---|
|Poids (2^n)|128|64|32|16|8|4|2|1|

Calcul :  
128 + 64 + 0 + 16 + 0 + 0 + 2 + 1 = 211

---

### Étape 3 : Résultat final en IPv4 décimale pointée

**203.0.113.211**