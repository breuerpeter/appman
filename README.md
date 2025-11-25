# minimal-app-manager

A minimal command-line tool for managing application installations.

## Apps directory structure

Each app in the `apps/` directory must have 4 files

```
apps/
├── app-name/
│   ├── install.sh
│   ├── uninstall.sh
│   ├── version.sh
│   └── info.txt
```

**File requirements:**

- `install.sh` - Installs the app. Accepts `-v <version>` if installing a specific version is supported (if not supported but argument is provided, do not install). Must be non-interactive.
- `uninstall.sh` - Uninstalls the app. Must be non-interactive.
- `version.sh` - Prints installed version on line 1 (empty if not installed), latest version on line 2 (empty if unknown).
- `info.txt` - (optional) Display name for the app on line 1.

## Setup

1. Add your own apps submodule (user-specific):

```bash
git submodule add <your-apps-repo-url> apps
```

2. Create a symlink to use the `setup` command from anywhere:

```bash
sudo ln -sf $(pwd)/setup /usr/local/bin/setup
```

## Usage

```bash
# List all available apps
setup list

# Check app status
setup <app>

# Install latest version
setup <app> install

# Install specific version
setup <app> install <version>

# Uninstall app
setup <app> uninstall

# Verbose mode
setup --verbose <app> install
```

## Examples

```bash
setup list
setup codex
setup codex install v0.63.0
setup codex uninstall
```
