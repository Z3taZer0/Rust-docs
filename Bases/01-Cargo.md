# Cargo

Cargo est l'outil utilisé pour créer, compiler et exécuter un projet Rust.

## Créer un projet

Dans un dossier vide, cette commande initialise un projet :

```powershell
cargo init .
```

Cargo crée notamment les éléments suivants :

```text
mon-projet/
├── Cargo.toml
└── src/
    └── main.rs
```

- `Cargo.toml` contient les informations et les dépendances du projet.
- `src/main.rs` contient le point de départ du programme.

## Exécuter le programme

```powershell
cargo run
```

Cette commande compile le programme, puis l'exécute. Le code commence dans la fonction `main` :

```rust
fn main() {
    println!("Bonjour !");
}
```

## À retenir

- `cargo init .` crée un projet dans le dossier actuel.
- `cargo run` compile et exécute le projet.
- Le code principal se trouve dans `src/main.rs`.

Pour pratiquer cette notion, réalise [l'exercice 01 — Préparer un projet de simulation](../Exercises/Bases.md#bases-cargo). La correction se trouve avec l'énoncé.
