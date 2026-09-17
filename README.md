# Notes Rust

Ce dossier contient les notions de Rust déjà étudiées. Chaque notion possède son propre fichier afin de pouvoir la retrouver rapidement et ajouter de nouvelles leçons sans agrandir un seul document.

## Leçons

- [Bases](Bases/README.md) : syntaxe essentielle pour écrire et exécuter de petits programmes.
- [Ownership](Ownership/README.md) : propriété, emprunts, références et slices.
- [Types structurés](Structured-Types/README.md) : structs, méthodes, enums, valeurs optionnelles, erreurs et vectors.
- [Exercices](Exercises/README.md) : exercices cumulatifs et corrections associés aux leçons.
- [Découvertes](Discoveries/README.md) : explications tirées des erreurs, avertissements et questions rencontrés en pratiquant.

## Progression vers Bevy

- [x] Syntaxe de base.
- [x] Ownership, emprunts et références.
- [ ] Structs, méthodes, enums, `Option`, `Result` et `Vec` — groupe actuel.
- [ ] Traits, génériques et attributs `derive`.
- [ ] Organisation en modules et utilisation de base des itérateurs.
- [ ] Premier projet Bevy.

Les bases générales de Rust sont terminées. Les trois étapes encore ouvertes correspondent à la préparation minimale pour lire les signatures et exemples courants de Bevy ; elles ne représentent pas l'ensemble du langage Rust.

## Organisation

```text
Rust docs/
├── README.md
├── Bases/
│   ├── README.md
│   ├── 01-Cargo.md
│   ├── 02-Variables.md
│   ├── 03-Printing.md
│   ├── 04-Constants.md
│   ├── 05-Functions.md
│   ├── 06-Loops.md
│   ├── 07-Types.md
│   ├── 08-Conditions.md
│   ├── 09-Arrays.md
│   ├── 10-Operators.md
│   ├── 11-Tuples.md
│   └── 12-Match.md
├── Ownership/
│   ├── README.md
│   ├── 01-Ownership.md
│   ├── 02-Move-Copy-Clone.md
│   ├── 03-Borrowing.md
│   ├── 04-Mutable-References.md
│   ├── 05-String-and-Str.md
│   └── 06-Slices.md
├── Structured-Types/
│   ├── README.md
│   ├── 01-Structs.md
│   ├── 02-Methods.md
│   ├── 03-Enums.md
│   ├── 04-Option.md
│   ├── 05-Result.md
│   └── 06-Vectors.md
├── Exercises/
│   ├── README.md
│   ├── Bases.md
│   ├── Ownership.md
│   └── Structured-Types.md
└── Discoveries/
    ├── README.md
    ├── 01-Clippy.md
    └── 02-Loop-Values-and-Indexes.md
```

Chaque nouveau grand thème peut avoir son propre dossier afin de conserver une progression claire.
