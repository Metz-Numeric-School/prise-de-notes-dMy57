
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

