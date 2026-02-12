# Change Log

All notable changes to this project will be documented in this file.

## [1.0.0] - 2026-02-12

Forked from <https://github.com/Jjarchie/geant4-macro-extension> to publish to [OVSX](https://open-vsx.org/)

### Changed

- Bumped version to 1.0.0.
- Bumped dev dependencies to latest versions.
- Changed publisher to [jintonic](https://github.com/jintonic) to publish to [OVSX](https://open-vsx.org/).
- Renamed vse-extension-quick-start.md to [CONTRIBUTING.md](CONTRIBUTING.md), updated its content to match the new workflow.
- Updated the "Installation" section in [README.md](README.md).

### Added

- Added more macro commands to [command_output.md](command_output.md) using [GEARS][] on Geant4 11.4.0.
- Added `mimetype` and `firstLine` to language configuration in [package.json](package.json) to improve language auto-detection.
- Added "Troubleshooting" section to [README.md](README.md) regarding language auto-detection.
- Added icons for the sidebar views in [package.json](package.json).
- Added [src](src), [images](images)`/*.gif` `node_modules` to [.vscodeignore](.vscodeignore) to reduce package size.
- Added a GitHub Action for publishing to [OVSX](https://open-vsx.org/).
- Added GitHub pull request and issue templates.
- Added recommended extensions in [extensions.json](.vscode/extensions.json).
- Added [prettier](https://prettier.io/) for code formatting.
- Added `"skipLibCheck": true` to [tsconfig.json](tsconfig.json) to skip type checking for dependencies.
- Added more scripts to [package.json](package.json).
- Added "NPM: Increment Version" and "Git: Push Tags" to [tasks.json](.vscode/tasks.json) to streamline publishing.
- Added [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
- Added [husky](https://typicode.github.io/husky/) to trigger formatting and linting before committing.
- Added jintonic in [LICENSE](LICENSE).

### Removed

- Removed `npm:watch` from [tasks.json](.vscode/tasks.json) as all scripts in [package.json](package.json) can be run in the "NPM Scripts" section in the VS Code Explorer.

## [0.4.1] - 2025-03-16

### Fixed

- Made sidebar logo consistent with other logos (was missing one arm).

## [0.4.0] - 2025-03-15

### Added

- Implemented a view in the sidebar for showing available commands, information, basic search and quickly adding them into an open macro file.
- Created icons for Geant4 macro files (both dark and light mode) and sidebar.
- Sorting of commands in alphabetical order.

### Fixed

- An error due to an incorrect number of parameters will no longer show when using quotation marks in parameters and using comments inline.
- A minor bug was rectified where the completion dialogue shows the second parameter highlighted rather than the first one when a new macro command is entered.
- A warning now shows when no arguments are supplied to a command and the command requires non-omittable arguments.

## [0.2.0] - 2025-03-13

### Added

- Fixed type checking for variables as defined through /control/alias.
- Implemented definition provider so that a variable definition can be found from its usage throughout the macro.
- Added renaming support so that a variable can be consistently renamed throughout the macro.
- Added autocomplete for when the braces are used.

### Fixed

- Fixed issue [#5](https://github.com/Jjarchie/geant4-macro-extension/issues/5), where text in comments were interpreted as parameters leading to incorrect warnings.

[GEARS]: https://github.com/jintonic/gears
