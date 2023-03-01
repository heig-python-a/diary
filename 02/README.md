# Semaine 02/16

## Structure de données

- Scalaires
  - Integers 
  - Float
  - Complex
  - String
  - Boolean
  - None
- Conteneurs 
  - Listes []
    - `-1` Dernière valeur
    - `:-1` Tout jusqu'à la dernière
    - `2:-2` de la troisième à l'avant dernière
    - `::2` Le tableau par pas de deux
    - N'est pas hashable
    - Possède un itérateur
  - Tuple ()
    - Hashable (hash)
    - Possède un itérateur
    - Non modifiable
  - Dictionnaires {}
    - {23: 'deux-trois'}
    - .items() 
    - .value()
    - .keys()
    - Les clés doivent être hashable
    - Hash Table
  - Set {}
    - Un dictionnaire avec que des clés.

## Classes

### Méthodes "magiques"

- `__init__` Initialisateur de classe qui peut prendre des paramètres
- `__next__` Qui retourne l'élément suivant d'une séquence
- `__iter__` Qui retourne un itérateur sur une séquence

### Ouvrir des fichiers 

```python 
fp = open(filename, 'r') # 'w', 'a'
fp.read() # Lis tout le fichier
fp.readline() # Lis la prochaine ligne
fp.readlines() # Lis toutes les lignes 
fp.close()
```


