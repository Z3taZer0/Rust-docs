# Slices

Une slice est une référence vers une partie continue d'une collection. Elle ne possède pas les valeurs qu'elle contient.

## Slice de texte

Le type d'une slice de texte est `&str` :

```rust
let message = String::from("Bonjour Rust");
let bonjour = &message[0..7];

println!("{bonjour}");
```

`0..7` sélectionne les octets depuis la position `0` incluse jusqu'à la position `7` exclue. Il s'agit de la même [syntaxe d'intervalle](../Bases/06-Loops.md) que dans une boucle `for`.

Les chaînes Rust utilisent l'UTF-8. Une découpe effectuée au milieu d'un caractère accentué provoque une erreur lors de l'exécution. Il faut donc éviter de choisir des positions arbitraires dans un texte inconnu.

## Slice de tableau

Le type `&[i32]` représente une référence vers plusieurs valeurs `i32` consécutives :

```rust
fn afficher(nombres: &[i32]) {
    for nombre in nombres {
        println!("{nombre}");
    }
}

fn main() {
    let nombres = [10, 20, 30, 40];

    afficher(&nombres[1..3]); // Affiche 20 puis 30.
    afficher(&nombres);       // Affiche tout le tableau.
}
```

Une fonction qui reçoit une slice peut travailler avec tout un tableau ou seulement une partie de celui-ci.

## Petit exercice

Écris une fonction `somme` qui reçoit une slice `&[u32]`, additionne ses valeurs avec une boucle `for` et retourne le total.

## À retenir

- Une slice emprunte une partie continue d'une collection.
- `&str` est une slice de texte.
- `&[T]` est une slice de valeurs de type `T`.
- L'intervalle `début..fin` inclut le début et exclut la fin.
- Une slice ne possède pas les données qu'elle consulte.
