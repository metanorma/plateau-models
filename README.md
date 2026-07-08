# PLATEAU Model

This repository contains the PLATEAU v5.1 UML model and generates a browser-based visualization using LutaML.

The site can be accessed at:
* [Project PLATEAU UML models site](https://metanorma.github.io/plateau-model)

## Prerequisites

- Ruby 3.2 or later
- Bundler

## Setup

1. Install Bundler (if not already installed):
   ```bash
   gem install bundler
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

## Generate the Web Page

To generate the `index.html` file from the QEA model:

```bash
bundle install
bundle exec ea spa 20251010_current_plateau_v5.1.qea -o index.html
```

This will create a single-page application (SPA) that can be opened in any web browser to visualize the UML model.

## GitHub Pages Deployment

The repository is configured to automatically deploy the generated page to GitHub Pages via GitHub Actions:

- The workflow is triggered on pushes to the `main` branch
- It can also be manually triggered via the Actions tab
- The generated page will be available at the GitHub Pages URL for this repository

### Manual Workflow Trigger

You can manually trigger the deployment workflow:
1. Go to the "Actions" tab in the GitHub repository
2. Select the "Deploy to GitHub Pages" workflow
3. Click "Run workflow" and select the branch

## Files

- `20251010_current_plateau_v5.1.qea` - The source UML model file in Enterprise Architect format
- `Gemfile` - Ruby dependencies specification
- `browser.html` - Generated visualization (created by the build process)
- `.github/workflows/deploy-pages.yml` - GitHub Actions workflow for automated deployment
