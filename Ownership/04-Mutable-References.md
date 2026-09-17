# Références mutables

Une référence mutable permet de modifier une valeur empruntée. La valeur d'origine doit elle-même être déclarée avec `mut`.

```rust
fn ajouter_point(texte: &mut String) {
    texte.push('!');
}

fn main() {
    let mut message = String::from("Bonjour");

    ajouter_point(&mut message);
    println!("{message}");
}
```

- `message` est mutable grâce à `let mut` ;
- `&mut message` crée une référence mutable ;
- `&mut String` indique que la fonction peut modifier le texte emprunté.

## Une référence mutable à la fois

Rust empêche l'utilisation simultanée de plusieurs références mutables vers la même valeur :

```rust
let mut message = String::from("Bonjour");

let premiere = &mut message;
premiere.push('!');

let seconde = &mut message;
seconde.push('?');
```

Le dernier usage de `premiere` a lieu avant la création de `seconde`. Leurs emprunts ne se chevauchent donc pas.

Cette règle évite que deux parties du programme modifient la même valeur au même moment.

## Petit exercice

Écris une fonction `ajouter_salutation` qui reçoit `&mut String` et ajoute `" !"` avec la méthode `push_str()`.

## À retenir

- `&mut` crée une référence mutable.
- La valeur empruntée doit être déclarée avec `mut`.
- Une seule référence mutable vers une valeur peut être active à la fois.
- Les références mutables rendent les modifications explicites.
