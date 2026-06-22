# Le Volant Enchanteur — Site du club de badminton

## Contexte du projet

Site web sur mesure pour le club de badminton "Le Volant Enchanteur", développé
en remplacement d'un site Blogger vieillissant. Objectif double :
1. Avoir un site complet et moderne pour le club.
2. Servir de projet d'apprentissage pour une stack JS/TS backend, en
   progressant sur l'usage de Claude Code.

## Profil du développeur

- Développeur intermédiaire en C# (WPF/MVVM, architecture en couches :
  ViewModels, Services, Repositories, Strategy pattern).
- **Débutant total en JS/TS backend.** Ne pas supposer de connaissances
  Node/Express/Prisma acquises — expliquer les concepts au fur et à mesure.
- Pas d'expérience SQL ni Entity Framework en C#. La référence BDD connue est
  **MongoDB** (documents JSON, collections, `collection.find()`, etc.) — utiliser
  MongoDB comme point de comparaison pour expliquer PostgreSQL et Prisma, pas EF Core.
- A déjà utilisé des classes DTO en C# pour sérialiser/désérialiser des données —
  peut s'appuyer sur ce concept pour expliquer les types retournés par Prisma et la
  forme des objets JSON dans les réponses API.
- À l'aise avec Git au quotidien.

## Stack technique retenue

| Couche | Choix |
|---|---|
| Runtime | Node.js |
| Langage | TypeScript |
| Framework backend | Express |
| Base de données | PostgreSQL (via Docker en local) |
| ORM | Prisma |
| Frontend V1 | HTML/CSS/JS vanilla (React envisagé en V2) |
| Gestionnaire de paquets | npm |
| Versioning | Git + dépôt GitHub |

## Méthode de travail — IMPORTANT

**Isolation maximale des tâches.** Le développement avance par petits paliers
isolés et vérifiables, jamais par gros blocs combinés. Chaque palier doit :
- Toucher une seule préoccupation à la fois (ex: ne pas mélanger mise en place
  de TypeScript ET création des routes Express dans la même étape).
- Avoir un critère de validation explicite et testable avant de passer à la
  suite (ex: "la commande X retourne Y", "la route /api/health répond 200").
- Être expliqué (le "pourquoi", pas seulement le "quoi") avant d'être exécuté.

Ne jamais enchaîner plusieurs paliers sans confirmation que le précédent
fonctionne. En cas de doute sur la granularité d'une tâche, préférer la
découper davantage plutôt que de la regrouper.

## Phasage du projet

- **Phase 1 (en cours)** : API Express + TypeScript minimale, sans base de
  données — données en dur dans le code. Objectif : isoler l'apprentissage
  de Node/Express/TS de celui de PostgreSQL/Prisma/Docker.
- **Phase 2** : Introduction de Docker, PostgreSQL, Prisma — remplacement des
  données en dur par de vraies requêtes en base.
- **Phase 3** : Frontend vanilla HTML/CSS/JS consommant l'API.
- **V2 (plus tard)** : Migration éventuelle du frontend vers React.

## Conventions Git

À chaque commit, mettre à jour `DEVLOG.md` avec :
- La date
- Ce qui a été fait
- Les points clés appris ou décisions prises

## Conventions de code

- TypeScript strict activé.
- Code et noms de variables en anglais ; contenu/textes destinés aux
  utilisateurs du site en français.
- Structure en couches inspirée de l'expérience C# du développeur : séparer
  routes / services / accès aux données dès que la complexité le justifie
  (pas nécessaire dès la Phase 1 avec données en dur).

## État actuel du projet

_(À mettre à jour au fil de l'avancement.)_

- [ ] Palier 1 — Initialisation du projet Node + TypeScript
- [ ] Palier 2 — Premier serveur Express minimal ("Hello World")
- [ ] Palier 3 — Première route API avec données en dur
- [ ] Palier 4 — Organisation en couches (routes/services)
- [ ] Dépôt GitHub initialisé et premier commit poussé
