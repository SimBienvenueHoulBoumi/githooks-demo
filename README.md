# repogarde-demo

Projet de démonstration de [repogarde](https://github.com/SimBienvenueHoulBoumi/repogarde), configuré **uniquement avec les modèles publiés** (`templates/project/`) :

| Fichier | Rôle |
|---|---|
| `lefthook.yml` | hooks locaux : règles repogarde à version figée |
| `.github/workflows/repogarde.yml` | CI : action `SimBienvenueHoulBoumi/repogarde@v1`, mode strict |
| `.repogarde.conf` | réglages partagés (exemples commentés) |

## Technologies prises en charge par repogarde

Ce projet est en Python, mais la même configuration fonctionne pour :

| Domaine | Technologies |
|---|---|
| **Java / JVM** | Maven, Gradle — Spring Boot, Quarkus, Android |
| **JavaScript / TypeScript** | npm, pnpm, yarn, bun, Deno — React, Next.js, Vue, Angular, Nest |
| **Python** | pip, uv, poetry, pipenv — Django, FastAPI, Flask |
| **Autres langages** | Go · Rust · PHP (Laravel, Symfony) · Ruby (Rails) · .NET · Dart / Flutter · Swift · Elixir · C / C++ · Shell |
| **Infrastructure** | Terraform / OpenTofu · Packer · Ansible · Helm · Kubernetes · Docker · GitHub Actions |
| **Hébergement / CI** | GitHub, GitLab, Bitbucket · GitHub Actions, GitLab CI |
| **Systèmes** | Linux, macOS, Windows |

Détails (formateurs, commandes de test) : [repogarde — Technologies](https://simbienvenuehoulboumi.github.io/repogarde/technologies/).

## Protection

`main` est protégée : merge uniquement par PR, check `repogarde` obligatoire.

Les PR de démonstration montrent ce qui passe et ce qui est bloqué :

- [#1 — conforme](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/1) : faite avec les hooks, mergée ;
- [#2 — non conforme](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/2) : faite sans les hooks, bloquée par la CI (message, branche, formatage).

Les branches mergées sont supprimées automatiquement (serveur et postes).
