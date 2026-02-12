This is a basic VS Code (and its derivatives) extension for Geant4 macro command files (with extension `.mac`).

## Features

- Syntax highlighting to distinguish between macro directories, functions, parameters, units and variables.
- Autocompletion based on a set of base macro commands.
- Adding custom macro commands from a Geant4 simulation output or explicitly in VS Code.
- Type checking of command parameters.
- Hover information for commands and directories.
- A sidebar panel for finding commands, displaying information and adding them to your macro files.

## Installation

### Open VSX (Antigravity, VSCodium, Cursor, etc.)

Search for **"Geant4 Macro"** in your editor's extension marketplace and click **Install**. This extension is hosted on the [Open VSX Registry][ovsx_page].

### VS Code (Standard)

Standard VS Code uses the Visual Studio Marketplace and does not search Open VSX by default. **VS Code users should use the [VSIX Installation](#vsix-installation) method below** or use the slightly outdated [original extension](https://github.com/Jjarchie/geant4-macro-extension) from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=jjarchie.geant4-macro-extension).

### VSIX Installation

1. Obtain the `.vsix` file from this GitHub [Releases][].
2. Install the `.vsix` file through your editor's **"Install from VSIX..."** command (found in the Extensions view `...` menu).

## Usage

The extension will be activated when opening a file with the `.mac` extension.

### 🛠 Troubleshooting: File Detection

By default, VS Code may identify `.mac` files as Shell Scripts or AppleScript. If your Geant4 macros are not being correctly colorized, you can force the association in two ways:

1. The Quick Fix (Single File)
   - Click on the Language Mode in the Status Bar (bottom right corner, it likely says "Shell Script").
   - Select "Configure File Association for '.mac'..." from the top of the list.
   - Select "Geant4 Macro".
2. The Permanent Fix (Global)
   - Add the following to your settings.json (accessible via Ctrl+Shift+P -> Preferences: Open User Settings (JSON)):

     ```json
     "files.associations": {
       "*.mac": "g4macro"
     }
     ```

### Syntax Highlighting

This extension provides syntax highlighting for Geant4 UI commands. Warnings are displayed for errors in commands and parameter types:

![Syntax Highlighting](images/type-checking.gif)

### Autocompletion

Start typing to get a list of suggested UI commands and receive prompts for the parameters of the command.

![Autocompletion](images/auto-complete.gif)

### Sidebar Panel

A convenient sidebar panel can be used to find commands and add them to your macro file.

![Sidebar Panel](images/tree-ui-example.gif)

### Hover Information

Hover over a command to see information about the command and its parameters:

![Hover Information](images/hover.gif)

### Variable Definitions

Variables are commonly included in Geant4 macros through the use of the `/control/alias [PARAMETER_NAME] [PARAMETER_VALUE]` command. This extension provides autocomplete of variables which have been defined in the macro file. The type of the parameter where the variable is included is also considered.

The variables can also be renamed using the `F2` key or by right-clicking on the variable and selecting `Rename Symbol`. The definition of the variable can also be found by clicking on the variable and selecting `Go to Definition` or by clicking the variable name while holding `Ctrl`:

![Renaming](images/rename.gif)

_Note: this extension does not currently support autocomplete for variables which are not defined in the current document, such as those used in `/control/foreach` or `/control/loop`. This will be implemented in a future release._

### Adding Custom Commands

Custom commands can be added several ways:

1. Storing the output of `/control/manual /` in a text file and running `Geant4 Macro: Add Command File...` from the command palette.
2. Running `Geant4 Macro: Add Command...` from the command palette and entering the command manually.
3. Using the code action generated on commands which do not exist. This can be done by hovering over the command and clicking the lightbulb icon, or by using the shortcut `Ctrl+.` as shown below.

![Adding Commands](images/custom-commands.gif)

Command files can also be removed using the command pallette or by directly modifying the `settings.json` file and refreshing the commands.

## Feature Requests

If you have any feature requests or issues, please open an issue on the [GitHub repository](https://github.com/jintonic/geant4-macro-extension/issues). Or better yet, submit a pull request based on the [CONTRIBUTING.md](CONTRIBUTING.md) file!

[ovsx_page]: https://open-vsx.org/extension/jintonic/g4macro
[Releases]: https://github.com/jintonic/geant4-macro-extension/releases
