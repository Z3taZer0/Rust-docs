# Fonctions

Une fonction regroupe des instructions sous un nom. Elle se déclare avec `fn`.

```rust
fn dire_bonjour() {
    println!("Bonjour !");
}
```

Pour exécuter cette fonction, il faut l'appeler :

```rust
fn main() {
    dire_bonjour();
}
```

Une fonction peut être écrite avant ou après `main`.

## Paramètres

Les paramètres permettent de donner des valeurs à une fonction. Leur type doit être indiqué.

```rust
fn afficher_nombre(nombre: i32) {
    println!("{nombre}");
}
```

Ici, `nombre` est un paramètre de type `i32`.

## Retourner une valeur

La flèche `->` indique le type de la valeur retournée :

```rust
fn addition(a: i32, b: i32) -> i32 {
    a + b
}
```

La dernière expression de la fonction est retournée. Elle ne possède pas de point-virgule.

```rust
a + b  // Cette valeur est retournée.
a + b; // Cette instruction ne retourne pas le résultat.
```

## Utiliser `return`

Le mot-clé `return` retourne immédiatement une valeur et arrête la fonction :

```rust
fn est_positif(nombre: i32) -> bool {
    if nombre < 0 {
        return false;
    }

    true
}
```

Dans cet exemple :

- un nombre négatif retourne immédiatement `false` ;
- sinon, la dernière expression retourne `true`.

## À retenir

- `fn` déclare une fonction.
- Les paramètres ont toujours un type.
- `-> Type` indique le type retourné.
- La dernière expression sans `;` peut être retournée automatiquement.
- `return` permet de retourner une valeur immédiatement.
