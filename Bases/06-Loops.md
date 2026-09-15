# Boucles

Une boucle répète des instructions. Rust propose trois formes principales : `loop`, `while` et `for`.

## `loop`

`loop` répète ses instructions sans condition d'arrêt automatique.

```rust
let mut compteur = 0;

loop {
    compteur += 1;

    if compteur == 3 {
        break;
    }
}
```

`break` arrête la boucle.

Une boucle `loop` peut aussi produire une valeur :

```rust
let mut compteur = 0;

let resultat = loop {
    compteur += 1;

    if compteur == 10 {
        break compteur * 2;
    }
};
```

Ici, `break compteur * 2` arrête la boucle et donne la valeur `20` à `resultat`.

## `while`

`while` répète des instructions tant que sa condition est vraie :

```rust
let mut nombre = 3;

while nombre > 0 {
    println!("{nombre} !");
    nombre -= 1;
}
```

La boucle s'arrête lorsque `nombre > 0` devient faux.

## `for`

`for` parcourt les valeurs d'un intervalle ou d'une collection.

```rust
for nombre in 0..5 {
    println!("{nombre}");
}
```

L'intervalle `0..5` contient `0`, `1`, `2`, `3` et `4`. La dernière valeur, `5`, est exclue.

Une boucle `for` peut aussi parcourir un tableau :

```rust
let nombres = [10, 20, 30];

for nombre in nombres {
    println!("{nombre}");
}
```

## `continue`

`continue` ignore la fin de l'itération actuelle et passe directement à la suivante :

```rust
for nombre in 0..5 {
    if nombre == 2 {
        continue;
    }

    println!("{nombre}");
}
```

Ce programme n'affiche pas `2`.

## À retenir

- `loop` répète jusqu'à ce qu'une instruction l'arrête.
- `while` répète tant qu'une condition est vraie.
- `for` parcourt plusieurs valeurs.
- `break` quitte une boucle.
- `continue` passe à l'itération suivante.
