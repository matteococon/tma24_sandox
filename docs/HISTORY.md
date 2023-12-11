# History

Here the list of instructions to create the project from scratch.

## Requirements

- macOS >= 13.6.2 (Ventura)
- Brew (install instructions: <https://brew.sh/>, then `brew update`
- Instruction from scratch (this file)
- The ".apk" of the Subject Under Test (sut) file `sut-app-debug.apk`

## Step #0 (optional) - Terminal Setup & VSCodium Project Setup

### Terminal Setup

Install Iterm2 as default terminal app:

```sh
brew install iterm2
```

Run Iterm2 (is in the Application folder) and open a new termial window.
Now install zsh (`ohmyzsh`) with this command:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Then install `powerlevel10k` theme for zsh:

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Open `~/.zshrc` and set the theme as following:

```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Now exit from Iterm2 to save the setup and open Iterm2 again.
Follow the setup on screen with your favourite setup.

### VSCodium Project Setup

Install VSCodium (`vscodium` is an alternative version on VSCode - here more info: <https://vscodium.com/>) with:

`brew install --cask vscodium`

Open VSCodium and choose an new empty folder that will be the root of the project.

Create a `./.vscode/` folder in the root of the project.

Create a `./.vscode/extensions.json` file with:

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

Create a `./.vscode/settings.json` file with:

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

- Codium Menu "Run" >
- "Add Configurations .." >
- "Web App (Chrome)"
- Note: This will create a launch.json file in your .vscode directory.

Save the workspace with:

- VSCode/Codium Menu "File" >
- "Save Workspace As.."
- Save the workspace as `./.vscode/workspace.code-workspace` folder

Close VSCode/Codium and open the Workspace file.

## Step #1 - gitignore Project Setup

Create a new `./.gitignore/` file merging in it the following gitignore files:

- Node: <https://github.com/github/gitignore/blob/main/Node.gitignore>
- JetBrains IDE <https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore>,
- Swift <https://github.com/github/gitignore/blob/main/Swift.gitignore>,
- Android <https://github.com/github/gitignore/blob/main/Android.gitignore>

Append at the bottom of `./.gitignore/` the following:

```sh
.DS_Store
```

Remove in `./.gitignore/` the `.vscode` row.

## Step #2 - Node Project Setup

Install latest stable node version running in the terminal in the root of the project
the following commands:

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

## Step #3 (optional) - Linting/Spell Project Setup

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

## Step #4 - Create a `Node.js` project

Adding the following `package.json`:

```json
{
  "name": "tma_current",
  "type": "module",
  "devDependencies": {
    "@wdio/appium-service": "^8.24.12",
    "@wdio/cli": "^8.24.16",
    "@wdio/local-runner": "^8.24.12",
    "@wdio/mocha-framework": "^8.24.12",
    "@wdio/spec-reporter": "^8.24.12",
    "appium-uiautomator2-driver": "^2.34.2",
    "ts-node": "^10.9.1",
    "typescript": "^5.0.4"
  },
  "scripts": {
    "wdio": "wdio run ./wdio.conf.ts"
  }
}
```

## Step #5 - Install Node packages

Run in the root of the folder:

```sh
npm install
```
