# Tableaux

Un tableau regroupe plusieurs valeurs du même type. Sa taille ne change pas.

```rust
let nombres = [10, 20, 30];
```

## Lire une valeur

Chaque valeur possède un indice. Le premier indice est `0`.

```rust
let nombres = [10, 20, 30];

println!("{}", nombres[0]); // Affiche 10.
println!("{}", nombres[2]); // Affiche 30.
```

Un indice qui n'existe pas provoque une erreur lors de l'exécution.

## Type et taille

Le type `[i32; 3]` signifie : un tableau de trois valeurs de type `i32`.

```rust
let nombres: [i32; 3] = [10, 20, 30];
```

La méthode `len()` donne le nombre d'éléments :

```rust
let nombres = [10, 20, 30];
println!("{}", nombres.len()); // Affiche 3.
```

## Parcourir un tableau

```rust
let nombres = [10, 20, 30];

for nombre in nombres {
    println!("{nombre}");
}
```

## À retenir

- Un tableau contient des valeurs du même type.
- Sa taille est fixe.
- Le premier indice est `0`.
- `len()` donne le nombre d'éléments.
- `for` permet de parcourir toutes les valeurs.

Pour pratiquer cette notion, réalise [l'exercice 09 — Analyser une série de dégâts](../Exercises/Bases.md#bases-arrays). La correction se trouve avec l'énoncé.
