]"{|'
],LP-[;.GBHYUIJMN7TFR5V64SWXS/]
\Un **bloc** est un groupe d'instructions placé entre des accolades `{}`. Les fonctions, les conditions et les boucles contiennent toutes des blocs.

```rust
fn main() { // Début du bloc de la fonction.
    let dehors = 10;

    { // Début d'un bloc intérieur.
        let dedans = 20;
        println!("{dehors}, {dedans}");
    } // Fin du bloc intérieur.

    println!("{dehors}");
    // println!("{dedans}"); // Erreur : `dedans` n'existe plus ici.
} // Fin du bloc de la fonction.
```

Un bloc peut en contenir un autre. La **portée** d'une variable est la zone du programme dans laquelle son nom peut être utilisé. Elle commence à sa déclaration et se termine généralement à la fin du bloc où elle a été créée.

Dans cet exemple, `dehors` reste accessible dans le bloc intérieur. En revanche, `dedans` n'est accessible que dans son propre bloc.

## Propriété et fin d'un bloc

Chaque valeur Rust possède une variable appelée son **propriétaire**. Lorsque le propriétaire quitte son bloc, Rust libère automatiquement la mémoire de la valeur.

```rust
fn main() {
    {
        let message = String::from("Bonjour");
        println!("{message}");
    } // `message` quitte son bloc : sa mémoire est libérée.
}
```

`String` permet de créer un texte qui peut grandir. Sa taille n'étant pas connue à l'avance, une partie de sa mémoire est réservée pendant l'exécution du programme.

## Les trois règles

1. Chaque valeur possède un propriétaire.
2. Une valeur ne peut avoir qu'un seul propriétaire à la fois.
3. Lorsque le propriétaire quitte son bloc, la valeur est supprimée.

Ces règles permettent à Rust de libérer la mémoire automatiquement, sans appeler manuellement une fonction de nettoyage.

## Petit exercice

Crée une variable `nom` contenant un `String` dans un bloc intérieur. Affiche-la dans ce bloc, puis observe pourquoi elle ne peut plus être utilisée après la fermeture du bloc.

## À retenir

- Un bloc regroupe des instructions entre `{` et `}`.
- La portée indique où une variable peut être utilisée.
- Une variable est propriétaire de sa valeur.
- La portée d'une variable se termine à la fermeture de son bloc.
- Rust libère alors automatiquement la mémoire possédée.
