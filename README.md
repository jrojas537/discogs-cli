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

4.  **Making it Globally Accessible (Optional):**
    To run `discogs-cli` from anywhere without typing the full path, you need to place the executable in a directory that is in your system's PATH.

    -   **Option A: Move the binary (Recommended)**
        Move the compiled `discogs-cli` binary to a standard location like `/usr/local/bin`.
        ```bash
        sudo mv ./scripts/discogs-cli /usr/local/bin/discogs-cli
        ```

    -   **Option B: Create a Symbolic Link**
        Alternatively, you can create a symbolic link from its current location to a directory in your PATH.
        ```bash
        sudo ln -s "$(pwd)/scripts/discogs-cli" /usr/local/bin/discogs-cli
        ```

    Once you've done this, you can run the tool from any directory by simply typing `discogs-cli`.

## Usage

If you've made the binary globally accessible, you can run the following commands from anywhere. Otherwise, you will need to use the full path to the executable (e.g., `./scripts/discogs-cli`).

### Collection Commands
```bash
# List all collection folders
discogs-cli collection list-folders

# List records from the default "All" folder
discogs-cli collection list

# List records from a specific folder using its ID
discogs-cli collection list --folder 1234567
```

### Search Commands
```bash
# Search for a release (default type)
discogs-cli search "Daft Punk - Discovery"

# Search for an artist
discogs-cli search --type artist "Aphex Twin"
```

### Wantlist Commands
```bash
# Display all items in your wantlist
discogs-cli wantlist list

# Add a release to your wantlist by its ID
discogs-cli wantlist add 12345

# Remove a release from your wantlist by its ID
discogs-cli wantlist remove 12345
```

## License

This project is licensed under the MIT License.
