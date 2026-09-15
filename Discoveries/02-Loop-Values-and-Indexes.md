# Valeurs et indices dans une boucle

Une boucle `for` donne directement chaque valeur parcourue. Il n'est pas nécessaire de créer un compteur uniquement pour retrouver cette valeur dans le tableau.

## Compteur manuel inutile

```rust
let nombres = [10, 20, 30];
let mut index = 0;

for _ in nombres {
    println!("{}", nombres[index]);
    index += 1;
}
```

Dans cet exemple, `_` ignore la valeur fournie par la boucle. Le compteur sert ensuite à récupérer manuellement cette même valeur.

## Utiliser directement la valeur

```rust
let nombres = [10, 20, 30];

for nombre in nombres {
    println!("{nombre}");
}
```

À chaque tour, `nombre` contient déjà la valeur actuelle : `10`, puis `20`, puis `30`.

## Quand l'indice est nécessaire

`enumerate()` fournit à la fois l'indice et la valeur :

```rust
let nombres = [10, 20, 30];

for (index, nombre) in nombres.into_iter().enumerate() {
    println!("Indice {index} : {nombre}");
}
```

Cette forme est utile uniquement lorsque le programme utilise réellement la position.

## À retenir

- `for valeur in tableau` donne directement chaque valeur.
- `_` signifie que la valeur actuelle est volontairement ignorée.
- Un compteur manuel est inutile si seule la valeur est utilisée.
- `enumerate()` sert lorsque l'indice et la valeur sont tous les deux nécessaires.
