# `Result`

`Result` représente une opération qui peut réussir ou échouer. Ce type possède deux variantes :

- `Ok(valeur)` contient le résultat réussi ;
- `Err(erreur)` contient une description de l'échec.

```rust
fn verifier_score(score: i32) -> Result<i32, String> {
    if score < 0 {
        Err(String::from("Le score ne peut pas être négatif"))
    } else {
        Ok(score)
    }
}
```

`Result<i32, String>` signifie que la fonction retourne soit un `i32`, soit un message d'erreur de type `String`.

## Traiter le résultat

```rust
fn verifier_score(score: i32) -> Result<i32, String> {
    if score < 0 {
        Err(String::from("Le score ne peut pas être négatif"))
    } else {
        Ok(score)
    }
}

match verifier_score(-5) {
    Ok(score) => println!("Score : {score}"),
    Err(erreur) => println!("Erreur : {erreur}"),
}
```

Le programme décide ainsi quoi faire dans chaque situation au lieu d'ignorer silencieusement l'erreur.

## Différence entre `Option` et `Result`

- `Option<T>` indique seulement si une valeur existe ;
- `Result<T, E>` explique aussi pourquoi une opération a échoué avec une erreur de type `E`.

## À retenir

- `Result<T, E>` contient `Ok(T)` ou `Err(E)`.
- `Ok` représente une réussite.
- `Err` représente un échec explicite.
- `match` permet de traiter les deux résultats.

Pour pratiquer cette notion, réalise [l'exercice 05 — Valider une transaction](../Exercises/Structured-Types.md#structured-result). La correction se trouve avec l'énoncé.
