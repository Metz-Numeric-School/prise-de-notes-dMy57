
	# C:\Users\Quent\OneDrive\Bureau\MNS\Mr_GAMORY

Git clone “URL”  = “prise de note dmy” 

# # (1a 6) “titre” 

**git add .** = ajoute tts les modifs / création de fichier préparer pour le prochain commit

**git status**  = voir si il y a eu des changement entre origin/master
master = branche local | origin/master = branche du dépot github

**git commit -a -m** "J'ai modifié ceci, etc [...]"
-a = valide tt les changement 
-m = permet de laisser un msg 

**git push** = envoie les notes de la branche local sur la branche origin/master

**git cd + nom du dossier**  = change directory (changement de dossier)

si plusieurs personnes sur le même projet et qu'on "push" ca va delete tout sans prendre en conte les dernières modifs de l'autre et ainsi de suite.

**git pull** = recup les données


# LES VARIABLES
 #variables

un nom et une valeur 

#valeur = différents types de valeurs

#nom = pas de caractères spéciaux / pas d'espace / ne pas commencer par un chiffre

Prenom = John 

#prenom = nom variable
#john = valeur
 #symbole-egale = déclaration  - affectation - initialisation 


prenom = john = INTERDIT ; mettre les guillemets pour les variables


Exemple variable valide : (création variable date du jour)

dateDuJour = "23-09-2024"
anneeDeNaissance = 1999  = pas de guillemet si pas d'espace car c'est un ENTIER

# CONVENTIONS DE NOMMAGES

camelCase =  mettre 1ere lettre de chaque mot en MAJ sauf le premier mot (ex : dateNaissance)

PascalCase = 1er lettre du mot en MAJ + chaque 1ere lettre de chaque mot suite. (ex : DateNaissance)

camelCase = lowerCamelCase
CamelCase = UpperCamelCase 

snake_case (mot séparé par le underscore _ )
kebab-case = - soustraction donc utilisé pour des URL ou noms de fichiers.

pas d'utilisation d'accent (ex : année_naissance = birth_year)

# TYPES DE DONNEES

Les #entiers (integer / int) = nbr de - infini à + infini chiffre rond sans virgule (chiffre entier)

Les #décimaux (float) = nbr de - infini à + infini chiffre à virgule (3.14) 

Les #chaines_de_caractères (string / str) = toujours "entre guillemet"

Table de caractères ASCII 
Booléen (boolean / bool) = true = 1 / false = 0 

# LES OPERATIONS

Entiers = + / - / x / : (division entière)  aucun résultat ne doit avoir de virgule (ex : 5/2 = 2)
Division = résultat décimal (8/2 = 4.0)
** = puissance 

division / multiplication = prioritaire / ** = prioritaire sur la division / multiplication 

#string = une seule opération possible = addition = CONCATENATION 

"Salut" + "ça_va" = "Salut ça_va"

x multiplication sur Python uniquement "A" x 4 = "AAAA"

Bool = opérateur logique :  and = et  / or = ou  / not = non 

# ALGEBRE DE BOOLE

ET

| A   | B   | A et B |
| --- | --- | ------ |
| F   | F   | F      |
| F   | V   | F      |
| V   | F   | F      |
| V   | V   | V      |

OU

| A   | B   | A ou B |
| --- | --- | ------ |
| F   | F   | F      |
| F   | V   | V      |
| V   | F   | V      |
| V   | V   | V      |


NOT

| A   | NON A |
| --- | ----- |
| F   | V     |
| V   | F     |

On peut également utiliser les valeurs numériques : 

| a   | b   | a ET b |
| --- | --- | ------ |
| 0   | 0   | 0 F    |
| 0   | 1   | 0 F    |
| 1   | 0   | 0 F    |
| 1   | 1   | 1 V    |

| A   | B   | A ou B |
| --- | --- | ------ |
| 0   | 0   | 0 F    |
| 0   | 1   | 1 V    |
| 1   | 0   | 1 V    |
| 1   | 1   | 1 V    |

---


|               | A   | B   | C   |
| ------------- | --- | --- | --- |
| a = 2         | 2   | x   | x   |
| b = 3         | 2   | 3   | x   |
| c = 6         | 2   | 3   | 6   |
| a = c + 1     | 7   | 3   | 6   |
| b = a + b     | 7   | 10  | 6   |
| c = a - b + 1 | 7   | 10  | -2  |
| a = b         | 10  | 10  | -2  |
| c = b * 2     | 10  | 10  | 20  |

A  = 10 
B = 10
C = 20

|                | A   | B   | C   |
| -------------- | --- | --- | --- |
| a = 7          | 7   | x   | x   |
| b = 5          | 7   | 5   | x   |
| c = 2          | 7   | 5   | 2   |
| a = B * C      | 10  | 5   | 2   |
| c = A + A      | 10  | 5   | 20  |
| b = c * 3 - c  | 10  | 40  | 20  |
| a = a + b + c  | 70  | 40  | 20  |
| c = a  - b + c | 70  | 40  | 50  |
A = 70
B = 40
C = 50


# OPERATEURS DE COMPARAISON
(utiliser sous certaines conditions)


a = = b - si A est STRICTEMENT égal à B
a ! = b  - si A est DIFFERENT de B
a > b - si A STRICTEMENT supérieur à B
a < b - si A est STRICTEMENT inférieur à B


A < = B inférieur OU égal
(a < b or a = = b) 

if condition -> instruction (indentation) décalage sur la droite 

---

Light = 0 ou 1 #python

``` pyhton
if light == 1 : 

print ("J'ouvre les volets)

else : print("Je ferme les volets")
```

firstname = input ("Votre nom")

Firstname = = "John""

print("Bonjour")

***else : (sinon)*** print ("Aurevoir")

	# C:\Users\Quent\OneDrive\Bureau\MNS\Mr_GAMORY