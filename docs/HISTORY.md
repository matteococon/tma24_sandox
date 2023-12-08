# History

Here the list of instructions to create the project from scratch.

## Requirements

- macOS >= 13.6.2 (Ventura)
- Brew <https://brew.sh/>
- a new empty folder

## VSCode/Codium Project Setup: `.vscode`

Install VSCodium <https://vscodium.com/> with:

`brew install --cask vscodium`

Open VSCodium and choose an empty folder.

Create a `.vscode` folder in the root.

Create a `.vscode/extensions.json` file with:

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "dsznajder.es7-react-js-snippets",
    "dbaeumer.vscode-eslint",
    "yoavbls.pretty-ts-errors",
    "jgclark.vscode-todo-highlight",
    "eamodio.gitlens",
    "trunk.io",
    "bierner.markdown-preview-github-styles",
    "aaron-bond.better-comments"
  ]
}
```

Create a `.vscode/settings.json` file with:

```json
{
  "javascript.inlayHints.enumMemberValues.enabled": true,
  "javascript.inlayHints.functionLikeReturnTypes.enabled": true,
  "javascript.inlayHints.parameterTypes.enabled": true,
  "javascript.inlayHints.propertyDeclarationTypes.enabled": true,
  "javascript.inlayHints.variableTypes.enabled": true,
  "typescript.inlayHints.enumMemberValues.enabled": true,
  "typescript.inlayHints.functionLikeReturnTypes.enabled": true,
  "typescript.inlayHints.parameterTypes.enabled": true,
  "typescript.inlayHints.propertyDeclarationTypes.enabled": true,
  "typescript.inlayHints.variableTypes.enabled": true,
  "editor.stickyScroll.enabled": true,
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "rvest.vs-code-prettier-eslint",
  "[markdown]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

Create a new configuration for Debugging React Apps with:

- VSCode/Codium Menu "Run" >
- "Add Configurations .." >
- "Web App (Chrome)"
- Note: This will create a launch.json file in your .vscode directory.

Save the workspace with:

- VSCode/Codium Menu "File" >
- "Save Workspace As.."
- Save inside `.vscode` folder

Close VSCode/Codium and opent the Workspace file.

## Project Setup: `.gitignore`

Create a gitignore for Node, JetBrains IDE, iOS, Android, React-Native.

Add in it the `.DS_Store` specification.

Remove `.vscode` specification.

> Note: here more info: <https://github.com/github/gitignore>

## Node Project Setup

```sh
brew install asdf
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
asdf list all nodejs
# pick the latest LTS/Stable version, e.g.:
asdf install nodejs 20.10.0
# this specify the version in the root of the current project
asdf local nodejs 20.10.0
# make this version as default for your current user:
cd ~/; asdf local nodejs 20.10.0

# check if works
node --version
npm --version
```

## Linting/Spell Project Setup

```sh
# <https://docs.trunk.io/check/cli>
trunk --version
# trunk init
trunk check enable codespell cspell gitleaks # generic, secrets, etc
trunk check enable shellcheck # bash
trunk check enable stylelint # css, scss
trunk check enable actionlint # github [Actions]
trunk check enable eslint # js
trunk check enable markdownlint # markdown
trunk check enable sort-package-json # package json
trunk check enable trivy tfsec osv-scanner # security
trunk check enable svgo # svg
trunk check enable swiftlint google-java-format ktlint # swift java kotlin
trunk check enable prettier # many format, YAML
# more linters here: <https://docs.trunk.io/check>
```
