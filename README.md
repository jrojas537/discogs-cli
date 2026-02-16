# discogs-cli

A command-line interface for managing your vinyl record collection on Discogs. This tool is built with Go and is designed to be a skill for the OpenClaw AI assistant, but it can also be used as a standalone CLI.

## A Note From The Author

This is one of my first projects building a skill from scratch, and I'm new to both Go and the OpenClaw skill ecosystem. I'm actively learning and will continue to work on this project, improving it with new features and better code as I go. My goal is to add more functionality, such as adding/removing records and implementing pagination for large collections.

---

## Features

*   **List Collection Folders:** View all the folders in your Discogs collection.
*   **List Releases:** Get a clean, tabular view of all the records within a specific folder.
*   **Search Database:** Search for artists, releases, and labels on Discogs.
*   **Manage Wantlist:** List, add, or remove items from your wantlist.
*   **Secure Configuration:** Your Discogs username and personal access token are stored securely in a local configuration file.

## Getting Started

Follow these instructions to get the tool compiled and configured on your local machine.

### Prerequisites

You must have the Go programming language toolchain installed.

*   **Debian/Ubuntu:** `sudo apt-get update && sudo apt-get install -y golang-go`
*   For other systems, follow the official installation instructions at [go.dev](https://go.dev/doc/install).

### Installation & Configuration

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/jrojas537/discogs-cli.git
    cd discogs-cli
    ```

2.  **Build the Binary:**
    This command compiles the Go source code into an executable binary.
    ```bash
    cd ./scripts && go build -o discogs-cli . && cd ..
    ```
    This will create a `discogs-cli` executable inside the `./scripts/` directory.

3.  **Set Your Credentials:**
    Run the `config set` command to securely save your Discogs username and a Personal Access Token.
    ```bash
    ./scripts/discogs-cli config set -u "YourDiscogsUsername" -t "YourDiscogsToken"
    ```
    *You can generate a Personal Access Token from your Discogs account settings.*

## Usage

Once configured, you can run the following commands from the root of the project directory.

### Collection Commands
```bash
# List all collection folders
./scripts/discogs-cli collection list-folders

# List records from the default "All" folder
./scripts/discogs-cli collection list

# List records from a specific folder using its ID
./scripts/discogs-cli collection list --folder 1234567
```

### Search Commands
```bash
# Search for a release (default type)
./scripts/discogs-cli search "Daft Punk - Discovery"

# Search for an artist
./scripts/discogs-cli search --type artist "Aphex Twin"
```

### Wantlist Commands
```bash
# Display all items in your wantlist
./scripts/discogs-cli wantlist list

# Add a release to your wantlist by its ID
./scripts/discogs-cli wantlist add 12345

# Remove a release from your wantlist by its ID
./scripts/discogs-cli wantlist remove 12345
```

## License

This project is licensed under the MIT License.
