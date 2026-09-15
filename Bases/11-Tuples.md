# Tuples

Un tuple regroupe plusieurs valeurs. Contrairement à un tableau, ses valeurs peuvent avoir des types différents.

```rust
let personne = ("Alice", 25, true);
```

## Lire une valeur

Chaque position possède un numéro qui commence à `0`.

```rust
let personne = ("Alice", 25, true);

println!("{}", personne.0); // Affiche Alice.
println!("{}", personne.1); // Affiche 25.
```

## Décomposer un tuple

Chaque valeur peut être placée dans une variable :

```rust
let personne = ("Alice", 25);
let (nom, age) = personne;

println!("{nom} a {age} ans");
```

## Type d'un tuple

```rust
let position: (i32, i32) = (10, -4);
```

Le type `(i32, i32)` décrit un tuple contenant deux entiers.

## À retenir

- Un tuple peut contenir plusieurs types.
- Sa taille est fixe.
- `.0`, `.1` et les numéros suivants donnent accès à ses valeurs.
- Un tuple peut être décomposé en plusieurs variables.
