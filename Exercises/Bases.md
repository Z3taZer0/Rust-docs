# Exercices — Bases

Les exercices sont cumulatifs : chaque exercice peut employer les notions des cours précédents.

<a id="bases-cargo"></a>
## 01 — Préparer un projet de simulation

Crée un projet Cargo nommé `arena_simulator` dans un nouveau dossier. Le programme doit afficher `Simulation prête`, puis être vérifié et compilé sans être exécuté une seconde fois.

Contraintes :

- créer le projet avec Cargo ;
- identifier le fichier qui contient `main` ;
- utiliser une commande pour vérifier le code ;
- produire l'exécutable de développement.

Résultat attendu lors de la première exécution :

```text
Simulation prête
```

<details>
<summary>Correction</summary>

```powershell
cargo new arena_simulator
Set-Location arena_simulator
cargo run
cargo check
cargo build
```

Contenu de `src/main.rs` :

```rust
fn main() {
    println!("Simulation prête");
}
```

`cargo run` compile et exécute. `cargo check` vérifie sans produire l'exécutable final. `cargo build` crée l'exécutable de développement dans `target/debug/`.

</details>

<a id="bases-variables"></a>
## 02 — Suivre une session de jeu

Représente une session avec un nom de joueur, un niveau, un score et un état de connexion. Modifie le score et le niveau après une victoire, puis ajoute un suffixe au nom affiché.

Contraintes :

- utiliser un `String` modifiable pour le nom ;
- conserver l'état de connexion dans une variable immuable ;
- modifier le niveau et le score avec des variables mutables ;
- afficher toutes les valeurs à la fin.

Résultat attendu :

```text
Joueur : Ferris [vainqueur]
Niveau : 2
Score : 150
Connecté : true
```

<details>
<summary>Correction</summary>

```rust
fn main() {
    let mut player_name = String::from("Ferris");
    let mut level: u32 = 1;
    let mut score: u32 = 100;
    let connected = true;

    level += 1;
    score += 50;
    player_name.push_str(" [vainqueur]");

    println!("Joueur : {player_name}");
    println!("Niveau : {level}");
    println!("Score : {score}");
    println!("Connecté : {connected}");
}
```

</details>

<a id="bases-printing"></a>
## 03 — Afficher une fiche de personnage

Produis une fiche lisible à partir de quatre variables : nom, classe, points de vie et niveau.

Contraintes :

- afficher un titre entouré de `=` ;
- utiliser la capture directe `{variable}` au moins deux fois ;
- utiliser un emplacement `{}` au moins une fois ;
- ne pas écrire directement les valeurs dans les chaînes affichées.

Résultat attendu :

```text
=== FICHE ===
Nom : Ferris
Classe : Gardien
Niveau : 4
Vie : 85 / 100
```

<details>
<summary>Correction</summary>

```rust
fn main() {
    let name = "Ferris";
    let class = "Gardien";
    let level = 4;
    let health = 85;
    let max_health = 100;

    println!("=== FICHE ===");
    println!("Nom : {name}");
    println!("Classe : {class}");
    println!("Niveau : {level}");
    println!("Vie : {} / {}", health, max_health);
}
```

</details>

<a id="bases-constants"></a>
## 04 — Calculer une récompense limitée

Calcule la récompense d'une mission à partir d'un score de base et d'un multiplicateur global. Affiche aussi la limite maximale de points de vie du jeu.

Contraintes :

- déclarer le multiplicateur et la vie maximale comme constantes ;
- indiquer explicitement le type de chaque constante ;
- conserver le score de base dans une variable ;
- calculer la récompense sans recopier les valeurs numériques.

Résultat attendu :

```text
Récompense : 300
Vie maximale : 100
```

<details>
<summary>Correction</summary>

```rust
const REWARD_MULTIPLIER: u32 = 3;
const MAX_HEALTH: u32 = 100;

fn main() {
    let base_score: u32 = 100;
    let reward = base_score * REWARD_MULTIPLIER;

    println!("Récompense : {reward}");
    println!("Vie maximale : {MAX_HEALTH}");
}
```

