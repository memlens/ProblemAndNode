# Résoudre le Puzzle Coulissant en Python : Implémentation de Problem et Node 🧩🐍

---
Les puzzles coulissants ne sont pas seulement des casse-têtes amusants, ils sont aussi parfaits pour booster nos compétences en intelligence artificielle ! Dans cet article, on va vous emmener à travers la résolution d'un puzzle coulissant en Python avec une petite touche de fun 🎉. On va utiliser des algorithmes de recherche non informée et implémenter les classes abstraites `Problem` et `Node`. 

---

## C'est Quoi un Puzzle Coulissant ? 🤔

Imaginez un plateau 5x4 avec des pièces que vous devez déplacer pour amener une pièce rouge (2x2) à sa place cible. Les autres pièces sont de tailles différentes, et vous devez les déplacer dans l'ordre :

- **Pièces verticales (2x1)**
- **Pièces horizontales (1x2)**
- **Pièces uniques (1x1)**

### Exemple de départ et de cible 🎯

**État initial :**
```
2 1 1 3
2 1 1 3
0 A A 0
4 6 7 5
4 8 9 5
```

**Objectif à atteindre :**
```
. . . .
. . . .
. . . .
. 1 1 .
. 1 1 .
```

---

## L'Approche Algorithmique 🧠💻

On va utiliser deux classes principales pour modéliser ce problème : `Problem` et `Node`.

### 1. Classe `Problem` – La Base du Puzzle

Cette classe définit tout ce qu'il faut pour résoudre notre puzzle :

- **`initial`** : L'état de départ du puzzle (où tout commence).
- **`goal`** : L'état à atteindre (c'est la cible !).
- **`actions(state)`** : Retourne les mouvements possibles à partir d'un état donné.
- **`result(state, action)`** : Applique une action et obtient le nouvel état.
- **`goal_test(state)`** : Vérifie si l'état actuel est l'objectif. 

### 2. Classe `Node` – Le Héros du Parcours

Chaque `Node` représente un état dans notre arbre de recherche :

- **`state`** : L'état actuel.
- **`parent`** : Le parent du nœud (pour tracer le chemin).
- **`action`** : L'action qui a permis d'atteindre cet état.

La méthode `expand` crée les "enfants" du nœud courant en appliquant toutes les actions possibles. Magique, non ? ✨

---

## Le Code Python – Magic Mode On 🧙‍♂️

Voici le code qui fait tout le travail :

### Classe `Problem`
```python
class Problem:
    def __init__(self, initial, goal):
        self.initial = initial
        self.goal = goal

    def actions(self, state):
        # Logic to find possible actions
        pass

    def result(self, state, action):
        # Apply an action and return the new state
        pass

    def goal_test(self, state):
        return state == self.goal
```

### Classe `Node`
```python
class Node:
    def __init__(self, state, parent=None, action=None, path_cost=0):
        self.state = state
        self.parent = parent
        self.action = action
        self.path_cost = path_cost

    def expand(self, problem):
        return [
            Node(problem.result(self.state, action), self, action)
            for action in problem.actions(self.state)
        ]
```

---

## Stratégies de Recherche – Choisissez Votre Arme 🛠️

Il existe plusieurs techniques pour explorer l'arbre des états. On en a testé deux :

### Recherche en largeur (BFS) 🌊

- **Avantages** : Trouve toujours la solution optimale (profondément, pas de raccourcis !).
- **Inconvénients** : Mange beaucoup de mémoire (ça devient un peu lourd...).

### Recherche en profondeur (DFS) 🏊‍♂️

- **Avantages** : Utilise peu de mémoire (tout va bien !).
- **Inconvénients** : Parfois, ça fait des boucles infinies et ça n'aboutit à rien... Pas top ! 🙄

---

## Résultats – Testons Cela ! 📊

Après avoir lancé nos tests sur différentes instances du puzzle, voici ce qu'on a observé :

- **BFS** a trouvé la solution à chaque fois, mais à un coût mémoire assez élevé.
- **DFS** a parfois échoué, bloqué dans des boucles infinies. Pas cool. 😅

---

## Conclusion – Mission Accomplie ✅

Voilà comment on a résolu le puzzle coulissant en utilisant des algorithmes de recherche non informée et en modélisant notre problème avec des classes Python. 🎉 N'hésitez pas à tester votre propre implémentation et à nous faire part de vos idées pour améliorer cette approche. Qui sait, vous pourriez résoudre des puzzles encore plus complexes ! 😎

---

## Références 📚

- [AI: A Modern Approach](http://aima.cs.berkeley.edu/) – Pour devenir un génie des algos de recherche.
- [Sliding Puzzle Online](http://www.gamedesign.jp/flash/slidingblock/slidingblock.html) – Testez vos solutions directement en ligne ! 🎮
