

Ce notebook présente les **variables**, **constantes** et **types de données** fondamentaux en Python : chaînes, entiers, flottants, booléens, tuples, dictionnaires, ensembles et listes. Chaque type est accompagné d'exemples pratiques et de démonstrations exécutables.

## Variables et constantes

Une **variable** est un espace mémoire qui stocke une valeur. Elle peut changer au cours du programme.

Une **constante** est une variable que l'on décide de **ne pas modifier** après son initialisation (même si Python ne l'interdit pas techniquement). Par convention, les constantes sont écrites **en majuscules**.

```python
# Exemple de variable
nom = "Alice"
age = 25
print(nom, age)

# Exemple de constante (par convention)
PI = 3.14159
print('La valeur de PI est', PI)
```

## Les types de données de base

Python gère automatiquement le type des variables (typage dynamique). On peut utiliser la fonction `type()` pour connaître le type d'une variable.

```python
x = 10
y = 3.14
z = "Bonjour"
b = True

print(type(x))  # int
print(type(y))  # float
print(type(z))  # str
print(type(b))  # bool
```

## Les chaînes de caractères (`str`)

Les chaînes permettent de manipuler du texte. On peut les délimiter par des guillemets simples ' ou doubles ". Elles supportent la concaténation, le slicing et diverses méthodes utiles.