</details>

<a id="bases-functions"></a>
## 05 — Séparer un calcul de combat

Écris un programme qui calcule les dégâts d'une attaque puis la vie restante d'un adversaire.

Contraintes :

- créer une fonction `calculate_damage(base, bonus)` qui retourne la somme ;
- créer une fonction `remaining_health(health, damage)` ;
- retourner immédiatement `0` lorsque les dégâts atteignent ou dépassent la vie ;
- ne réaliser aucun calcul de combat directement dans `main`.

Résultat attendu :

```text
Dégâts : 35
Vie restante : 45
```

<details>
<summary>Correction</summary>

```rust
fn calculate_damage(base: u32, bonus: u32) -> u32 {
    base + bonus
}

fn remaining_health(health: u32, damage: u32) -> u32 {
    if damage >= health {
        return 0;
    }

    health - damage
}

fn main() {
    let damage = calculate_damage(25, 10);
    let health = remaining_health(80, damage);

    println!("Dégâts : {damage}");
    println!("Vie restante : {health}");
}
```

</details>

<a id="bases-loops"></a>
## 06 — Simuler trois vagues

Simule trois vagues d'ennemis. Chaque vague contient autant d'ennemis que son numéro multiplié par deux. Affiche un compte à rebours avant la simulation et ignore l'ennemi numéro `2` de la deuxième vague.

Contraintes :

- utiliser `while` pour le compte à rebours ;
- utiliser deux boucles `for` imbriquées pour les vagues et les ennemis ;
- utiliser un intervalle inclusif ;
- utiliser `continue` pour ignorer l'ennemi demandé ;
- compter le nombre total d'ennemis traités.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let mut countdown = 3;

    while countdown > 0 {
        println!("Départ dans {countdown}");
        countdown -= 1;
    }

    let mut processed = 0;

    for wave in 1..=3 {
        println!("Vague {wave}");

        for enemy in 1..=wave * 2 {
            if wave == 2 && enemy == 2 {
                continue;
            }

            println!("Ennemi {enemy}");
            processed += 1;
        }
    }

    println!("Ennemis traités : {processed}");
}
```

</details>

<a id="bases-types"></a>
## 07 — Choisir les types d'un état de partie

Déclare les données d'une partie avec des types explicites adaptés : température négative, nombre de pièces, précision décimale, état actif, raccourci clavier et nom de zone.

Contraintes :

- utiliser exactement une fois chacun des types `i32`, `u32`, `f64`, `bool`, `char` et `&str` ;
- choisir des valeurs cohérentes avec leur type ;
- afficher chaque valeur ;
- ne faire aucune conversion de type.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let temperature: i32 = -12;
    let coins: u32 = 250;
    let accuracy: f64 = 0.875;
    let active: bool = true;
    let shortcut: char = 'M';
    let zone: &str = "Montagnes";

    println!("Zone : {zone}");
    println!("Température : {temperature}");
    println!("Pièces : {coins}");
    println!("Précision : {accuracy}");
    println!("Active : {active}");
    println!("Raccourci : {shortcut}");
}
```

</details>

<a id="bases-conditions"></a>
## 08 — Contrôler l'accès à une zone

Décide si un joueur peut entrer dans une zone selon son niveau, la possession d'une clé et l'état de la zone.

Règles :

- refuser si la zone est fermée ;
- sinon, autoriser un joueur de niveau `10` ou plus ;
- sinon, autoriser un joueur de niveau `5` ou plus qui possède la clé ;
- refuser tous les autres joueurs.

