# GitHub Action: Build Vue SPA

This action builds a Vue Single Page Application (SPA).

## Inputs
`node-version` *(optional)*: Node.js version to use (default: `20`)  
`working-directory` *(optional)*: Project directory (default: `.`)  
`build-directory` *(optional)*: Output directory for build artifacts (default: `dist`)  
`build-command` *(optional)*: Build command to run (default: `npm run build`)

## Example Usage
``` yaml
- name: Build
  uses: adele25p/pages-build-deployment-vue-spa/build@v1
  with:
    node-version: '18'
    working-directory: '.'
    build-directory: 'dist'
    build-command: 'npm run build'
```

## How it works
1. Checks the working directory
2. Installs Node.js and dependencies using the official actions
3. Runs the build command
4. Uploads the build artifacts to GitHub Pages using the official action
