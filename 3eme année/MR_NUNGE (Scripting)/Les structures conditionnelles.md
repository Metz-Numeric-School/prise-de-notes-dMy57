

Ce notebook couvre en profondeur les **conditions** en Python : opérateurs de comparaison, booléens, `if / elif / else`, opérateurs logiques, _truthiness_, expressions conditionnelles (ternaires), imbrication, et les pièges fréquents.

Vous trouverez des **exemples exécutables** ainsi que des **exercices** avec corrigés.

## 1. Booléens et opérateurs de comparaison

### Définition

Un booléen (ou valeur booléenne) est un type de donnée logique qui ne peut prendre que deux valeurs possibles :

* 👉 `True` (vrai)
* 👉 `False` (faux)

Ce type sert à exprimer une condition logique, un état ou le résultat d’une comparaison.

**Opérateurs de comparaison courants :**

- `==` égalité
- `!=` différence
- `<`, `<=`, `>`, `>=`
- `in` (appartenance), `not in`

Les comparaisons **retournent un booléen**.

```python
# Exemples
a = 5
b = 7
d = "Alice"
e = "Bob"

print("Résultat de a == b", a == b)   # False
print("Résultat de d == e", d == e)   # False
print("Résultat de a != b", a != b)   # True
print("Résultat de a < b ", a < b)    # True
print("Résultat de a <= 5", a <= 5)   # True

# Appartenance
lettres = ['a', 'b', 'c']
print('a' in lettres)    # True
print("z" in lettres)    # False
```

## 2. La structure `if / elif / else`

Syntaxe :

```python
if condition_1:
    bloc_1
elif condition_2:
    bloc_2
else:
    bloc_sinons
```

Notez bien l'utilisation des ":" à la fin des lignes précédent les blocs.

Les blocs, eux, sont déterminés par **l'indentation**. Dès qu'une condition est vraie, son bloc s'exécute et **les autres ne sont pas évaluées**.

Les conditions `elif` et `else` sont optionnelles. Vous pouvez avoir uniquement un `if`.

⚠️ **Attention** : un `elif` ou un `else` ne peuvent pas être utilisés sans `if` !

```python
# Exemple : catégoriser un âge
age = 17

if age < 12:
    categorie = "enfant"
elif age < 18:
    categorie = "adolescent"
elif age < 65:
    categorie = "adulte"
else:
    categorie = "senior"

print(categorie)
```

## 3. Opérateurs logiques : `and`, `or`, `not`

- `A and B` est vrai si **A ET B** sont vrais.
- `A or B` est vrai si **au moins l'un** des deux est vrai.
- `not A` inverse la vérité de `A`.

Ces opérateurs **sont à court-circuit** :
- Avec `and`, si `A` est faux, Python **n'évalue pas** `B`.
- Avec `or`, si `A` est vrai, Python **n'évalue pas** `B`.

```python
# Exemples d'usage
revenu = 32000
annees_anciennete = 4

# éligible si revenu >= 30000 ET ancienneté >= 3 ans
if revenu >= 30000 and annees_anciennete >= 3:
    print("Éligible")
else:
    print("Non éligible")

# Exemple 'or' : accès gratuit si -12 ans ou +65 ans
age = 70
if age < 12 or age >= 65:
    print("Accès gratuit")
else:
    print("Tarif normal")

# 'not'
inscrit_newsletter = False
if not inscrit_newsletter:
    print("Proposer l'inscription")

# Combinaison des opérateurs logiques
userExists = True
isAdmin = False
isPublic = True
print(userExists and isAdmin or isPublic)
```

## 4. Truthiness (valeurs évaluées comme vrai/faux)

La **truthiness** (ou *valeur de vérité implicite*) désigne la **façon dont Python évalue une valeur comme "vraie" ou "fausse"**, même si ce n'est **pas un booléen explicite** (`True` ou `False`).

Autrement dit, **toute valeur en Python peut être interprétée comme vraie ou fausse** lorsqu'elle est utilisée dans un contexte logique (par exemple dans un `if`).

**Règle générale :**

* ✅ **Valeurs considérées comme vraies ("truthy")**
  → Presque tout ce qui **n'est pas vide ou nul** :
  `1`, `"bonjour"`, `[1, 2]`, `{ 'clé': 'valeur' }`, etc.

* ❌ **Valeurs considérées comme fausses ("falsy")**
  → Les valeurs **vides ou nulles** :
  `0`, `0.0`, `''`, `[]`, `{}`, `set()`, `None`, `False`

**🧠 À retenir :**

> La **truthiness** est la capacité de Python à **interpréter automatiquement une valeur comme vraie ou fausse** dans un test logique, sans exiger qu'elle soit explicitement `True` ou `False`.

```python
# Exemples
texte = ""
liste = [1, 2, 3]
dictionnaire = {}

if not texte:
    print("Le texte est vide")

if liste:  # True si la liste n'est pas vide
    print("La liste contient des éléments")

if not dictionnaire:
    print("Le dictionnaire est vide")
```

## 5. Expression conditionnelle (ternaire)

Forme compacte pour affecter une valeur selon une condition :

```python
valeur = expression_si_vrai if condition else expression_si_faux
```
À utiliser pour des cas simples (lisibilité avant tout).

