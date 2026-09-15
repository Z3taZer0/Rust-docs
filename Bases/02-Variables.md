# Variables

Une variable permet de donner un nom à une valeur. Elle se déclare avec `let`.

```rust
let nombre = 5;
let nom = "Alice";
```

Rust peut souvent trouver le type tout seul. Ici, `nombre` est un entier et `nom` est une chaîne de caractères de type `&str`.

Le type peut aussi être écrit explicitement après le nom :

```rust
let nombre: i32 = 5;
```

## Variables immuables

Par défaut, la valeur d'une variable ne peut pas être modifiée :

```rust
let nombre = 5;
nombre = 6; // Erreur : nombre est immuable.
```

## Variables mutables

Le mot-clé `mut` permet de modifier la valeur :

```rust
let mut nombre: i32 = 5;
nombre = 6;
```

## Chaînes de caractères modifiables

Une valeur de type `String` peut contenir du texte que l'on souhaite modifier :

```rust
let mut message = String::from("Bonjour");
message.push_str(", monde !");
```

Après `push_str`, `message` contient `"Bonjour, monde !"`.

## À retenir

- `let` déclare une variable.
- Une variable est immuable par défaut.
- `let mut` déclare une variable modifiable.
- `: i32` indique explicitement le type d'une variable.
