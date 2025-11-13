# hk - Hotkey Reference Tool

A fast, searchable personal hotkey and keyboard shortcut reference tool. Like `tldr` but for your personal hotkeys!

## Features

- **Fast search** - Quickly find the hotkey you need
- **Fuzzy matching** - Don't remember the exact term? Fuzzy search helps
- **Organized by tool** - Filter hotkeys by application (Vim, VS Code, Terminal, etc.)
- **Color-coded output** - Easy-to-read, visually organized results
- **Interactive mode** - Optional `fzf` integration for interactive browsing
- **Extensible** - Easy to add your own hotkeys

## Installation

### Quick Setup

1. Clone or download this repository:
```bash
git clone <repo-url>
cd hotkey
```

2. Add the tool to your PATH by adding this to your `~/.zshrc` or `~/.bashrc`:
```bash
export PATH="$PATH:/path/to/hotkey"
```

Or create a symlink:
```bash
ln -s /path/to/hotkey/hk /usr/local/bin/hk
```

3. Reload your shell:
```bash
source ~/.zshrc  # or source ~/.bashrc
```

### Optional: Install fzf for interactive search

For the best experience, install `fzf`:
```bash
# macOS
brew install fzf

# Linux
sudo apt-get install fzf  # Debian/Ubuntu
sudo yum install fzf      # Fedora
```

## Usage

### Basic Commands

```bash
# Search for hotkeys
hk vim                    # Search for vim-related hotkeys
hk clipboard              # Search for clipboard operations
hk navigate               # Search for navigation shortcuts

# Browse all hotkeys
hk                        # Interactive search (with fzf) or list all

# Filter by tool
hk -t vim                 # Show all Vim hotkeys
hk --tool "VS Code"       # Show all VS Code hotkeys

# List available tools
hk -l                     # List all tools with hotkey counts
hk --list

# Get help
hk --help                 # Show help message
```

### Examples

**Search for a specific function:**
```bash
$ hk clipboard
Search results for 'clipboard':

Vim [Clipboard]
  Copy to system clipboard
  → "+y

Vim [Clipboard]
  Display registers
  → :reg
```

**View all hotkeys for a tool:**
```bash
$ hk -t terminal
Hotkeys for 'terminal':

[Navigation]
  Clear screen
  → Ctrl+L

[Navigation]
  Clear line (untype everything)
  → Ctrl+U

[Commands]
  Execute last command with sudo
  → sudo !!
  ...
```

**Fuzzy search:**
```bash
$ hk nvgt        # Matches "navigation"
$ hk vscd        # Matches "VS Code"
```

## Adding Your Own Hotkeys

Edit `hotkeys.json` to add new hotkeys:

```json
{
  "hotkeys": [
    {
      "tool": "MyApp",
      "category": "General",
      "description": "Description of what it does",
      "hotkey": "Cmd+Shift+X",
      "example": "Optional usage example"
    }
  ]
}
```

### Field Descriptions

- **tool** (required): The application or tool name
- **category** (required): Category within the tool (e.g., "Navigation", "Editing", "Git")
- **description** (required): What the hotkey does
- **hotkey** (required): The keyboard shortcut or command
- **example** (optional): Usage example or additional notes

## Current Hotkey Coverage

The tool comes pre-loaded with hotkeys for:

- **iTerm2** - Terminal emulator shortcuts
- **TextMate** - Text editor commands
- **Terminal/Bash** - Command line tricks and shortcuts
- **zsh** - Shell aliases and commands
- **VS Code** - Editor shortcuts, Git, Claude Code integration
- **Vim** - Comprehensive Vim commands (motion, editing, windows, tabs, folding, etc.)

## Tips

1. **Quick access** - Create a short alias in your shell:
   ```bash
   alias k='hk'  # Now just type 'k vim'
   ```

2. **Regular updates** - Add new hotkeys as you learn them to build your personal reference

3. **Share with team** - Export your `hotkeys.json` to share common shortcuts with teammates

4. **Muscle memory** - Use `hk` when you can't remember a shortcut instead of searching online

## Why This Tool?

- Notes are slow to search through
- Online searches take too long
- Built-in help is often overwhelming
- You want a personal, curated collection
- Faster than opening cheat sheets or documentation

## Requirements

- Python 3.6+
- Optional: `fzf` for interactive mode

## License

See LICENSE file for details.

## Contributing

Feel free to:
- Add more hotkeys
- Improve the search algorithm
- Add new features
- Report bugs or suggest improvements