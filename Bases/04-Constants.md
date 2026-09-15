# Constantes

Une constante représente une valeur qui ne changera jamais. Elle se déclare avec `const`.

```rust
const MAX_POINTS: u32 = 100_000;
```

Le type d'une constante doit toujours être écrit. Dans cet exemple, le type est `u32`.

Par convention, le nom d'une constante est écrit en majuscules. Les mots sont séparés par des `_`.

## Constante ou variable ?

```rust
const MAX_POINTS: u32 = 100_000;
let points: u32 = 50;
```

- `MAX_POINTS` représente une limite fixe.
- `points` représente une valeur utilisée par le programme.

## À retenir

- `const` déclare une constante.
- Une constante ne peut pas être modifiée.
- Son type doit être indiqué.
- Son nom s'écrit généralement en majuscules.
