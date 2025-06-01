# 📦 pages-build-deployment-vue-spa

This repository provides two GitHub Actions to automate building and deploying a Vue Single Page Application (SPA) to GitHub Pages.

## Available Actions
**./build**: Builds the Vue SPA.  
**./deploy**: Deploys the built files to GitHub Pages.

## Quick Usage
Add this workflow to `.github/workflows/deploy.yml` :
``` yaml
# This is a GitHub Actions workflow file for building and deploying a Vue SPA to GitHub Pages.
# It uses the adele25p/pages-build-deployment-vue-spa action to build the Vue SPA and deploy it to GitHub Pages.

name: 'Build and Deploy Vue SPA to GitHub Pages'
description: 'Builds and deploys a Vue Single Page Application (SPA) to GitHub Pages'

# On
# The workflow is triggered on push events to the main branch.
on :
  push:
    branches:
      - main

# Permissions
# The action requires permissions to read the contents of the repository and write to the pages.
permissions:
  contents: read
  pages: write
  id-token: write

# Jobs
# The workflow consists of two jobs: build and deploy.
jobs:
  build:                           # Build the Vue SPA
    runs-on: ubuntu-latest
    steps:
      - name: Build
        uses: adele25p/pages-build-deployment-vue-spa/build@v1

  deploy:                          # Deploy the built Vue SPA to GitHub Pages
    runs-on: ubuntu-latest
    needs: build

    # The deployment is done to the GitHub Pages environment.
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    steps:
      - name: Deploy
        id: deployment
        uses: adele25p/pages-build-deployment-vue-spa/deploy@v1
```

## Requirements
Make sure the following conditions are met before using the workflow:
- [x] Your Vue Project is set up to build as a Single Page Application (SPA).  
- [x] You have a valid `vue.config.js` file in your project root, configured for SPA mode.
- [x] Your repository is configured to use GitHub Pages.
- [x] The `vue.config.js` file should not include any configurations that conflict with SPA routing, such as `history` mode in Vue Router without proper fallback.

## Customizing the Workflow
You can customize the build and deploy actions by passing inputs in the workflow file.  
This allows you to adapt the workflow to different tools such as **Vite**, **Vue CLI**, **Webpack**, **Nuxt (SPA) ...**

## Action Details
See `build/README.md` for build action documentation.  
See `deploy/README.md` for deploy action documentation.

## Useful Links
| Resource | Description |
| -------- | ----------- |
| [GitHub Actions Documentation](https://docs.github.com/en/actions) | Learn how GitHub Actions work and how to customise workflows. |
| [GitHub Pages Documentation](https://docs.github.com/en/pages) | Understand how to configure and use GitHub Pages. |
| [Vue.js Deployment Guide](https://vuejs.org/guide/best-practices/production-deployment.html) | Official Vue documentation on deploying applications. |
| [Vite Deployment Guide](https://vitejs.dev/guide/static-deploy.html) | Instructions for deploying Vite apps to static hosts. |
