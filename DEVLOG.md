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
