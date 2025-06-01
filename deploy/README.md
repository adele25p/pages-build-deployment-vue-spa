# GitHub Action: Deploy Vue SPA to GitHub Pages

This action deploys a Vue Single Page Application (SPA) to GitHub Pages.

## Inputs
`build-directory` *(optional)*: Directory containing the built files (default: `dist`)

## Outputs
`page_url`: The URL of the deployed page

## Example Usage
``` yaml
- name: Deploy
  uses: adele25p/pages-build-deployment-vue-spa/deploy@v1
  with:
    build-directory: 'dist'
```

## How it works
1. Checks the build directory
2. Deploys the content to GitHub Pages using the official action
