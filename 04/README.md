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

On vous demande: 
1. Filtrer la liste pour ne récupérer que les poissons mâles
2. Afficher que les noms de poissons
3. Établir une liste (set) de toutes les espèces présentes dans l'aquarium
4. Créer une fonction `fish(name, group, genre, status)` qui affiche :
    `Poisson {name} de l'espèce {group} est {"vivant" if status else "mort"}`
5. Executer la fonction pour chaque élément de la liste (vous utiliserez `*`)
6. Comment savoir en une ligne si il y a des poissons mort dans l'aquarium
7. Est-ce qu'il y a un "Scalaire" (nom de l'espèce) dans votre aquarium ?

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

### Solution chat.openai

```python
fish_list = [("Nemo", "Poisson-clown", "mâle", True),
             ("Dory", "Chirurgien bleu", "femelle", True),
             ("Marlin", "Poisson-clown", "mâle", False),
             ("Bruce", "Grand requin blanc", "mâle", True),
             ("Anchor", "Requin-marteau", "mâle", False),
             ("Gill", "Poisson-chirurgien", "mâle", True),
             ("Bloat", "Poisson-globe", "mâle", True),
             ("Peach", "Etoile de mer", "femelle", True)]

# Question 1: Filtrer la liste pour ne récupérer que les poissons mâles
male_fish = filter(lambda fish: fish[2] == "mâle", fish_list)

# Question 2: Afficher que les noms de poissons
fish_names = map(lambda fish: fish[0], male_fish)
print(list(fish_names))  # Output: ['Nemo', 'Marlin', 'Bruce', 'Anchor', 'Gill', 'Bloat']

# Question 3: Établir une liste (set) de toutes les espèces présentes dans l'aquarium
fish_species = set(map(lambda fish: fish[1], fish_list))
print(fish_species)  # Output: {'Poisson-clown', 'Poisson-chirurgien', 'Chirurgien bleu', 'Etoile de mer', 'Requin-marteau', 'Grand requin blanc', 'Poisson-globe'}

# Question 4: Créer une fonction fish(name, group, genre, status) qui affiche : Poisson {name} de l'espèce {group} est {"vivant" if status else "mort"}
def fish(name, group, genre, status):
    print(f"Poisson {name} de l'espèce {group} est {'vivant' if status else 'mort'}")

# Question 5: Executer la fonction pour chaque élément de la liste (vous utiliserez *)
for fish_info in fish_list:
    fish(*fish_info)

# Question 6: Comment savoir en une ligne si il y a des poissons mort dans l'aquarium
any_dead_fish = any(map(lambda fish: not fish[3], fish_list))
print(any_dead_fish)  # Output: True

# Question 7: Est-ce qu'il y a un "Scalaire" (nom de l'espèce) dans votre aquarium ?
is_scalaire_present = any(map(lambda fish: fish[1] == "Scalaire", fish_list))
print(is_scalaire_present)  # Output: False
```
