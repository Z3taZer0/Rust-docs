# `String` et `&str`

Rust utilise souvent deux formes de texte : `String` et `&str`.

## `String`

Un `String` possède son contenu et peut être modifié :

```rust
let mut message = String::from("Bonjour");
message.push_str(" Rust");

println!("{message}");
```

## `&str`

Un `&str` est une vue empruntée sur du texte :

```rust
let langage: &str = "Rust";
println!("{langage}");
```

Un texte écrit directement entre guillemets est un `&str`. Il est inclus dans le programme et n'est pas modifiable.

## Préférer `&str` pour lire du texte

Une fonction qui doit seulement lire du texte peut recevoir `&str` :

```rust
fn afficher(texte: &str) {
    println!("{texte}");
}

fn main() {
    let message = String::from("Bonjour");

    afficher(&message);
    afficher("Salut");
}
```

La même fonction accepte alors une référence vers un `String` et un texte écrit directement dans le code.

## À retenir

- `String` possède un texte qui peut grandir ou changer.
- `&str` emprunte une vue sur du texte.
- Un texte littéral comme `"Rust"` est un `&str`.
- Pour une fonction qui lit seulement du texte, `&str` est généralement le type le plus pratique.

Pour pratiquer cette notion, réalise [l'exercice 05 — Produire des descriptions à partir de plusieurs textes](../Exercises/Ownership.md#ownership-string-str). La correction se trouve avec l'énoncé.
