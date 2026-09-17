# Enums

Un `enum` représente une valeur qui peut prendre plusieurs formes appelées **variantes**.

```rust
enum Direction {
    Up,
    Down,
    Left,
    Right,
}

let direction = Direction::Right;
```

`Direction::Right` utilise `::` pour choisir la variante `Right` du type `Direction`.

## Associer des données à une variante

Chaque variante peut contenir des données différentes :

```rust
enum Action {
    Move(i32, i32),
    Say(String),
    Wait,
}

let mouvement = Action::Move(3, -1);
let message = Action::Say(String::from("Bonjour"));
let attente = Action::Wait;
```

## Traiter les variantes avec `match`

```rust
enum Action {
    Move(i32, i32),
    Say(String),
    Wait,
}

fn execute(action: Action) {
    match action {
        Action::Move(x, y) => println!("Déplacement : {x}, {y}"),
        Action::Say(message) => println!("{message}"),
        Action::Wait => println!("Attente"),
    }
}

fn main() {
    execute(Action::Move(3, -1));
}
```

Les noms `x`, `y` et `message` récupèrent les données contenues dans la variante correspondante.

## À retenir

- Un `enum` définit plusieurs variantes possibles d'un même type.
- Une variante se choisit avec `Type::Variante`.
- Une variante peut contenir des données.
- `match` permet de traiter chaque variante et de récupérer ses données.

Pour pratiquer cette notion, réalise [l'exercice 03 — Traiter une suite d'événements](../Exercises/Structured-Types.md#structured-enums). La correction se trouve avec l'énoncé.
