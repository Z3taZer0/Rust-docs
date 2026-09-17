# Exercices — Ownership

Chaque exercice demande d'indiquer, avant de consulter la correction, quelles variables possèdent une valeur et quelles fonctions l'empruntent ou la déplacent.

<a id="ownership-scope"></a>
## 01 — Construire un rapport avec des portées

Crée un rapport de mission dont le titre reste disponible pendant tout le programme. Dans deux blocs intérieurs successifs, crée un message temporaire différent et calcule un nombre de points. Après chaque bloc, le message temporaire doit être libéré, mais le total et le titre doivent rester utilisables.

Contraintes :

- utiliser un `String` dans le bloc principal ;
- créer un autre `String` dans chaque bloc intérieur ;
- modifier un total déclaré dans le bloc principal ;
- afficher le titre et le total après la fermeture des deux blocs ;
- commenter une ligne qui ne compilerait pas parce qu'elle utilise une variable hors de sa portée.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let title = String::from("Rapport de mission");
    let mut total = 0;

    {
        let message = String::from("Objectif principal terminé");
        total += 100;
        println!("{message} : {total} points");
    }

    {
        let message = String::from("Bonus découvert");
        total += 25;
        println!("{message} : {total} points");
    }

    println!("{title} : {total} points");
    // println!("{message}"); // `message` n'existe plus hors de son bloc.
}
```

`title` et `total` appartiennent au bloc de `main`. Chaque variable `message` appartient uniquement à son bloc intérieur et est supprimée à sa fermeture.

</details>

<a id="ownership-move-copy-clone"></a>
## 02 — Transférer une fiche de joueur

Simule l'inscription d'un joueur. Une fonction doit prendre la propriété de son nom, lui ajouter un statut et retourner le `String`. Avant le transfert, conserve volontairement une copie du nom original. Copie également un identifiant numérique sans rendre l'original inutilisable.

Contraintes :

- la fonction reçoit et retourne un `String` ;
- déplacer le nom vers la fonction ;
- utiliser `clone()` une seule fois pour conserver l'original ;
- démontrer que l'identifiant `u32` reste utilisable après son affectation.

<details>
<summary>Correction</summary>

```rust
fn register(mut name: String) -> String {
    name.push_str(" [inscrit]");
    name
}

fn main() {
    let original_name = String::from("Ferris");
    let backup_name = original_name.clone();
    let registered_name = register(original_name);

    let player_id: u32 = 42;
    let copied_id = player_id;

    println!("Original conservé : {backup_name}");
    println!("Nom enregistré : {registered_name}");
    println!("Identifiants : {player_id}, {copied_id}");
}
```

`original_name` est déplacé vers `register`. La fonction retourne ensuite la propriété du `String` modifié. `backup_name` possède une copie indépendante. Le nombre est copié automatiquement.

</details>

<a id="ownership-borrowing"></a>
## 03 — Inspecter un profil sans le déplacer

Écris plusieurs fonctions qui lisent le même nom de joueur : l'une affiche le profil, l'autre retourne sa longueur en octets et la dernière vérifie s'il dépasse une limite. Le propriétaire doit encore pouvoir modifier le nom après tous les appels.

Contraintes :

- chaque fonction de lecture reçoit `&String` ;
- aucune fonction ne retourne le `String` ;
- appeler au moins deux fonctions plusieurs fois avec la même valeur ;
- modifier le propriétaire après les emprunts.

<details>
<summary>Correction</summary>

```rust
fn display_profile(name: &String) {
    println!("Joueur : {name}");
}

fn name_length(name: &String) -> usize {
    name.len()
}

fn exceeds_limit(name: &String, limit: usize) -> bool {
    name.len() > limit
}

