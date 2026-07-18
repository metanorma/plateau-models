# PLATEAU Model

This repository hosts the PLATEAU 3D City Model UML specifications and publishes an interactive browser-based visualization for each, built with [LutaML](https://lutaml.com) and the [`ea`](https://github.com/lutaml/ea) gem.

Live site: <https://metanorma.github.io/plateau-model>

The site offers **two side-by-side UML model specifications**, bilingual (Japanese / English):

| Directory | Specification | Status | Source |
| --- | --- | --- | --- |
| `/citygml-2/` | PLATEAU v5.1 (CityGML 2.0) | Production | `20251010_current_plateau_v5.1.qea` |
| `/citygml-3/` | PLATEAU CityGML 3.0 Consolidated Draft | Draft | `20260323_CityGML_3.0_Consolidated_Draft.qea` |

The root `index.html` is a hand-authored landing page (committed); each subdirectory contains a generated SPA.

## Prerequisites

- Ruby 3.2 or later
- Bundler

## Setup

```bash
gem install bundler     # if not already installed
bundle install
```

## Generate the SPAs locally

Each QEA file produces a self-contained HTML SPA into its own subdirectory:

```bash
# CityGML 2.0 — PLATEAU v5.1 (current production model)
mkdir -p citygml-2
bundle exec ea spa 20251010_current_plateau_v5.1.qea -o citygml-2/index.html

# CityGML 3.0 — Consolidated Draft (next-generation model)
mkdir -p citygml-3
bundle exec ea spa 20260323_CityGML_3.0_Consolidated_Draft.qea -o citygml-3/index.html
```

Open `index.html` (the landing page) in any browser to choose a model.

## GitHub Pages deployment

The repository auto-deploys to GitHub Pages via `.github/workflows/deploy-pages.yml`:

- Triggered on push to `main` (and the `migrate/new-lutaml-spa` branch during the migration window).
- The workflow regenerates both SPAs from their QEA sources and uploads the entire repository (landing page + SPA subdirectories) as the Pages artifact.
- Can also be run manually via the Actions tab.

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | Hand-authored bilingual landing page (committed) |
| `20251010_current_plateau_v5.1.qea` | CityGML 2.0 source UML model (Enterprise Architect) |
| `20260323_CityGML_3.0_Consolidated_Draft.qea` | CityGML 3.0 source UML model (Enterprise Architect) |
| `citygml-2/index.html` | Generated CityGML 2.0 SPA (gitignored) |
| `citygml-3/index.html` | Generated CityGML 3.0 SPA (gitignored) |
| `Gemfile` | Ruby dependencies (`ea`, `lutaml-uml`) |
| `.github/workflows/deploy-pages.yml` | GitHub Actions workflow |
