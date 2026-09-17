# Conditions

Une condition permet d'exécuter du code seulement lorsqu'une expression est vraie.

## `if` et `else`

```rust
let age = 20;

if age >= 18 {
    println!("Majeur");
} else {
    println!("Mineur");
}
```

La condition ne nécessite pas de parenthèses. Son résultat doit être un `bool`, donc `true` ou `false`.

## Plusieurs possibilités

```rust
let score = 75;

if score >= 90 {
    println!("Excellent");
} else if score >= 50 {
    println!("Réussi");
} else {
    println!("Échoué");
}
```

## Comparaisons

| Opérateur | Signification |
|---|---|
| `==` | égal à |
| `!=` | différent de |
| `<` | plus petit que |
| `>` | plus grand que |
| `<=` | plus petit ou égal à |
| `>=` | plus grand ou égal à |

## À retenir

- `if` exécute un bloc lorsque sa condition est vraie.
- `else if` teste une autre condition.
- `else` s'exécute lorsqu'aucune condition précédente n'est vraie.
- `=` donne une valeur, tandis que `==` compare deux valeurs.

Pour pratiquer cette notion, réalise [l'exercice 08 — Contrôler l'accès à une zone](../Exercises/Bases.md#bases-conditions). La correction se trouve avec l'énoncé.