fn main() {
    let mut name = String::from("Ferris");

    display_profile(&name);
    println!("Longueur : {}", name_length(&name));
    println!("Trop long : {}", exceeds_limit(&name, 10));

    name.push_str(" le Brave");

    display_profile(&name);
    println!("Longueur : {}", name_length(&name));
}
```

Les références permettent aux trois fonctions de lire le même `String`. Chaque emprunt se termine après son dernier usage, puis le propriétaire peut modifier la valeur.

</details>

<a id="ownership-mutable-references"></a>
## 04 — Modifier un état de combat par emprunt

Crée trois fonctions : une retire des points de vie, une soigne le joueur et une ajoute une ligne à un journal de combat. Toutes les modifications doivent passer par des références mutables.

Contraintes :

- ne retourner ni les points de vie ni le journal ;
- empêcher les points de vie de descendre sous `0` ;
- appliquer deux attaques et un soin ;
- utiliser successivement plusieurs références mutables vers les mêmes propriétaires ;
- afficher l'état final dans `main`.

<details>
<summary>Correction</summary>

```rust
fn damage(health: &mut u32, amount: u32) {
    if amount >= *health {
        *health = 0;
    } else {
        *health -= amount;
    }
}

fn heal(health: &mut u32, amount: u32) {
    *health += amount;
}

fn add_log(log: &mut String, message: &str) {
    log.push_str(message);
    log.push('\n');
}

fn main() {
    let mut health = 100;
    let mut log = String::from("Combat\n");

    damage(&mut health, 30);
    add_log(&mut log, "Le joueur perd 30 PV");

    heal(&mut health, 10);
    add_log(&mut log, "Le joueur récupère 10 PV");

    damage(&mut health, 25);
    add_log(&mut log, "Le joueur perd 25 PV");

    println!("{log}Vie finale : {health}");
}
```

`*health` accède à la valeur située derrière la référence mutable. Les emprunts sont successifs : aucune paire de références mutables n'est utilisée simultanément.

</details>

<a id="ownership-string-str"></a>
## 05 — Produire des descriptions à partir de plusieurs textes

Écris une fonction qui reçoit n'importe quelle vue de texte et retourne une catégorie selon sa longueur. Utilise-la avec un littéral, un `String` construit pendant l'exécution et une référence vers ce `String`.

Contraintes :

- la fonction reçoit `&str` ;
- retourner uniquement des littéraux `&str` ;
- construire un nom complet avec `String` et `push_str()` ;
- appeler la fonction au moins trois fois ;
- prouver que le `String` reste utilisable après les appels.

<details>
<summary>Correction</summary>

```rust
fn category(text: &str) -> &str {
    if text.len() <= 5 {
        "court"
    } else if text.len() <= 10 {
        "moyen"
    } else {
        "long"
    }
}

fn main() {
    let literal = "Rust";
    let mut player_name = String::from("Ferris");
    player_name.push_str(" le Brave");

    println!("{literal} : {}", category(literal));
    println!("Ferris : {}", category("Ferris"));
    println!("{player_name} : {}", category(&player_name));
    println!("Le propriétaire conserve : {player_name}");
}
```

Une référence vers un `String` peut être utilisée comme `&str` pour une fonction qui lit uniquement le texte.

</details>

<a id="ownership-slices"></a>
## 06 — Analyser une fenêtre de combat

Une partie contient huit valeurs de dégâts. Écris une fonction qui analyse n'importe quelle partie continue de ce tableau et retourne son total et sa valeur maximale. Compare ensuite le combat complet, les trois premiers tours et les quatre derniers.

Contraintes :

- la fonction reçoit `&[u32]` ;
- ne pas recopier les tableaux dans la fonction ;
- appeler la même fonction avec trois slices différentes ;
- retourner un tuple `(total, maximum)` ;
- laisser le tableau original utilisable après toutes les analyses.

<details>
<summary>Correction</summary>

```rust
fn analyze(damages: &[u32]) -> (u32, u32) {
    let mut total = 0;
    let mut maximum = 0;

    for damage in damages {
        total += damage;

        if *damage > maximum {
            maximum = *damage;
        }
    }

    (total, maximum)
}

fn display(label: &str, damages: &[u32]) {
    let (total, maximum) = analyze(damages);
    println!("{label} : total {total}, maximum {maximum}");
}

fn main() {
    let damages = [8, 12, 5, 20, 7, 11, 4, 16];

    display("Combat complet", &damages);
    display("Trois premiers tours", &damages[0..3]);
    display("Quatre derniers tours", &damages[4..8]);

    println!("Nombre total de tours : {}", damages.len());
}
```

Chaque slice emprunte une zone différente du même tableau. La fonction ne possède aucune de ces données.

</details>
