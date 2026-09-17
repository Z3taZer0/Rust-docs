# Vectors

Un `Vec<T>` stocke plusieurs valeurs du même type. Contrairement à un tableau, sa taille peut changer pendant l'exécution.

```rust
let mut scores: Vec<u32> = Vec::new();

scores.push(10);
scores.push(20);
scores.push(30);
```

`Vec::new()` crée un vector vide et `push()` ajoute une valeur à la fin.

## La macro `vec!`

La macro `vec!` crée directement un vector contenant des valeurs :

```rust
let scores = vec![10, 20, 30];
```

Le point d'exclamation indique que `vec!` est une macro. Les macros seront détaillées plus tard ; ici, il suffit de retenir cette syntaxe de création.

## Parcourir sans déplacer

```rust
let scores = vec![10, 20, 30];

for score in &scores {
    println!("{score}");
}

println!("Nombre de scores : {}", scores.len());
```

`&scores` emprunte le vector. Il reste donc utilisable après la boucle.

## Lire une position avec `get()`

```rust
let scores = vec![10, 20, 30];

match scores.get(1) {
    Some(score) => println!("{score}"),
    None => println!("Cette position n'existe pas"),
}
```

`get()` retourne une `Option` au lieu d'arrêter le programme lorsqu'une position n'existe pas.

## Supprimer une valeur

```rust
let mut scores = vec![10, 20, 30];
let dernier = scores.pop();

match dernier {
    Some(score) => println!("Score retiré : {score}"),
    None => println!("Le vector était vide"),
}
```

`pop()` supprime la dernière valeur et retourne une `Option`.

## À retenir

- `Vec<T>` contient un nombre variable de valeurs de type `T`.
- `push()` ajoute une valeur et `pop()` retire la dernière.
- `&vector` permet de parcourir sans déplacer le vector.
- `get()` retourne une `Option` et évite un accès invalide.

Pour pratiquer cette notion, réalise [l'exercice 06 — Gérer un inventaire dynamique](../Exercises/Structured-Types.md#structured-vectors). La correction se trouve avec l'énoncé.