Le programme doit afficher une seule décision et préciser sa raison.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let level = 7;
    let has_key = true;
    let zone_open = true;

    if !zone_open {
        println!("Accès refusé : zone fermée");
    } else if level >= 10 {
        println!("Accès autorisé : niveau suffisant");
    } else if level >= 5 && has_key {
        println!("Accès autorisé : clé utilisée");
    } else {
        println!("Accès refusé : conditions insuffisantes");
    }
}
```

</details>

<a id="bases-arrays"></a>
## 09 — Analyser une série de dégâts

Analyse les dégâts `[12, 7, 19, 4, 15]`. Calcule leur total, compte les attaques d'au moins `10` dégâts et trouve la plus grande valeur.

Contraintes :

- conserver les valeurs dans un tableau de taille explicite ;
- utiliser une seule boucle `for` ;
- ne pas accéder aux éléments avec un indice numérique ;
- afficher le nombre de valeurs avec `len()`.

Résultat attendu :

```text
Attaques : 5
Total : 57
Attaques fortes : 3
Maximum : 19
```

<details>
<summary>Correction</summary>

```rust
fn main() {
    let damages: [u32; 5] = [12, 7, 19, 4, 15];
    let mut total = 0;
    let mut strong_attacks = 0;
    let mut maximum = 0;

    for damage in damages {
        total += damage;

        if damage >= 10 {
            strong_attacks += 1;
        }

        if damage > maximum {
            maximum = damage;
        }
    }

    println!("Attaques : {}", damages.len());
    println!("Total : {total}");
    println!("Attaques fortes : {strong_attacks}");
    println!("Maximum : {maximum}");
}
```

</details>

<a id="bases-operators"></a>
## 10 — Simuler une réserve d'énergie

Une réserve commence à `80`. Trois actions coûtent respectivement `15`, `30` et `50`. Une action est exécutée seulement si la réserve est suffisante et si le système est actif. Après chaque action réussie, ajoute un bonus égal au reste de la division de son coût par `4`.

Contraintes :

- employer `-=`, `+=`, `%`, `&&` et `!` ;
- compter les actions refusées ;
- empêcher la réserve de devenir négative en testant avant la soustraction.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let costs = [15, 30, 50];
    let mut energy = 80;
    let mut rejected = 0;
    let system_disabled = false;

    for cost in costs {
        if energy >= cost && !system_disabled {
            energy -= cost;
            energy += cost % 4;
            println!("Action exécutée, énergie : {energy}");
        } else {
            rejected += 1;
            println!("Action refusée");
        }
    }

    println!("Actions refusées : {rejected}");
}
```

</details>

<a id="bases-tuples"></a>
## 11 — Produire un rapport de combat

Écris une fonction qui reçoit un tableau de quatre dégâts et retourne un tuple contenant le total, la valeur maximale et le nombre d'attaques nulles.

Contraintes :

- le type retourné doit être `(u32, u32, u32)` ;
- effectuer l'analyse dans une boucle ;
- décomposer le tuple dans `main` ;
- afficher les trois résultats avec des noms explicites.

<details>
<summary>Correction</summary>

```rust
fn analyze(damages: [u32; 4]) -> (u32, u32, u32) {
    let mut total = 0;
    let mut maximum = 0;
    let mut misses = 0;

    for damage in damages {
        total += damage;

        if damage > maximum {
            maximum = damage;
        }

        if damage == 0 {
            misses += 1;
        }
    }

    (total, maximum, misses)
}

fn main() {
    let report = analyze([12, 0, 8, 20]);
    let (total, maximum, misses) = report;

    println!("Total : {total}");
    println!("Maximum : {maximum}");
    println!("Attaques manquées : {misses}");
}
```

</details>

<a id="bases-match"></a>
## 12 — Interpréter une commande de jeu

Une commande numérique représente une action : `1` attaque, `2` défend, `3` soigne et toute autre valeur attend. Utilise `match` pour produire à la fois un message et une variation de score.

Contraintes :

- faire retourner un tuple à `match` ;
- prévoir tous les cas avec `_` ;
- modifier le score après le `match` ;
- tester au moins quatre commandes dans une boucle.

<details>
<summary>Correction</summary>

```rust
fn main() {
    let commands = [1, 2, 3, 9];
    let mut score: i32 = 0;

    for command in commands {
        let (message, change) = match command {
            1 => ("Attaque", 10),
            2 => ("Défense", 5),
            3 => ("Soin", 3),
            _ => ("Attente", 0),
        };

        score += change;
        println!("{message} : score {score}");
    }
}
```

</details>
