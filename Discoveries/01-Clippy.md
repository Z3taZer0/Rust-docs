# Clippy

Clippy est le linter officiel de Rust. Il examine du code qui compile et signale notamment des écritures inutiles, compliquées ou peu habituelles.

## Lancer Clippy

Dans le dossier qui contient `Cargo.toml` :

```powershell
cargo clippy
```

## Comprendre le résultat

```text
warning: the variable `x` is used as a loop counter
help: consider using ...
```

- `warning` indique un avertissement. Le programme peut tout de même compiler et fonctionner.
- `help` propose une autre écriture.
- Une suggestion de Clippy n'est pas une obligation et peut utiliser une notion encore inconnue.

Clippy vérifie principalement la qualité et les habitudes d'écriture. Un avertissement ne signifie donc pas automatiquement que le résultat du programme est incorrect.

## Utiliser une suggestion

Avant de modifier le code, il faut identifier :

- ce que Clippy considère comme inutile ou risqué ;
- si la suggestion conserve le même comportement ;
- si les notions proposées sont déjà comprises.

Il vaut mieux conserver une version claire et comprise que copier une correction inconnue uniquement pour supprimer un avertissement.

## À retenir

- `cargo clippy` analyse le projet.
- Un avertissement n'est pas une erreur de compilation.
- Le message explique le problème et propose souvent une solution.
- Une suggestion doit être comprise avant d'être appliquée.
