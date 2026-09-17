# Exercices — Types structurés

Ces exercices construisent progressivement les types d'un petit jeu. Le projet de synthèse réunit toutes les notions du groupe.

<a id="structured-structs"></a>
## 01 — Modéliser les données d'une arène

Crée trois formes de structs pour représenter une arène : une struct à champs nommés pour un combattant, une tuple struct pour son identifiant et une unit struct servant de marqueur pour le joueur contrôlé.

Contraintes :

- `Fighter` contient un nom, une position `x` et `y`, ainsi que des points de vie ;
- `FighterId` contient un `u32` ;
- `Controlled` ne contient aucune donnée ;
- créer deux combattants, puis déplacer le premier en modifiant ses champs ;
- afficher les données des deux combattants et l'identifiant du premier.

<details>
<summary>Correction</summary>

```rust
struct Fighter {
    name: String,
    x: f32,
    y: f32,
    health: u32,
}

struct FighterId(u32);
struct Controlled;

fn main() {
    let first_id = FighterId(1);
    let _controlled = Controlled;

    let mut first = Fighter {
        name: String::from("Ferris"),
        x: 0.0,
        y: 0.0,
        health: 100,
    };

    let second = Fighter {
        name: String::from("Crab"),
        x: 8.0,
        y: 3.0,
        health: 80,
    };

    first.x += 2.5;
    first.y += 1.0;

    println!("Joueur {} : {}", first_id.0, first.name);
    println!("Position : {}, {}", first.x, first.y);
    println!("Vie : {}", first.health);
    println!("Adversaire : {} ({} PV)", second.name, second.health);
}
```

Le préfixe `_` de `_controlled` indique que la variable est volontairement inutilisée.

</details>

<a id="structured-methods"></a>
## 02 — Encapsuler les actions d'un personnage

Transforme les opérations d'un personnage en méthodes. Le code de `main` ne doit modifier directement aucun champ après la création du personnage.

Contraintes :

- construire le personnage avec `Player::new(name)` ;
- ajouter les méthodes `take_damage`, `heal`, `is_alive` et `display` ;
- empêcher la vie de descendre sous `0` ;
- limiter le soin à `100` sans utiliser de méthode non étudiée ;
- appliquer plusieurs actions et afficher l'état final.

<details>
<summary>Correction</summary>

```rust
struct Player {
    name: String,
    health: u32,
}

impl Player {
    fn new(name: String) -> Self {
        Self { name, health: 100 }
    }

    fn take_damage(&mut self, amount: u32) {
        if amount >= self.health {
            self.health = 0;
        } else {
            self.health -= amount;
        }
    }

    fn heal(&mut self, amount: u32) {
        if self.health + amount > 100 {
            self.health = 100;
        } else {
            self.health += amount;
        }
    }

    fn is_alive(&self) -> bool {
        self.health > 0
    }

    fn display(&self) {
        println!("{} : {} PV", self.name, self.health);
    }
}

fn main() {
    let mut player = Player::new(String::from("Ferris"));

    player.take_damage(35);
    player.heal(20);
    player.take_damage(10);
    player.display();

    println!("En vie : {}", player.is_alive());
}
```

</details>

<a id="structured-enums"></a>
## 03 — Traiter une suite d'événements

Définis un enum `GameEvent` capable de représenter un déplacement, des dégâts, un message ou une attente. Écris une fonction qui reçoit un événement et affiche précisément son contenu.

Contraintes :

- `Move` contient deux `i32` ;
- `Damage` contient un `u32` ;
- `Message` contient un `String` ;
- `Wait` ne contient rien ;
- chaque variante doit être traitée sans utiliser `_` ;
- appeler la fonction avec les quatre variantes.

<details>
<summary>Correction</summary>

