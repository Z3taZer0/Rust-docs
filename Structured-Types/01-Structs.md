# Structs

Une `struct` permet de créer un type qui regroupe plusieurs données liées.

```rust
struct Position {
    x: f32,
    y: f32,
}

fn main() {
    let joueur = Position { x: 10.0, y: 5.0 };

    println!("{}, {}", joueur.x, joueur.y);
}
```

`Position` est le nom du nouveau type. `x` et `y` sont ses champs. Le point `.` permet de lire un champ d'une valeur existante.

## Modifier un champ

Toute la valeur doit être déclarée avec `mut` pour modifier l'un de ses champs :

```rust
struct Position {
    x: f32,
    y: f32,
}

let mut joueur = Position { x: 10.0, y: 5.0 };
joueur.x += 2.0;
```

## Utiliser des variables comme champs

Lorsque la variable et le champ portent le même nom, il suffit d'écrire ce nom une seule fois :

```rust
struct Position {
    x: f32,
    y: f32,
}

let x = 10.0;
let y = 5.0;
let joueur = Position { x, y };
```

## Tuple structs et unit structs

Une tuple struct possède des champs numérotés :

```rust
struct Score(u32);

let score = Score(100);
println!("{}", score.0);
```

Une unit struct ne contient aucune donnée. Elle sert souvent de marqueur :

```rust
struct Player;

let joueur = Player;
```

Ces deux formes apparaissent fréquemment dans Bevy pour définir des composants simples.

## À retenir

- Une `struct` crée un type composé de plusieurs champs.
- `valeur.champ` donne accès à un champ.
- La valeur doit être mutable pour modifier ses champs.
- Une tuple struct possède des champs numérotés.
- Une unit struct ne contient aucune donnée.

Pour pratiquer cette notion, réalise [l'exercice 01 — Modéliser les données d'une arène](../Exercises/Structured-Types.md#structured-structs). La correction se trouve avec l'énoncé.
