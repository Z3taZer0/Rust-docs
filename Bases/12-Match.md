# `match`

`match` compare une valeur à plusieurs possibilités et exécute le bloc correspondant.

```rust
let nombre = 2;

match nombre {
    1 => println!("Un"),
    2 => println!("Deux"),
    3 => println!("Trois"),
    _ => println!("Autre nombre"),
}
```

Chaque possibilité est appelée un bras. La flèche `=>` sépare la valeur recherchée du code à exécuter.

## Le cas `_`

`match` doit prévoir toutes les possibilités. `_` récupère toutes celles qui n'ont pas été écrites avant.

```rust
let note = 15;

match note {
    20 => println!("Parfait"),
    10 => println!("Moyenne"),
    _ => println!("Autre note"),
}
```

## Retourner une valeur

`match` peut produire une valeur :

```rust
let actif = true;

let message = match actif {
    true => "Actif",
    false => "Inactif",
};

println!("{message}");
```

## À retenir

- `match` compare une valeur à plusieurs possibilités.
- `=>` indique le code associé à une possibilité.
- `_` représente tous les autres cas.
- Tous les cas possibles doivent être couverts.
- `match` peut retourner une valeur.

Pour pratiquer cette notion, réalise [l'exercice 12 — Interpréter une commande de jeu](../Exercises/Bases.md#bases-match). La correction se trouve avec l'énoncé.
