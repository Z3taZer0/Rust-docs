# Borrowing

Une référence permet d'utiliser une valeur sans en prendre la propriété. Cette utilisation temporaire s'appelle un **emprunt** ou *borrowing*.

```rust
fn longueur(texte: &String) -> usize {
    texte.len()
}

fn main() {
    let message = String::from("Bonjour");
    let taille = longueur(&message);

    println!("{message} occupe {taille} octets");
}
```

`&message` crée une référence vers `message`. Le type `&String` indique que la fonction reçoit cette référence.

La fonction `longueur` emprunte le texte. Elle ne le possède donc pas, et `message` reste utilisable après l'appel.

## Un emprunt ne modifie pas la valeur

Une référence ordinaire est en lecture seule :

```rust
fn afficher(texte: &String) {
    println!("{texte}");
}
```

La fonction peut lire le texte, mais elle ne peut pas le modifier.

## Petit exercice

Écris une fonction `est_long` qui reçoit `&String` et retourne `true` lorsque la longueur du texte dépasse 10 octets.

## À retenir

- `&valeur` crée une référence.
- Une référence permet d'emprunter une valeur sans la déplacer.
- Une référence ordinaire permet de lire, mais pas de modifier.
- Le propriétaire peut réutiliser sa valeur après l'emprunt.