(Référence sur la [doc Python](https://docs.python.org/3/library/stdtypes.html#text-and-binary-sequence-type-methods-summary))

```python
a = 'Bonjour'
b = "le monde"
message = a + ' ' + b
print(message)

print(a[0])      # B
print(a[:3])     # Bon
print(len(a))    # longueur

print(a.upper())  # BONJOUR
print(a.capitalize())  # Le monde
```

## Les nombres entiers (`int`) et réels (`float`)

Les entiers (`int`) représentent des nombres sans décimales, tandis que les flottants (`float`) représentent des nombres à virgule.

```python
a = 10       # int
b = 3.5      # float
c = a + b

print(a + b - c )
print(a - b)
print(a * b)
print(a / b)
print(a // b)  # division entière
print(a % 3)   # modulo
print(a ** 2)  # puissance
```

## Les booléens (`bool`)

Les valeurs booléennes ne peuvent être que `True` ou `False`. Elles sont souvent le résultat d'une comparaison logique.

```python
x = 5
y = 10
a = False
b = True

print(x < y)   # True
print(x == y)  # False
print(not(x > y))  # True
print(a and b) # False
```

## Les tuples (`tuple`)

Un **tuple** est une **collection ordonnée et immuable**.
Cela signifie que **l’ordre des éléments est conservé**, mais qu’**on ne peut pas modifier son contenu après sa création** (pas d’ajout, de suppression ou de remplacement d’élément).

Un tuple s’écrit entre **parenthèses `()`**, et ses éléments peuvent être de **types variés** : entiers, chaînes, listes, dictionnaires, etc.

**Caractéristiques principales :**

* Ordonné → on peut accéder aux éléments par leur **index** (`tuple[0]`, `tuple[1]`, …)
* Immuable → on **ne peut pas** changer les éléments une fois le tuple créé
* Peut contenir **des doublons** (contrairement aux `set`)

**Utilité des tuples :**

* Stocker des **valeurs fixes** qui ne doivent pas changer (ex. coordonnées GPS, dimensions, constantes).
* Utiliser comme **clé de dictionnaire** (car immuables).
* Retourner **plusieurs valeurs** depuis une fonction (Python renvoie naturellement un tuple).

```python
# Exemple simple
coord = (10, 20)
print(coord[0])  # accès à un élément

x, y = coord  # déballage du tuple
print('x =', x, ', y =', y)

t = (42,)
print(type(t))  # tuple à un seul élément

# Exemple d'un tuple avec plusieurs types

info = ('Alice', 30, True, ['pomme', 'banane'])
print(info)
```

## Les listes (`list`)

Une liste est une **collection ordonnée et modifiable**. Elle est très utilisée pour stocker plusieurs valeurs dans un seul objet. Les éléments sont placés entre crochets [].

(Référence sur la [doc Python](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists))

```python
fruits = ['pomme', 'banane', 'cerise', 'banane']

print(fruits[0])
fruits.append("orange")
print(fruits)

fruits.insert(1, 'kiwi')
print(fruits)

fruits.remove('banane')
print(fruits)

print(len(fruits))
```

## Les ensembles (`set`)

Un ensemble est une **collection non ordonnée et sans doublons**. Il est pratique pour les opérations d'ensemble : union, intersection, différence.

```python
animaux = {'chat', 'chien', 'oiseau', 'chat'}
print("Affichage brut d'un set :")
print(animaux) # "chat" ne sera affiche qu'une fois
print(animaux)

animaux.add('poisson')
animaux.remove('chien')
print("Après add/remove :")
print(animaux)

autres = {'poisson', 'lapin'}
print("Union / Intersection :")
print(animaux.union(autres)) # Fusionne les deux sets
print(animaux.intersection(autres)) # Affiche les valeurs communes aux deux sets
```

## Les dictionnaires (`dict`)

Un dictionnaire stocke des **paires clé-valeur**. Les clés doivent être uniques et servent à accéder rapidement aux valeurs associées.

```python
personne = {
    'nom': 'Dupont',
    'age': 30,
    'ville': 'Paris'
}

# Affichage en ligne possible : personne = {'nom': 'Dupont', 'age': 30, 'ville': 'Paris'}

print(personne['nom'])

# Ajouter ou modifier des clés
personne['age'] = 31
personne['metier'] = 'Développeur'

print(personne)

for cle in personne.keys():          # uniquement les clés
    print('Clé :', cle)

for valeur in personne.values():     # uniquement les valeurs
    print('Valeur :', valeur)

for cle, valeur in personne.items(): # les deux à la fois
    print(cle, '→', valeur)

# Supprimer une clé
del personne['metier']

# Vérifier si une clé existe
if 'nom' in personne:
    print('La clé "nom" existe bien !')

print(personne)
```

Un dictionnaire peut contenir **d'autres dictionnaires**.
C’est très utile pour représenter des structures de données complexes (par exemple : plusieurs personnes, produits, élèves…).

```python
# Dictionnaire imbriqué : une personne contient un sous-dictionnaire 'adresse'
personne = {
    'nom': 'Durand',
    'prenom': 'Sophie',
    'age': 29,
    'profession': 'Architecte',
    'adresse': {
        'rue': '15 rue des Lilas',
        'ville': 'Lyon',
        'code_postal': 69003,
        'pays': 'France'
    }
}

# Accès direct aux clés du dictionnaire principal
print(personne['prenom'], personne['nom'])  # Sophie Durand

# Accès au sous-dictionnaire 'adresse'
print(personne['adresse'])

# Accès à un champ spécifique de l'adresse
print(personne['adresse']['ville'])  # Lyon

# Modification du code postal
personne['adresse']['code_postal'] = 69007

# Affichage complet formaté
print(f"{personne['prenom']} habite au {personne['adresse']['rue']}, "
      f"{personne['adresse']['code_postal']} {personne['adresse']['ville']} ({personne['adresse']['pays']})")
```

## Conversion entre types

Python permet de convertir les types avec les fonctions :
* `int()` : pour convertir une donnée en nombre entier
* `float()` : pour convertir une donnée en nombre à virgule flottante
* `str()` : pour convertir une donnée en chaîne de caractères
* `list()` : pour convertir une donnée en une liste
* `tuple()` : pour convertir une donnée (comme une liste par exemple), en tuple
* `set()` : pour convertir une donnée (comme une liste par exemple) en set

```python
a = '123'
b = int(a)
c = float(a)

print(a, type(a))
print(b, type(b))
print(c, type(c))

liste = [1, 2, 3]
tup = tuple(liste)
print(tup)

ens = {'a', 'b', 'c'}
liste2 = list(ens)
print(liste2)
```

