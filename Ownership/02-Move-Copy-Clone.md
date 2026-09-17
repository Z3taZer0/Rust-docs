# `Move`, `Copy` et `Clone`

Une affectation ne produit pas toujours une nouvelle valeur indépendante. Son comportement dépend du type utilisé.

## Déplacer un `String`

```rust
let premier = String::from("Rust");
let second = premier;

println!("{second}");
```

La propriété du texte passe de `premier` à `second`. Ce transfert s'appelle un **move**. Après celui-ci, `premier` ne peut plus être utilisé.

```rust
let premier = String::from("Rust");
let second = premier;

// println!("{premier}"); // Erreur : la valeur a été déplacée.
println!("{second}");
```

## Copier une valeur simple

Les types simples comme `i32`, `u32`, `bool` et `char` implémentent généralement `Copy` :

```rust
let premier = 5;
let second = premier;

println!("{premier}, {second}");
```

Ici, la valeur `5` est copiée. Les deux variables restent utilisables.

## Dupliquer avec `clone()`

Pour créer volontairement une copie complète d'un `String`, il faut utiliser `clone()` :

```rust
let premier = String::from("Rust");
let second = premier.clone();

println!("{premier}, {second}");
```

Une copie complète peut demander plus de travail qu'un simple déplacement. `clone()` rend ce coût visible dans le code.

## À retenir

- Une affectation déplace généralement un `String`.
- Les valeurs simples sont souvent copiées automatiquement.
- `clone()` crée explicitement une copie complète.

Pour pratiquer cette notion, réalise [l'exercice 02 — Transférer une fiche de joueur](../Exercises/Ownership.md#ownership-move-copy-clone). La correction se trouve avec l'énoncé.
