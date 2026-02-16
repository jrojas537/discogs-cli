---
name: discogs-cli
description: Manages a user's vinyl record collection on Discogs. Use it to list records or folders from a collection.
metadata: {"clawdbot":{"emoji":"Vinyl","requires":{"bins":["go"]}}}
---

# Discogs Collection Manager

This skill provides a command-line interface to interact with a user's record collection on Discogs.com. It uses a subcommand structure similar to `git` or `gog`.

## Prerequisites

This skill is a Go program and requires the Go toolchain to be installed and compiled.

**Installation (Debian/Ubuntu):**
`sudo apt-get update && sudo apt-get install -y golang-go`

## One-Time Setup

Before first use, you must compile the tool and configure your credentials.

1.  **Compile the tool:**
    ```bash
    cd ./discogs-cli/scripts && go build -o discogs-cli .
    ```

2.  **Configure Credentials:** This command saves your Discogs token and username to a configuration file so you don't have to enter them again.
    ```bash
    ./discogs-cli/scripts/discogs-cli config set -u "YourUsername" -t "YourSecretToken"
    ```

## Usage

Once configured, you can run commands from anywhere by referencing the compiled binary.

### List Collection Folders

Shows all folders and their record counts.

```bash
./discogs-cli/scripts/discogs-cli collection list-folders
```

### List Releases in a Folder

Shows all records within a specific folder. The output is a formatted table.

```bash
# List all releases from the "All" folder (default)
./discogs-cli/scripts/discogs-cli collection list

# List all releases from a specific folder by ID
./discogs-cli/scripts/discogs-cli collection list --folder 8815833
```
