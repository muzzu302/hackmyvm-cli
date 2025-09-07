# HMV-CLI
A powerful Python command-line interface for interacting with the [HackMyVM](https://hackmyvm.eu) platform. This tool enables cybersecurity practitioners to efficiently search, download, and manage virtual machines with persistent authentication and comprehensive filtering capabilities.

<img width="1429" height="846" alt="image" src="https://github.com/user-attachments/assets/b9933337-b3fc-4a91-a103-8276d6fa1b3d" />
<img width="1583" height="758" alt="image" src="https://github.com/user-attachments/assets/04b4c37e-cdbc-4357-aacf-b7877eb2d9cb" />
<img width="1227" height="1262" alt="image" src="https://github.com/user-attachments/assets/e2eef2fd-6dda-412b-9f06-45d27684e3f4" />

## ✨ Features

- **🔍 Advanced Machine Search**
  - Multiple filter options: difficulty, category, tags, and machine names
  - Color-coded difficulty levels for quick identification
  - Pagination support for large result sets
  - Real-time search with partial name matching

- **🎯 Difficulty Level Filtering** with visual indicators:
  - 🟢 **Easy** → Green highlighting
  - 🟡 **Medium** → Yellow highlighting
  - 🔴 **Hard** → Red highlighting

- **📂 Category & Tag Filtering**
  - Categories: `windows`, `linux`, `size`, `hacked`, `all`
  - 25+ specialized tags: `web`, `docker`, `suid`, `sqli`, `cve`, etc.

- **⚡ Efficient Operations**
  - Flag submission for completed challenges
  - Direct machine downloads as ZIP files
  - Writeup search functionality
  - Achievement statistics tracking
  - Persistent session management

- **🔐 Secure Authentication**
  - Local credential storage
  - Automatic session persistence
  - No repeated login requirements

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- Active HackMyVM account

### Installation

```bash
pipx install git+https://github.com/Yanxinwu946/hackmyvm-cli
# or
uv tool install git+https://github.com/Yanxinwu946/hackmyvm-cli
```

### Direct Execution

If you prefer not to install the package, you can run it directly from source:

```bash
git clone https://github.com/Yanxinwu946/hackmyvm-cli
cd hackmyvm-cli
python -m hmv
```

### Initial Configuration
Configure your HackMyVM credentials (required for first use):
```bash
hmv config
```
*This creates `~/.hmv/config.json` with your credentials stored locally.*

### Start Exploring
```bash
hmv search
```

## 📖 Usage Guide

### Machine Search & Discovery

#### Basic Operations
```bash
# List all available machines (first page)
hmv search

# Search by machine name (partial matching)
hmv search -n todd
hmv search -n aria

# Filter by difficulty level
hmv search -l easy
hmv search -l medium
hmv search -l hard
```

#### Advanced Filtering
```bash
# Filter by specialized tags
hmv search -t web
hmv search -t docker
hmv search -t sqli

# Combine filters
hmv search -t web -f hard

# Browse by categories
hmv search -l windows
hmv search -l linux
```

**Best Practices**:
- Combine `-t` and `-f` for precise filtering.
- Use `-p` for basic searches or with `-f` for navigation through large result sets.

#### Available Tags
`bruteforce` • `suid` • `wordpress` • `cron` • `smb` • `docker` • `sudo` • `web` • `fileupload` • `pathhijacking` • `stego` • `binary` • `capabilities` • `cve` • `commandinjection` • `portknocking` • `ssti` • `libraryhijack` • `sqli` • `lfi` • `rce` • `logpoisoning` • `nfs` • `xxe`

### Writeup Discovery
Search for community writeups and walkthroughs:
```bash
hmv writeup Todd
hmv writeup "machine name"
```

### Flag Submission
Submit flags for completed challenges:
```bash
hmv flag -i "flag{your_captured_flag}" -vm MachineName
```

**Note**: Ensure the flag format is correct to avoid submission errors.

### Machine Downloads
Download virtual machines for local setup:
```bash
hmv download Soul
hmv download TryHarder
```

### Achievement Statistics
Track and analyze overall statistics:
```bash
# View achievement statistics
hmv stats

# Update data from server
hmv stats -u

# Filter by specific VM or user
hmv stats -vm Todd
hmv stats -user Sublarge
```

### Help & Documentation
```bash
hmv -h
hmv --help              # Main help
hmv search --help       # Search options
hmv flag --help         # Flag submission help
hmv stats --help        # Statistics options
```

## ⚙️ Configuration & Files

### Configuration Files
- **`~/.hmv/config.json`** - Stores your HackMyVM credentials locally
- **`~/.hmv/session.pkl`** - Maintains active session data
- **`~/.hmv/writeups.csv`** - Cached writeup database (auto-updated)
- **`~/.hmv/achievements.csv`** - Achievement statistics data

### Pagination Behavior
- **Basic search**: Returns paginated results (use `-p` for navigation)
- **Filtered searches** (`-l`, `-n`, `-t`): Return all matching results (do not use with `-p`)
- **Client-side filtering** (`-f`): Works with pagination for refined browsing

### Security Notes
- Credentials are stored locally in JSON format
- Session data persists until manual credential update
- Never share configuration files containing your credentials

## 🔄 Updating & Maintenance

### Updating the Tool
To update to the latest version, reinstall:

#### With pipx
```bash
pipx install --force git+https://github.com/Yanxinwu946/hackmyvm-cli
```

#### With uv
```bash
uv tool install --force git+https://github.com/Yanxinwu946/hackmyvm-cli
```

### Uninstallation and Cleanup
- **Uninstall the tool**:
  ```bash
  pipx uninstall hmv-cli  # If installed with pipx
  uv tool uninstall hmv-cli  # If installed with uv
  ```
- **Clear configuration and cache**:
  ```bash
  rm -rf ~/.hmv/
  ```

## ❓ FAQ

### How do I reset my configuration?
Run `hmv config` again to update your credentials.

### Can I use this tool offline?
No, it requires an internet connection to fetch data from HackMyVM.

### What if I forget my password?
You can reset it on the HackMyVM website.

### Is my data secure?
Credentials are stored locally; avoid sharing config files.

## 🙏 Acknowledgments

Thanks to the HackMyVM community for providing a great platform for cybersecurity practice.
