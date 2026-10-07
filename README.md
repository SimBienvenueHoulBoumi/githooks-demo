# repogarde-demo

🇫🇷 Français · [🇬🇧 English](README.en.md)

Projet de démonstration de [repogarde](https://github.com/SimBienvenueHoulBoumi/repogarde) : une petite application Python dont tout le cycle de vie (commits, branches, formatage, tests, code mort, releases) est encadré par repogarde, configuré **uniquement avec les modèles publiés** (`templates/project/`).

## Le projet

`calc` est une bibliothèque Python minimale, volontairement simple pour que l'attention reste sur l'outillage :

```text
src/calc/__init__.py    add(a, b) et mul(a, b)
tests/test_calc.py      tests pytest
pyproject.toml          projet Python (version tenue à jour par les releases)
CHANGELOG.md            généré à chaque release
```

```bash
pip install pytest && pytest -q     # lancer les tests (pythonpath réglé dans pyproject.toml)
```

Les versions sont publiées automatiquement : [releases](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/releases).

## Configuration repogarde

| Fichier | Rôle |
|---|---|
| `lefthook.yml` | hooks locaux : règles repogarde à version figée |
| `.github/workflows/repogarde.yml` | CI : action `SimBienvenueHoulBoumi/repogarde@v2`, mode strict : messages, branche, secrets, formatage (ruff), tests (pytest), nouveau code mort (ruff, vulture) |
| `.github/workflows/release.yml` | releases automatiques : version calculée depuis les commits, PR de release validée par la CI puis mergée, tag et release |
| `.repogarde.conf` | réglages partagés : langue des messages de la CI (`lang = fr`), exemples commentés |

## Essayer

```bash
git clone https://github.com/SimBienvenueHoulBoumi/repogarde-demo && cd repogarde-demo
lefthook install          # hooks du projet (ou ./install.sh --global de repogarde : délégation automatique)
git switch -c feat/division
# … modifier src/calc/__init__.py, puis :
git add . && git cc                # assistant de commit (installé par repogarde/install.sh)
# ou : git commit -am "division" → préfixé en « feat(division): division », code formaté par ruff
git push -u origin feat/division   # tests (pytest) avant l'envoi
```

Sans les hooks, la CI refait les mêmes vérifications et bloque la PR.

## Technologies prises en charge par repogarde

Ce projet est en Python, mais la même configuration fonctionne pour :

| Domaine | Technologies |
|---|---|
| **Java / JVM** | Maven, Gradle — Spring Boot, Quarkus, Android |
| **JavaScript / TypeScript** | npm, pnpm, yarn, bun, Deno — React, Next.js, Vue, Angular, Nest |
| **Python** | pip, uv, poetry, pipenv — Django, FastAPI, Flask |
| **Autres langages** | Go · Rust · PHP (Laravel, Symfony) · Ruby (Rails) · .NET · Dart / Flutter · Swift · Elixir · C / C++ · Shell |
| **Infrastructure** | Terraform / OpenTofu · Packer · Ansible · Helm · Kubernetes · Docker · GitHub Actions |
| **Hébergement / CI** | Hooks : tout dépôt Git · CI : GitHub Actions, GitLab CI |
| **Systèmes** | Linux, macOS, Windows |

Détails (formateurs, commandes de test) : [repogarde — Technologies](https://simbienvenuehoulboumi.github.io/repogarde/technologies/).

## Protection

`main` est protégée : merge uniquement par PR, check `repogarde` obligatoire.

Les PR de démonstration montrent ce qui passe et ce qui est bloqué :

- [#1 — conforme](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/1) : faite avec les hooks, mergée ;
- [#2 — non conforme](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/2) : faite sans les hooks, bloquée par la CI (message, branche, formatage), puis fermée ; le log du blocage reste consultable.

Les branches mergées sont supprimées automatiquement (serveur et postes).
