# Types

Un type indique la forme d'une valeur. Rust peut souvent le trouver automatiquement.

```rust
let age = 20;         // Entier
let taille = 1.75;    // Nombre décimal
let actif = true;     // Booléen
let lettre = 'R';     // Caractère
let nom = "Ferris";   // Texte
```

## Types courants

| Type | Contenu | Exemple |
|---|---|---|
| `i32` | entier positif ou négatif | `-12` |
| `u32` | entier positif ou nul | `12` |
| `f64` | nombre décimal | `3.14` |
| `bool` | vrai ou faux | `true` |
| `char` | un caractère | `'R'` |
| `&str` | du texte | `"Rust"` |

Le type peut être indiqué après le nom de la variable :

```rust
let temperature: i32 = -5;
let score: u32 = 100;
```

## À retenir

- Chaque valeur possède un type.
- `i32` accepte les nombres négatifs, contrairement à `u32`.
- Rust trouve souvent le type automatiquement.
- Une annotation comme `: u32` permet de choisir le type explicitement.

Pour pratiquer cette notion, réalise [l'exercice 07 — Choisir les types d'un état de partie](../Exercises/Bases.md#bases-types). La correction se trouve avec l'énoncé.
