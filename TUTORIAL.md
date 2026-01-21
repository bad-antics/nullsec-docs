# NullSec Linux - Feature Tutorial & Guide

## Table of Contents

1. [Getting Started](#getting-started)
2. [Security Tools](#security-tools)
3. [Network Tools](#network-tools)
4. [Customization](#customization)
5. [Development Tools](#development-tools)
6. [System Management](#system-management)
7. [Windows Tools](#windows-tools)
8. [Advanced Usage](#advanced-usage)

---

## Getting Started

### First Boot

After installing NullSec Linux, you'll be greeted with the NullSec Welcome screen. Here's what to do first:

```bash
# 1. Update your system
sudo apt update && sudo apt upgrade -y

# 2. Run the security audit
sudo nullsec-harden --audit

# 3. Initialize your password vault
nullsec-vault init

# 4. Start the Control Center
nullsec-turbo
```

### Understanding the Tool Structure

All NullSec tools follow a consistent pattern:

```bash
nullsec-<toolname> <action> [options]

# Examples:
nullsec-crypt encrypt file.txt
nullsec-vault add mypassword --generate
nullsec-scan 192.168.1.1 --profile quick
```

---

## Security Tools

### NullSec Crypt - File Encryption

Military-grade AES-256-GCM encryption for your files.

#### Basic Usage

```bash
# Encrypt a file
nullsec-crypt encrypt document.pdf
# Enter password when prompted
# Creates: document.pdf.enc

# Decrypt a file
nullsec-crypt decrypt document.pdf.enc
# Enter password
# Creates: document.pdf

# Encrypt with specific output
nullsec-crypt encrypt secret.txt -o encrypted_secret.bin
```

#### Batch Operations

```bash
# Encrypt all PDFs in a folder
for f in *.pdf; do nullsec-crypt encrypt "$f"; done

# Encrypt and delete original (secure)
nullsec-crypt encrypt file.txt && nullsec-shred file.txt
```

#### Security Notes

- Uses PBKDF2 with 100,000 iterations for key derivation
- Random salt for each encryption
- Authenticated encryption prevents tampering
- No metadata leakage

---

### NullSec Vault - Password Manager

Secure, encrypted password storage.

#### Initial Setup

```bash
# Initialize new vault (first time only)
nullsec-vault init
# Create strong master password
# Vault stored at: ~/.nullsec-vault
```

#### Managing Passwords

```bash
# Add with generated password
nullsec-vault add github --generate --length 32
# Output: Generated: aK9#mP2$xL...

# Add with custom password
nullsec-vault add email "MySecretPassword123!"

# Retrieve password (copies to clipboard)
nullsec-vault get github

# List all entries
nullsec-vault list

# Remove entry
nullsec-vault remove oldsite
```

#### Advanced Features

```bash
# Export vault (encrypted backup)
nullsec-vault export > vault-backup.enc

# Change master password
nullsec-vault rekey

# Search entries
nullsec-vault search "git"
```

---

### NullSec Harden - System Hardening

Automated security audit and hardening.

#### Security Audit

```bash
# Basic audit
sudo nullsec-harden --audit

# Verbose output with recommendations
sudo nullsec-harden --audit --verbose

# Generate HTML report
sudo nullsec-harden --audit --report
```

#### What It Checks

- Firewall configuration
- SSH hardening
- User account security
- Service minimization
- File permissions
- Kernel parameters
- Network settings
- Update status

#### Apply Hardening

```bash
# Preview changes
sudo nullsec-harden --preview

# Apply recommended settings
sudo nullsec-harden --apply

# Apply specific category
sudo nullsec-harden --apply --only ssh,firewall
```

---

### NullSec Shred - Secure Deletion

DOD 5220.22-M compliant file destruction.

```bash
# Securely delete a file
nullsec-shred secret.txt

# Delete with 7 passes (paranoid)
nullsec-shred secret.txt --passes 7

# Shred directory recursively
nullsec-shred --recursive secret-folder/

# Wipe free space on disk
nullsec-shred --free-space /dev/sda1
```

---

### NullSec Whisper - Encrypted Messaging

End-to-end encrypted communication.

```bash
# Generate key pair
nullsec-whisper keygen

# Share public key
nullsec-whisper pubkey > my-public-key.txt

# Encrypt message for recipient
echo "Secret message" | nullsec-whisper encrypt recipient-pubkey.txt

# Decrypt received message
nullsec-whisper decrypt < encrypted-message.txt
```

---

## Network Tools

### NullSec Scan - Network Scanner

Comprehensive port and vulnerability scanning.

#### Basic Scanning

```bash
# Quick scan (common ports)
nullsec-scan 192.168.1.1

# Full port scan (1-65535)
nullsec-scan 192.168.1.1 --profile full

# Scan specific ports
nullsec-scan 192.168.1.1 --ports 80,443,8080

# Scan port range
nullsec-scan 192.168.1.1 --ports 1-1000
```

#### Network Discovery

```bash
# Scan entire subnet
nullsec-scan 192.168.1.0/24 --discovery

# Find live hosts
nullsec-scan 10.0.0.0/24 --ping-sweep
```

#### Advanced Features

```bash
# Service detection
nullsec-scan target.com --service-detection

# Vulnerability hints
nullsec-scan target.com --vuln-scan

# Output to file
nullsec-scan target.com --output scan-results.json
```

---

### NullSec NetWatch - Traffic Monitor

Real-time network traffic analysis.

```bash
# Start monitoring
sudo nullsec-netwatch

# Monitor specific interface
sudo nullsec-netwatch --interface eth0

# Filter by port
sudo nullsec-netwatch --port 443

# Log to file
sudo nullsec-netwatch --log traffic.log
```

---

### NullSec Proxy - Privacy Manager

Tor, VPN, and proxy management.

```bash
# Start Tor routing
nullsec-proxy tor start

# Check current IP
nullsec-proxy status

# Get new Tor identity
nullsec-proxy tor newidentity

# Configure system proxy
nullsec-proxy set socks5://127.0.0.1:9050

# Enable kill switch (blocks non-Tor traffic)
sudo nullsec-proxy killswitch enable
```

---

## Customization

### NullSec Theme - Desktop Theming

```bash
# List available themes
nullsec-theme list

# Apply theme
nullsec-theme apply cyber

# Preview theme
nullsec-theme preview void

# Create custom theme
nullsec-theme create mytheme --primary "#ff6600"
```

### Theme Colors

| Theme | Look |
|-------|------|
| cyber | Classic green terminal |
| void | Deep purple elegance |
| blood | Aggressive red |
| arctic | Cool blue |
| toxic | Radioactive green |
| phantom | Minimal white |
| neon | Vibrant pink |
| stealth | Low-profile gray |

---

### NullSec Fetch - System Info

```bash
# Display system info
nullsec-fetch

# Minimal output
nullsec-fetch --minimal

# ASCII art only
nullsec-fetch --logo-only
```

---

## Development Tools

### NullSec Project - Project Scaffolder

Create projects in 11 languages with proper structure.

```bash
# Interactive mode
nullsec-project

# Quick create
nullsec-project python myapp
nullsec-project rust myproject
nullsec-project node myserver

# With git init
nullsec-project go myapi --git

# Available templates:
# python, rust, go, node, typescript, c, cpp, java, ruby, php, bash
```

---

### NullSec Turbo - Control Center

```bash
# Start dashboard
nullsec-turbo

# Custom port
PORT=8080 nullsec-turbo

# Access at http://localhost:3000
```

#### Dashboard Features

- Real-time system stats (CPU, Memory, Disk)
- Network interface monitoring
- Process manager
- Service status
- Tool launcher
- Security quick actions

---

## System Management

### NullSec Dashboard - System Monitor

```bash
# Terminal dashboard
nullsec-dashboard

# Custom refresh rate
nullsec-dashboard --refresh 1

# Single snapshot
nullsec-dashboard --once
```

---

### NullSec Watch - File Watcher

```bash
# Watch directory for changes
nullsec-watch /path/to/dir

# Execute command on change
nullsec-watch ./src --exec "npm run build"

# Watch specific extensions
nullsec-watch . --filter "*.js,*.ts"
```

---

## Windows Tools

NullSec tools are also available for Windows!

### Installation

1. Download `nullsec-windows-1.0.0.zip`
2. Extract and run `install.bat`
3. Use `NullSec-Menu.bat` or add to PATH

### Usage (PowerShell)

```powershell
# Encryption
.\nullsec-crypt.ps1 encrypt document.docx

# Password vault
.\nullsec-vault.ps1 init
.\nullsec-vault.ps1 add github -Generate

# Network scan
.\nullsec-scan.ps1 192.168.1.1 -Profile full

# Security audit
.\nullsec-harden.ps1 audit -Verbose

# System monitor
.\nullsec-dashboard.ps1
```

---

## Advanced Usage

### Automated Security Workflow

Create a daily security routine:

```bash
#!/bin/bash
# daily-security.sh

echo "=== NullSec Daily Security Check ==="

# Update tools
nullsec-auto-update

# Run security audit
sudo nullsec-harden --audit --report

# Check for suspicious network activity
sudo nullsec-netwatch --duration 60 --alert

# Rotate Tor identity
nullsec-proxy tor newidentity

# Backup vault
nullsec-vault export > ~/backups/vault-$(date +%Y%m%d).enc

echo "=== Security check complete ==="
```

### Integration with Other Tools

```bash
# Use with nmap
nullsec-scan target.com --export-nmap | nmap -iL -

# Pipe to encryption
tar czf - important/ | nullsec-crypt encrypt --stdin > backup.tar.gz.enc

# Combine with SSH
nullsec-crypt decrypt secrets.enc | ssh user@server "cat > /tmp/secrets"
```

### Environment Variables

```bash
# Custom vault location
export NULLSEC_VAULT="$HOME/.secure/vault"

# Default scan profile
export NULLSEC_SCAN_PROFILE="full"

# Theme preference
export NULLSEC_THEME="cyber"

# Proxy settings
export NULLSEC_PROXY="socks5://127.0.0.1:9050"
```

---

## Troubleshooting

### Common Issues

**Tool not found**
```bash
# Ensure PATH is set
export PATH="$HOME/.local/bin:$PATH"
# Add to ~/.bashrc for persistence
```

**Permission denied**
```bash
# Some tools require sudo
sudo nullsec-harden --audit
sudo nullsec-netwatch
```

**Vault locked**
```bash
# Check vault file permissions
ls -la ~/.nullsec-vault
chmod 600 ~/.nullsec-vault
```

### Getting Help

```bash
# Any tool
nullsec-<tool> --help
nullsec-<tool> help

# Version info
nullsec-<tool> --version
```

---

## Support

- GitHub Issues: [nullsec-linux/issues](https://github.com/nullsec-linux/nullsec-linux/issues)
- Documentation: [nullsec-linux/docs](https://github.com/nullsec-linux/nullsec-docs)

---

*NullSec Linux - Security Through Transparency*
