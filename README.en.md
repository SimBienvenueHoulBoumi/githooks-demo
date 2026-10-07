# repogarde-demo

[🇫🇷 Français](README.md) · 🇬🇧 English

Demo project for [repogarde](https://github.com/SimBienvenueHoulBoumi/repogarde): a small Python application whose whole lifecycle (commits, branches, formatting, tests, dead code, releases) is guarded by repogarde, configured **only with the published templates** (`templates/project/`).

## The project

`calc` is a minimal Python library, deliberately simple so that the focus stays on the tooling:

```text
src/calc/__init__.py    add(a, b) and mul(a, b)
tests/test_calc.py      pytest tests
pyproject.toml          Python project (version kept up to date by releases)
CHANGELOG.md            generated on each release
```

```bash
pip install pytest && pytest -q     # run the tests (pythonpath set in pyproject.toml)
```

Versions are published automatically: [releases](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/releases).

## repogarde configuration

| File | Role |
|---|---|
| `lefthook.yml` | local hooks: repogarde rules at a pinned version |
| `.github/workflows/repogarde.yml` | CI: `SimBienvenueHoulBoumi/repogarde@v2` action, strict mode: messages, branch, secrets, formatting (ruff), tests (pytest), new dead code (ruff, vulture) |
| `.github/workflows/release.yml` | automatic releases: version computed from the commits, release PR validated by the CI then merged, tag and release |
| `.repogarde.conf` | shared settings: CI message language (`lang = fr`), commented examples |

## Try it

```bash
git clone https://github.com/SimBienvenueHoulBoumi/repogarde-demo && cd repogarde-demo
lefthook install          # project hooks (or repogarde's ./install.sh --global: automatic delegation)
git switch -c feat/division
# … edit src/calc/__init__.py, then:
git add . && git cc                # commit assistant (installed by repogarde/install.sh)
# or: git commit -am "division" → prefixed as "feat(division): division", code formatted by ruff
git push -u origin feat/division   # tests (pytest) before sending
```

Without the hooks, the CI runs the same checks again and blocks the PR.

## Technologies supported by repogarde

This project is in Python, but the same configuration works for:

| Area | Technologies |
|---|---|
| **Java / JVM** | Maven, Gradle — Spring Boot, Quarkus, Android |
| **JavaScript / TypeScript** | npm, pnpm, yarn, bun, Deno — React, Next.js, Vue, Angular, Nest |
| **Python** | pip, uv, poetry, pipenv — Django, FastAPI, Flask |
| **Other languages** | Go · Rust · PHP (Laravel, Symfony) · Ruby (Rails) · .NET · Dart / Flutter · Swift · Elixir · C / C++ · Shell |
| **Infrastructure** | Terraform / OpenTofu · Packer · Ansible · Helm · Kubernetes · Docker · GitHub Actions |
| **Hosting / CI** | Hooks: any Git repository · CI: GitHub Actions, GitLab CI |
| **Systems** | Linux, macOS, Windows |

Details (formatters, test commands): [repogarde — Technologies](https://simbienvenuehoulboumi.github.io/repogarde/en/technologies/).

## Protection

`main` is protected: merge only through PRs, `repogarde` check required.

The demo PRs show what passes and what is blocked:

- [#1 — compliant](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/1): made with the hooks, merged;
- [#2 — non-compliant](https://github.com/SimBienvenueHoulBoumi/repogarde-demo/pull/2): made without the hooks, blocked by the CI (message, branch, formatting), then closed; the blocking log is still available.

Merged branches are deleted automatically (server and developer machines).
