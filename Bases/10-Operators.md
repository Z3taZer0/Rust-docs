# Opérateurs

Les opérateurs permettent de calculer ou de modifier une valeur.

## Calculs

```rust
let addition = 5 + 2;       // 7
let soustraction = 5 - 2;   // 3
let multiplication = 5 * 2; // 10
let division = 5 / 2;       // 2
let reste = 5 % 2;          // 1
```

Avec des entiers, `5 / 2` donne `2`. La partie décimale est supprimée.

## Modifier une variable

```rust
let mut score = 10;

score += 5; // Identique à score = score + 5.
score -= 2; // Identique à score = score - 2.
```

## Combiner des conditions

```rust
let age = 20;
let billet = true;

if age >= 18 && billet {
    println!("Entrée autorisée");
}
```

- `&&` signifie « et ».
- `||` signifie « ou ».
- `!` inverse un booléen : `!true` donne `false`.

## À retenir

- `%` donne le reste d'une division.
- Une division entre entiers retourne un entier.
- `+=` et `-=` modifient une variable mutable.
- `&&`, `||` et `!` permettent de combiner des booléens.
