## Semaine 04/16

- On peut vérifier la présence d'un élément avec `in` comme `4 in [1,2,3,4]`
- `all` qui retourne vrai si tous les éléments sont vrai
- `any` qui retourne vrai si au moins un élément est vrai
- On peut utiliser la destructuration pour échanger deux valeurs, 
- ou pour extraire l'indice d'une valeur dans une boucle 
- La surchage des opérateurs existe aussi avec les container de données
  - `{1,2,3,4} - {1,2}`
  - `{1,2,3,4} ^ {1,2,6}`

```python
a, b = b, a  # J'échange a et b
for i, v in enumerate([1,2,3,4])
```

## Opérateur zip

```python
>>> firstnames = ['John', 'Emmet', 'Luke']
>>> lastnames = ['Doe', 'Brown', 'Skywalker']
>>> list(zip(firstnames, lastnames))
[('John', 'Doe'), ('Emmet', 'Brown'), ('Luke', 'Skywalker')]

>>> [' '.join(x) for x in list(zip(firstnames, lastnames))]
['John Doe', 'Emmet Brown', 'Luke Skywalker']

>>> list(map(lambda x: ' '.join(x), zip(firstnames, lastnames)))
['John Doe', 'Emmet Brown', 'Luke Skywalker']

>>> list(filter(lambda x: x%3, [1,2,3,4,5,6,7]))
[1, 2, 4, 5, 7]
```

## Opérateur de déréférencement * et **

```python
>>> def operate(a, b, **kwargs):
        if 'add' in kwargs:
            print(f"{a}+{b}={a+b}")
        if 'sub' in kwargs:
            print(f"{a}-{b}={a-b}")

>>> operate(23,42)
>>> operate(23,42, add=True)
23+42=65
>>> operate(23,42, add=True, sub=True)
23+42=65
23-42=-19
```

## Exercice

Exercez-vous avec les éléments suivants:

```python
in 
all
any 
map
filter
*
**
```

On a une liste de noms de poissons chaque élément est un tuple avec 

1. Le nom du poisson
2. Son espèce
3. Son sexe
4. Mort ou vivant (bool)

a. Filtrer la liste pour ne récupérer que les poissons mâles
b. Afficher que les noms de poissons
c. Établir une liste (set) de toutes les espèces présentes dans l'aquarium
d. Créer une fonction `fish(name, group, genre, status)` qui affiche :
    `Poisson {name} de l'espèce {group} est {"vivant" if status else "mort"}`
e. Executer la fonction pour chaque élément de la liste (vous utiliserez `*`)
f. Comment savoir en une ligne si il y a des poissons mort dans l'aquarium
g. Est-ce qu'il y a un "Scalaire" (nom de l'espèce) dans votre aquarium ?

```python
import random

fish_names = ["Trout", "Salmon", "Bass", "Catfish", "Tuna", "Mackerel", "Sardine", "Haddock", "Halibut", "Cod"]
fish_species = ["Oncorhynchus mykiss", "Salmo salar", "Micropterus salmoides", "Ictalurus punctatus", "Thunnus albacares", "Scomber scombrus", "Sardina pilchardus", "Melanogrammus aeglefinus", "Hippoglossus hippoglossus", "Gadus morhua"]
fish_gender = ["Male", "Female"]
fish_status = [True, False]

fish_list = []

for i in range(100):
    name = random.choice(fish_names)
    species = random.choice(fish_species)
    gender = random.choice(fish_gender)
    status = random.choice(fish_status)
    fish_list.append((name, species, gender, status))

print(fish_list)
```
