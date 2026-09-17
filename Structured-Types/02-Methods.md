# Méthodes et `impl`

Un bloc `impl` associe des fonctions à un type.

```rust
struct Rectangle {
    largeur: u32,
    hauteur: u32,
}

impl Rectangle {
    fn aire(&self) -> u32 {
        self.largeur * self.hauteur
    }
}

fn main() {
    let rectangle = Rectangle {
        largeur: 10,
        hauteur: 5,
    };

    println!("{}", rectangle.aire());
}
```

`&self` est une référence vers la valeur sur laquelle la méthode est appelée. `rectangle.aire()` emprunte donc `rectangle` sans en prendre la propriété.

## Modifier avec `&mut self`

```rust
struct Player {
    health: u32,
}

impl Player {
    fn heal(&mut self, amount: u32) {
        self.health += amount;
    }
}

fn main() {
    let mut player = Player { health: 50 };
    player.heal(10);

    println!("{}", player.health);
}
```

Une méthode qui reçoit `&mut self` peut modifier la valeur.

## Fonction associée

Une fonction associée n'utilise pas `self`. Elle est appelée avec `::` et sert souvent à construire une valeur :

```rust
struct Player {
    health: u32,
}

impl Player {
    fn new() -> Self {
        Self { health: 100 }
    }
}

let player = Player::new();
println!("{}", player.health);
```

`Self` désigne ici le type `Player`. `Player::new()` suit un chemin jusqu'à la fonction associée `new`.

## À retenir

- `impl Type` associe des fonctions à un type.
- `&self` permet de lire la valeur.
- `&mut self` permet de la modifier.
- Une méthode est appelée avec `valeur.methode()`.
- Une fonction associée est appelée avec `Type::fonction()`.
- `Self` représente le type du bloc `impl`.

Pour pratiquer cette notion, réalise [l'exercice 02 — Encapsuler les actions d'un personnage](../Exercises/Structured-Types.md#structured-methods). La correction se trouve avec l'énoncé.
