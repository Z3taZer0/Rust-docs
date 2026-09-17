# Affichage avec `println!`

La macro `println!` affiche une ligne dans le terminal.

```rust
println!("Bonjour !");
```

## Afficher une variable

Une paire d'accolades `{}` réserve une place pour la valeur donnée après le texte :

```rust
let resultat = 42;
println!("Le résultat est : {}", resultat);
```

Rust permet aussi d'écrire directement le nom d'une variable entre les accolades :

```rust
let resultat = 42;
println!("Le résultat est : {resultat}");
```

Ces deux exemples affichent :

```text
Le résultat est : 42
```

Les accolades peuvent contenir un nom de variable, mais pas un appel de fonction complet :

```rust
let resultat = String::from("Bonjour");
println!("{resultat}");
```

## Pourquoi y a-t-il un `!` ?

`println!` est une macro. En Rust, le nom d'une macro se termine par `!` lorsqu'on l'utilise.

Pour le moment, il suffit de retenir qu'une macro ressemble à une fonction, mais qu'elle peut accepter une syntaxe plus flexible.

## À retenir

- `println!` affiche une ligne.
- `{}` indique où placer une valeur.
- `{nom}` affiche directement une variable appelée `nom`.
- Le `!` indique que `println!` est une macro.

Pour pratiquer cette notion, réalise [l'exercice 03 — Afficher une fiche de personnage](../Exercises/Bases.md#bases-printing). La correction se trouve avec l'énoncé.