```rust
enum GameEvent {
    Move(i32, i32),
    Damage(u32),
    Message(String),
    Wait,
}

fn handle(event: GameEvent) {
    match event {
        GameEvent::Move(x, y) => println!("Déplacement vers {x}, {y}"),
        GameEvent::Damage(amount) => println!("Dégâts reçus : {amount}"),
        GameEvent::Message(text) => println!("Message : {text}"),
        GameEvent::Wait => println!("Aucune action"),
    }
}

fn main() {
    handle(GameEvent::Move(4, -2));
    handle(GameEvent::Damage(15));
    handle(GameEvent::Message(String::from("Porte ouverte")));
    handle(GameEvent::Wait);
}
```

La fonction prend la propriété de chaque événement. La variante `Message` déplace également son `String` dans la variable `text` du bras correspondant.

</details>

<a id="structured-option"></a>
## 04 — Rechercher un objet sans valeur spéciale

Recherche un objet dans un inventaire fixe. La fonction doit retourner la position trouvée avec `Some` ou signaler son absence avec `None`.

Contraintes :

- recevoir l'inventaire sous la forme `&[&str]` ;
- recevoir le nom recherché sous la forme `&str` ;
- retourner `Option<usize>` ;
- ne retourner ni `0` ni la longueur pour signaler un échec ;
- traiter une recherche avec `match` et une autre avec `if let`.

<details>
<summary>Correction</summary>

```rust
fn find_item(inventory: &[&str], target: &str) -> Option<usize> {
    let mut index = 0;

    for item in inventory {
        if *item == target {
            return Some(index);
        }

        index += 1;
    }

    None
}

fn main() {
    let inventory = ["Potion", "Clé", "Carte", "Corde"];

    match find_item(&inventory, "Carte") {
        Some(index) => println!("Carte trouvée à la position {index}"),
        None => println!("Carte absente"),
    }

    if let Some(index) = find_item(&inventory, "Potion") {
        println!("Potion trouvée à la position {index}");
    }

    match find_item(&inventory, "Épée") {
        Some(index) => println!("Épée trouvée à la position {index}"),
        None => println!("Épée absente"),
    }
}
```

</details>

<a id="structured-result"></a>
## 05 — Valider une transaction

Écris une fonction qui tente d'acheter un objet. Elle doit distinguer une transaction valide de deux erreurs différentes : prix nul et solde insuffisant.

Contraintes :

- recevoir le solde et le prix en `u32` ;
- retourner `Result<u32, String>` ;
- retourner le nouveau solde avec `Ok` ;
- produire un message différent pour chaque erreur ;
- tester trois achats dans `main` et traiter chacun avec `match`.

<details>
<summary>Correction</summary>

```rust
fn purchase(balance: u32, price: u32) -> Result<u32, String> {
    if price == 0 {
        Err(String::from("Le prix doit être supérieur à zéro"))
    } else if price > balance {
        Err(String::from("Solde insuffisant"))
    } else {
        Ok(balance - price)
    }
}

fn display_purchase(balance: u32, price: u32) {
    match purchase(balance, price) {
        Ok(remaining) => println!("Achat accepté, solde : {remaining}"),
        Err(error) => println!("Achat refusé : {error}"),
    }
}

fn main() {
    display_purchase(100, 35);
    display_purchase(20, 50);
    display_purchase(100, 0);
}
```

</details>

<a id="structured-vectors"></a>
## 06 — Gérer un inventaire dynamique

Crée un type `Inventory` qui possède un `Vec<String>` et une capacité maximale. Ses méthodes doivent ajouter, retirer et afficher des objets sans exposer la logique de gestion dans `main`.

Contraintes :

- construire un inventaire vide avec une fonction associée ;
- `add` retourne `Result<usize, String>` avec le nouveau nombre d'objets ;
- refuser un ajout lorsque la capacité est atteinte ;
- `remove_last` retourne `Option<String>` ;
- parcourir les objets par emprunt dans une méthode `display`.

<details>
<summary>Correction</summary>

