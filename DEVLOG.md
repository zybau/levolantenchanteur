# Devlog — Le Volant Enchanteur

## 2026-06-21

### Initialisation du projet
- `npm init` — création du `package.json`
- Installation de TypeScript en `devDependency`
- Configuration du `tsconfig.json` en mode strict (`strict: true`, `rootDir: ./src`, `outDir: ./dist`)
- Création de `src/index.ts` — premier fichier TypeScript
- Installation de `tsx` pour exécuter TypeScript directement en dev sans compiler

### Scripts npm
| Script | Commande | Usage |
|---|---|---|
| `npm run dev` | `tsx src/index.ts` | Développement rapide |
| `npm run build` | `tsc` | Compilation production |
| `npm start` | `node dist/index.js` | Exécution production |

### Points clés appris
- Différence `devDependencies` vs `dependencies`
- SemVer : `MAJEUR.MINEUR.PATCH`
- `tsx` vs `ts-node` vs `tsc + node`
- Politique d'exécution PowerShell sur Windows (`RemoteSigned`)

## 2026-06-22

### Palier 2 — Premier serveur Express minimal

- Installation de `express` et `@types/express`
- Remplacement du `console.log` initial par un serveur Express écoutant sur le port 3000
- Validation : `npm run dev` affiche `Serveur démarré sur http://localhost:3000`

### Points clés appris
- HTTP : protocole requête/réponse entre client (navigateur) et serveur
- Méthodes HTTP : GET (lire), POST (créer), PUT (modifier), DELETE (supprimer)
- Codes de statut : 200 OK, 404 Not Found, 500 Internal Server Error
- Différence site classique (HTML généré côté serveur) vs API (données JSON)
- Express reçoit les requêtes HTTP, lit l'URL, exécute le bon code, renvoie une réponse
- `@types/xxx` : paquets de types TypeScript séparés pour les libs écrites en JS pur

## 2026-06-22 (suite)

### Palier 3 — Première route API avec données en dur

- Ajout de la route `GET /api/health` dans `src/index.ts`
- Validation : `http://localhost:3000/api/health` répond `200 OK` avec `{ "status": "ok" }`

### Points clés appris
- Une route Express associe une méthode HTTP + une URL à une fonction qui renvoie une réponse
- `res.json()` sérialise un objet JS en JSON et positionne automatiquement le bon header `Content-Type`
- Toutes les routes sont définies avant `app.listen()` — on configure le serveur avant de le démarrer

## 2026-06-22 (suite)

### Palier 4 — Organisation en couches (routes / services)

- Création de `src/app.ts` — configuration Express (routes, middlewares)
- Création de `src/routes/health.ts` — route `GET /health` isolée dans son fichier
- `src/index.ts` réduit au strict minimum : importe `app` et démarre le serveur
- Validation : `http://localhost:3000/api/health` répond toujours `{ "status": "ok" }`

### Points clés appris
- `Router` Express : mini-instance Express pour regrouper des routes liées — analogie C# : Controller avec RoutePrefix
- `app.use('/api', healthRouter)` : branche le router et préfixe toutes ses routes par `/api`
- Séparation des responsabilités : `index.ts` (démarrage) / `app.ts` (configuration) / `routes/` (endpoints)

## 2026-06-22 (suite)

### Palier 5 — Docker et PostgreSQL

- Installation de Docker Desktop (avec mise à jour de WSL 2)
- Création de `docker-compose.yml` décrivant un conteneur PostgreSQL 16
- Validation : `docker compose up -d` démarre le conteneur, `docker compose ps` confirme le statut `running` sur le port 5432

### Points clés appris
- Docker : outil d'isolation par conteneurs — embarque runtime + librairies + config dans un bloc autonome
- Image vs conteneur : image = modèle (classe), conteneur = instance en cours d'exécution
- Volume Docker : stockage persistant séparé du conteneur — les données survivent aux redémarrages
- `docker compose up -d` : démarre en arrière-plan ("detached") ; `docker compose down` : arrête et nettoie
- Sur Windows, Docker s'appuie sur WSL 2 pour accéder au noyau Linux nécessaire à l'isolation des conteneurs
