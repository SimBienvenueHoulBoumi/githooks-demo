# githooks-demo

Projet de démonstration de [githooks](https://github.com/SimBienvenueHoulBoumi/githooks), configuré **uniquement avec les modèles publiés** (`templates/project/`) :

| Fichier | Rôle |
|---|---|
| `lefthook.yml` | hooks locaux : règles githooks à version figée |
| `.github/workflows/githooks.yml` | CI : action `SimBienvenueHoulBoumi/githooks@v1`, mode strict |
| `.githooks.conf` | réglages partagés (exemples commentés) |

## Technologies prises en charge par githooks

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

Détails (formateurs, commandes de test) : [githooks — Langages et types de projets](https://github.com/SimBienvenueHoulBoumi/githooks#langages-et-types-de-projets).

## Protection

`main` est protégée : merge uniquement par PR, check `githooks` obligatoire.

Les PR de démonstration montrent ce qui passe et ce qui est bloqué :

- [#1 — conforme](https://github.com/SimBienvenueHoulBoumi/githooks-demo/pull/1) : faite avec les hooks, mergée ;
- [#2 — non conforme](https://github.com/SimBienvenueHoulBoumi/githooks-demo/pull/2) : faite sans les hooks, bloquée par la CI (message, branche, formatage).

Les branches mergées sont supprimées automatiquement (serveur et postes).