```rust
struct Inventory {
    items: Vec<String>,
    capacity: usize,
}

impl Inventory {
    fn new(capacity: usize) -> Self {
        Self {
            items: Vec::new(),
            capacity,
        }
    }

    fn add(&mut self, item: String) -> Result<usize, String> {
        if self.items.len() >= self.capacity {
            Err(String::from("Inventaire plein"))
        } else {
            self.items.push(item);
            Ok(self.items.len())
        }
    }

    fn remove_last(&mut self) -> Option<String> {
        self.items.pop()
    }

    fn display(&self) {
        println!("Inventaire :");

        for item in &self.items {
            println!("- {item}");
        }
    }
}

fn main() {
    let mut inventory = Inventory::new(2);

    for item in ["Potion", "Clé", "Carte"] {
        match inventory.add(String::from(item)) {
            Ok(count) => println!("Objet ajouté, total : {count}"),
            Err(error) => println!("Ajout refusé : {error}"),
        }
    }

    inventory.display();

    if let Some(item) = inventory.remove_last() {
        println!("Objet retiré : {item}");
    }
}
```

</details>

<a id="structured-project"></a>
## Projet de synthèse — Personnage et partie

Construis un petit modèle de jeu réunissant toutes les notions du groupe.

Le programme doit contenir :

- une struct `Player` avec un nom, des points de vie, un score et un `Vec<String>` ;
- un enum `GameState` avec `Menu`, `Playing`, `Paused` et `GameOver(u32)` ;
- un constructeur et des méthodes pour les dégâts, le score et l'inventaire ;
- une méthode d'ajout d'objet qui retourne un `Result` et limite l'inventaire à trois objets ;
- une méthode de retrait qui retourne une `Option` ;
- une fonction qui affiche chaque état avec `match` ;
- un scénario complet dans `main` passant par au moins trois états.

<details>
<summary>Correction</summary>

```rust
struct Player {
    name: String,
    health: u32,
    score: u32,
    inventory: Vec<String>,
}

enum GameState {
    Menu,
    Playing,
    Paused,
    GameOver(u32),
}

impl Player {
    fn new(name: String) -> Self {
        Self {
            name,
            health: 100,
            score: 0,
            inventory: Vec::new(),
        }
    }

    fn take_damage(&mut self, amount: u32) {
        if amount >= self.health {
            self.health = 0;
        } else {
            self.health -= amount;
        }
    }

    fn add_score(&mut self, points: u32) {
        self.score += points;
    }

    fn add_item(&mut self, item: String) -> Result<usize, String> {
        if self.inventory.len() >= 3 {
            Err(String::from("Inventaire plein"))
        } else {
            self.inventory.push(item);
            Ok(self.inventory.len())
        }
    }

    fn remove_last_item(&mut self) -> Option<String> {
        self.inventory.pop()
    }

    fn display(&self) {
        println!("{} : {} PV, score {}", self.name, self.health, self.score);

        for item in &self.inventory {
            println!("- {item}");
        }
    }
}

fn display_state(state: GameState) {
    match state {
        GameState::Menu => println!("État : menu"),
        GameState::Playing => println!("État : partie en cours"),
        GameState::Paused => println!("État : pause"),
        GameState::GameOver(score) => println!("État : fin, score {score}"),
    }
}

fn main() {
    display_state(GameState::Menu);

    let mut player = Player::new(String::from("Ferris"));
    display_state(GameState::Playing);

    for item in ["Potion", "Clé", "Carte", "Corde"] {
        match player.add_item(String::from(item)) {
            Ok(count) => println!("{item} ajouté, {count} objet(s)"),
            Err(error) => println!("Impossible d'ajouter {item} : {error}"),
        }
    }

    player.add_score(150);
    player.take_damage(40);
    display_state(GameState::Paused);

    if let Some(item) = player.remove_last_item() {
        println!("Objet utilisé : {item}");
    }

    player.take_damage(60);
    player.display();
    display_state(GameState::GameOver(player.score));
}
```

</details>