```python
# Exemple
note = 14
mention = "Admis" if note >= 10 else "Ajourné"
print(mention)

# Exemple légèrement plus complexe (éviter d'en faire trop)
# A n'utiliser que dans des cas où la lisibilité reste simple. Sinon, préferer une structure en if/elif/else classique.
age = 20
tarif = 0 if age < 12 else (8 if age < 26 else 12)
print(tarif)
```

## 6. Imbrication vs. chaîne de `elif`


Évitez les imbrications trop profondes. Préférez une **chaîne de `elif`** claire.

```python
# Mauvais style (imbrication inutile)
x = 5
if x > 0:
    if x < 10:
        print("Entre 1 et 9")
    else:
        print("10 ou plus")
else:
    print("Négatif ou nul")

# Meilleur style
x = 5
if x <= 0:
    print("Négatif ou nul")
elif x < 10:
    print("Entre 1 et 9")
else:
    print("10 ou plus")
```

## 7. Bonnes pratiques et pièges fréquents

1. **Utiliser == pour comparer des valeurs**.
2. **Attention à l'assignation vs. comparaison** : = assigne, == compare.
3. **Comparer des types compatibles** (éviter 3 < '3').
4. **Lisibilité** : préférez des conditions nommées (variables intermédiaires) si l'expression devient longue.
5. **Chaînage de comparaisons** : Python permet 18 <= age < 65.
6. **Court-circuit** : utile pour éviter des erreurs (ex. vérifier obj non nul avant obj.attr).
7. **Ne pas abuser des ternaires** : au-delà d'un cas simple, préférez if.

```python
## 2. Assignation vs. comparaison
x = 10  # ✅ assignation

# Mauvais : confondre '=' et '=='
if x == 10:   # ✅ comparaison correcte
    print("x vaut bien 10")

# if x = 10:  ❌ SyntaxError : on ne peut pas assigner dans une condition
```

```python
## 4. Lisibilité : conditions nommées
revenu = 28000
depenses = 12000
annee_experience = 4

# Trop complexe et illisible :
if (revenu > 25000 and depenses < 15000 and annee_experience >= 3) or (revenu > 40000 and annee_experience >= 2):
    print("Éligible")

# ✅ Mieux : variables intermédiaires
conditions_base = revenu > 25000 and depenses < 15000 and annee_experience >= 3
conditions_bonus = revenu > 40000 and annee_experience >= 2

if conditions_base or conditions_bonus:
    print("Éligible")
```

```python
## 5. Chaînage de comparaisons
age = 34
if 18 <= age < 65:
    print("Adulte en âge de travailler")
```

```python
## 6. Court-circuit logique

user = None

# ❌ Erreur si on essaye d'accéder à user['nom'] directement
# print(user["nom"])  # provoque TypeError

# ✅ Grâce au court-circuit de 'and', la 2e partie n’est évaluée que si la 1re est vraie
if user and "nom" in user:
    print("Nom :", user["nom"])
else:
    print("Utilisateur non défini ou sans nom")
```

```python
## 7. Ternaires

# ✅ Simple : clair

age = 20
message = "majeur" if age >= 18 else "mineur"

print(message)

# ❌ Complexe : illisible

prix = 10 if age < 12 else 8 if age < 18 else 12 if age < 65 else 6

print(prix)  # difficile à lire !

# ✅ Mieux avec if / elif

if age < 12:
    prix = 10
elif age < 18:
    prix = 8
elif age < 65:
    prix = 12
else:
    prix = 6

print(prix)

```

## 9. Mise en pratique

### Exercice 1 — Pair / impair

Écrire un programme qui lit un entier `n` (déjà fourni) et affiche `pair` si `n` est pair, sinon `impair`.

🧠 **Pour aller plus loin :** vous pouvez aller récupérer le nombre avec une saisie utilisateur (`input()`). N'oubliez pas de vérifier les types.

```python
# TODO: compléter
n = 18  # vous pouvez changer la valeur pour tester

# Votre code ici
# indice: utilisez l'opérateur % (modulo)

```

### Exercice 2 — Tarif réduit

On applique un **tarif réduit** si l'utilisateur a **moins de 26 ans** **ou** est **bénéficiaire du RSA**. Sinon, tarif normal. Afficher `reduit` ou `normal`.

```python
# TODO: compléter
age = 27
beneficiaire_rsa = True

# Votre code ici

```

### Exercice 3 — Catégorisation de notes

À partir d'une `note` sur 20, afficher :
- `<10` : `ajourné`
- `10 à 11.99` : `passable`
- `12 à 13.99` : `assez bien`
- `14 à 15.99` : `bien`
- `>= 16` : `très bien`

```python
# TODO: compléter
note = 0.5

# Votre code ici

```

### Exercice 4 — Login très simplifié

Demandez (via les variables déjà posées) `username` et `password`. Affichez `OK` si les deux correspondent aux références, sinon `KO`.

**Références :** `ref_user = 'admin'`, `ref_pwd = '1234'`

```python
# TODO: compléter
ref_user = 'admin'
ref_pwd = '1234'

username = 'admin'   # simule une saisie
password = '1234'    # simule une saisie

# Votre code ici
```

### Exercice 5 — Sécurité accès mineurs

Affichez `autorisé` si l'utilisateur a 18 ans **ou plus**, sinon `refusé`. Faites-le en utilisant une expression conditionnelle (**ternaire**)

```python
# TODO: compléter
age = 13

# Votre code ici
```

