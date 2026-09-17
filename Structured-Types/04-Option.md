# `Option`

`Option` représente une valeur qui peut être présente ou absente. Ce type possède deux variantes :

- `Some(valeur)` contient une valeur ;
- `None` indique l'absence de valeur.

```rust
fn division(a: i32, b: i32) -> Option<i32> {
    if b == 0 {
        None
    } else {
        Some(a / b)
    }
}
```

`Option<i32>` signifie que la fonction retourne soit un entier, soit aucune valeur.

## Utiliser `match`

```rust
fn division(a: i32, b: i32) -> Option<i32> {
    if b == 0 {
        None
    } else {
        Some(a / b)
    }
}

match division(10, 2) {
    Some(resultat) => println!("{resultat}"),
    None => println!("Division impossible"),
}
```

## Utiliser `if let`

`if let` est une forme courte lorsque seule une variante est utile :

```rust
let bonus = Some(50);

if let Some(points) = bonus {
    println!("Bonus : {points}");
}
```

Le bloc s'exécute uniquement si `bonus` contient `Some`.

## Pourquoi ne pas utiliser une valeur spéciale ?

Retourner `0` pour signaler une absence serait ambigu : `0` peut aussi être un résultat valide. `Option` oblige le programme à distinguer explicitement une valeur présente d'une valeur absente.

## À retenir

- `Option<T>` contient `Some(T)` ou `None`.
- `match` traite les deux possibilités.
- `if let` traite facilement une variante précise.
- `Option` représente une absence sans valeur spéciale ambiguë.

Pour pratiquer cette notion, réalise [l'exercice 04 — Rechercher un objet sans valeur spéciale](../Exercises/Structured-Types.md#structured-option). La correction se trouve avec l'énoncé.
