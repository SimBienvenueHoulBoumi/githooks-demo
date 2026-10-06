# githooks-demo

Projet de démonstration de [githooks](https://github.com/SimBienvenueHoulBoumi/githooks), configuré **uniquement avec les modèles publiés** (`templates/project/`) :

| Fichier | Rôle |
|---|---|
| `lefthook.yml` | hooks locaux : règles githooks à version figée |
| `.github/workflows/githooks.yml` | CI : action `SimBienvenueHoulBoumi/githooks@v1`, mode strict |
| `.githooks.conf` | réglages partagés (exemples commentés) |

`main` est protégée : merge uniquement par PR, check `githooks` obligatoire.

Les PR de démonstration montrent ce qui passe et ce qui est bloqué.
