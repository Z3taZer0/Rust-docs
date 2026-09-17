# Variables

Une variable permet de donner un nom à une valeur. Elle se déclare avec `let`.

```rust
let nombre = 5;
let nom = "Alice";
```

Rust peut souvent trouver le type tout seul. Ici, `nombre` est un entier et `nom` est une chaîne de caractères de type `&str`.

Le type peut aussi être écrit explicitement après le nom :

```rust
let nombre: i32 = 5;
```

## Variables immuables

Par défaut, la valeur d'une variable ne peut pas être modifiée :

```compile_fail
let nombre = 5;
nombre = 6; // Erreur : nombre est immuable.
```

## Variables mutables

Le mot-clé `mut` permet de modifier la valeur :

```rust
let mut nombre: i32 = 5;
nombre = 6;
```

## Chaînes de caractères modifiables

Une valeur de type `String` peut contenir du texte que l'on souhaite modifier :

```rust
let mut message = String::from("Bonjour");
message.push_str(", monde !");
```

Après `push_str`, `message` contient `"Bonjour, monde !"`.

## La syntaxe `::`

Le double deux-points `::` permet de suivre un **chemin** jusqu'à un élément. Dans `String::from`, il signifie : utiliser l'élément `from` associé au type `String`.

```rust
let message = String::from("Bonjour");
```

`from` est appelée une **fonction associée** : elle appartient au type `String`, mais elle n'est pas appelée sur une valeur qui existe déjà.

Un chemin peut contenir plusieurs parties :

```rust
let maximum = std::cmp::max(4, 9);
println!("{maximum}");
```

Ce chemin se lit de gauche à droite :

- `std` est la bibliothèque standard de Rust ;
- `cmp` est l'un de ses modules ;
- `max` est la fonction utilisée.

## Différence entre `::` et `.`

```rust
let mut message = String::from("Bonjour");
message.push('!');
```

- `String::from(...)` utilise une fonction associée au type `String` ;
- `message.push(...)` appelle une méthode sur la valeur `message`.

Le point `.` part donc d'une valeur existante, tandis que `::` parcourt un chemin comme `Type::élément` ou `module::élément`.

## À retenir

- `let` déclare une variable.
- Une variable est immuable par défaut.
- `let mut` déclare une variable modifiable.
- `: i32` indique explicitement le type d'une variable.
- `::` sépare les différentes parties d'un chemin.
- `.` appelle une méthode sur une valeur existante.

Pour pratiquer cette notion, réalise [l'exercice 02 — Suivre une session de jeu](../Exercises/Bases.md#bases-variables). La correction se trouve avec l'énoncé.
