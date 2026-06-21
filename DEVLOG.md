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
