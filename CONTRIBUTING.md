Thank you for considering contributing! It’s people like you who make this extension better for everyone. By contributing to this project, you agree to abide by our [code of conduct](CODE_OF_CONDUCT.md) and that your contributions will be licensed under the project's [license](LICENSE) (MIT).

## About the Extension

### Core Extension Files

- **[package.json](package.json)**: The manifest file that defines the extension's metadata, contributions (languages, grammars, commands, views), and scripts.
- **[src/](src/)**: Contains the TypeScript source code for the extension's logic, including command handling, providers, and tree views.
- **[command_output.txt](command_output.txt)**: The primary database of Geant4 commands and documentation used at runtime for autocomplete, hovers, and diagnostics.
- **[syntaxes/g4macro.tmLanguage.json](syntaxes/g4macro.tmLanguage.json)**: The TextMate grammar file that provides the logic for syntax highlighting.
- **[language-configuration.json](language-configuration.json)**: Configures language-specific features like comment toggling, bracket matching, and auto-indentation.
- **[images/](images/)**: Contains the extension icon and logos with both dark and light themes for sidebar view, as well as gifs for documentation.

### Documentation & Legal

- **[README.md](README.md)**: The main documentation providing installation, usage, and troubleshooting details.
- **[CHANGELOG.md](CHANGELOG.md)**: A detailed log of all notable changes and version history.
- **[LICENSE](LICENSE)**: The project's MIT license.
- **[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)**: Standards for behavior and enforcement within our community.
- **[.github/](.github/)**: Contains issue and pull request templates.

### Development & CI/CD

- **[.vscode/](.vscode/)**: Workspace-specific configurations including launch settings for the "Extension Development Host", recommended extensions, and common tasks.
- **[tsconfig.json](tsconfig.json)**, **[.eslintrc.js](.eslintrc.js)**, **[.prettierrc](.prettierrc)**: Configuration files for TypeScript, ESLint, and Prettier to ensure code quality and consistency.
- **[.vscodeignore](.vscodeignore)** & **[.gitignore](.gitignore)**: Lists of files to be excluded from the final VSIX bundle and Git tracking, respectively.
- **[.github/workflows/](.github/workflows/)**: GitHub Action workflows for automated publishing to Open VSX and other CI tasks.

## 🛠 Development Workflow

We follow a standard "Fork-and-Pull" workflow.

1. **Fork** the repository to your own GitHub account.
2. **Clone** your fork locally.
3. **Install** dependencies inside the working directory by running `npm i` (make sure that your computer has the required software installed, see [Prerequisites](#prerequisites)).
4. **Enable** "NPM Scripts" section in VS Code Explorer by clicking "..." in the Explorer view and selecting "NPM Scripts". Run "package" script to build the vsix file.
5. **Create a branch** for your feature or fix:
   ```bash
   git checkout -b feat/add-new-snippets
   # or
   git checkout -b fix/fix-typo
   git checkout -b docs/update-readme
   ```
6. **Make your changes** with the "watch" script running in the background. To add features such as IntelliSense, hovers and validators check out the VS Code extenders documentation at <https://code.visualstudio.com/docs>.
7. **Test your changes** locally using the "Extension Development Host" (<kbd>F5</kbd>), and then use <kbd>Ctrl+R</kbd> (or <kbd>Cmd+R</kbd> on Mac) to reload the testing window.
8. **Run** "package" script again to check what's included in the vsix file.
9. **Commit** your changes, which will trigger formatting and linting in the background.
10. **Push** your changes to your fork.
11. **Create a Pull Request** from your fork to the main repository.

### Prerequisites

To build this extension, you need [Node.js][] installed, which includes [npm][] and [npx][].

- **macOS**: `brew install node` (using [Homebrew][]) or use the official installer.
- **Linux**: `sudo apt install nodejs npm` ([Debian][] / [Ubuntu][]) or use [NodeSource][].
- **Windows**: `winget install OpenJS.NodeJS` or download from [Node.js][].

_Tip_: Use [nvm][] (macOS/Linux) or [nvm-windows][] to manage Node versions easily.

## Publishing the Extension (For Maintainers Only)

### Recommended Workflow

Press <kbd>Ctrl/CMD</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> in VS Code or one of its derivatives to run the extension publishing workflow in the following order:

1. **NPM: Increment Version** (This will bump the version in package.json and create an annotated git tag)
2. **NPM: GitHub Release** (This will trigger a [GitHub Action](#github-action) to publish the extension to the [Open VSX Registry][])
3. rerun the "package" script, and upload the VSIX package to the corresponding GitHub [Release][] as an [asset](#github-release-asset).

### GitHub Action

This repository is configured with a GitHub Action that automatically publishes to the [Open VSX Registry][] whenever a new version tag is pushed.

1.  **Run the version command**: Instead of manual editing, use `npm version` to bump the version and create an **annotated tag** automatically.

    | Command             | Action               | Example (1.0.1 →) | When to use                       |
    | :------------------ | :------------------- | :---------------- | :-------------------------------- |
    | `npm version patch` | Increments 3rd digit | **1.0.2**         | Bug fixes / minor tweaks          |
    | `npm version minor` | Increments 2nd digit | **1.1.0**         | New features (non-breaking)       |
    | `npm version major` | Increments 1st digit | **2.0.0**         | Breaking changes / major overhaul |

    ```bash
    # Example: bump patch and add a message
    npm version patch -m "Release version %s"
    ```

2.  **Push the changes and tags**: `git push origin HEAD --follow-tags`

    _Note: Ensure your working directory is clean before running `npm version`. This command will update [package.json](package.json), commit the change, and create an annotated tag for you._

### Manual Publishing

You can also publish manually from your terminal using the local version of [ovsx][]:

```bash
# Using the local project scripts
npm run deploy -- -p <YOUR_OVSX_TOKEN>
# Or using npx
npx ovsx publish -p <YOUR_OVSX_TOKEN>
```

### Managing `ovsx` Versions

This project pins a specific version of the [ovsx][] publisher in [package.json](package.json) to ensure consistent builds.

- **To try a different version (one-time):**
  ```bash
  npx ovsx@latest publish
  ```
- **To permanently update the version:**
  ```bash
  npm install ovsx@latest --save-dev
  ```

### GitHub Release Asset

To build the [VSIX][] package locally, run the "package" script. This will create a `.vsix` file in the root directory, which can be uploaded as a GitHub [Release][] Asset for the original VS Code users to download and install manually.

[Node.js]: https://nodejs.org/
[npm]: https://www.npmjs.com/
[npx]: https://www.npmjs.com/package/npx
[Homebrew]: https://brew.sh/
[Debian]: https://www.debian.org/
[Ubuntu]: https://ubuntu.com/
[NodeSource]: https://github.com/nodesource/distributions
[nvm]: https://github.com/nvm-sh/nvm
[nvm-windows]: https://github.com/coreybutler/nvm-windows
[VSIX]: https://code.visualstudio.com/api/working-with-extensions/publishing-extension#packaging-extensions
[Open VSX Registry]: https://open-vsx.org/
[ovsx]: https://www.npmjs.com/package/ovsx
[ovsx_page]: https://open-vsx.org/extension/jintonic/g4macro
[Release]: https://github.com/jintonic/geant4-macro-extension/releases
