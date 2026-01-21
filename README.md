# NullSec Linux - Security Through Transparency

<div align="center">

![NullSec Logo](https://img.shields.io/badge/NullSec-Linux-00ff41?style=for-the-badge&logo=linux&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-NullSec%20Public-purple?style=for-the-badge)

**The Ultimate Security-Focused Linux Distribution**

[Download](#download) • [Features](#features) • [Documentation](#documentation) • [Community](#community)

---

</div>

## 🛡️ What is NullSec Linux?

NullSec Linux is a security-focused operating system designed for cybersecurity professionals, penetration testers, privacy advocates, and power users who demand complete control over their digital environment.

Built on a solid Debian foundation, NullSec combines cutting-edge security tools with an elegant, highly customizable interface that doesn't compromise on usability.

## ✨ Key Features

### 🔐 **Complete Security Suite**

| Tool | Description |
|------|-------------|
| **NullSec Crypt** | Military-grade AES-256-GCM file encryption |
| **NullSec Vault** | Encrypted password manager with secure generation |
| **NullSec Harden** | Automated system security hardening |
| **NullSec Shred** | DOD-compliant secure file destruction |
| **NullSec Whisper** | End-to-end encrypted messaging |

### 📡 **Network Intelligence**

| Tool | Description |
|------|-------------|
| **NullSec Scan** | Multi-protocol network & vulnerability scanner |
| **NullSec NetWatch** | Real-time traffic monitoring & analysis |
| **NullSec Proxy** | Tor/VPN/Proxy management with kill switch |
| **NullSec Torrent** | Anonymous, encrypted torrent client |
| **NullSec Verify** | File integrity & checksum verification |

### 🎨 **Professional Customization**

| Tool | Description |
|------|-------------|
| **NullSec Theme** | 8 stunning color schemes |
| **NullSec Icons** | Custom icon pack generator |
| **NullSec Plymouth** | Animated boot screens |
| **NullSec Wallpaper** | Dynamic wallpaper manager |
| **NullSec Fetch** | Stylish system info display |

### 💻 **Developer Tools**

| Tool | Description |
|------|-------------|
| **NullSec Project** | 11-language project scaffolder |
| **NullSec Code** | Optimized code editor integration |
| **NullSec Turbo** | Web dashboard & control center |

### ⚙️ **System Management**

| Tool | Description |
|------|-------------|
| **NullSec Installer** | Custom ISO & image builder |
| **NullSec Dashboard** | Real-time system monitoring |
| **NullSec Watch** | Intelligent file system watcher |

## 🖥️ Control Center

The NullSec Control Center provides a professional web-based dashboard for managing your entire system:

```
┌─────────────────────────────────────────────────────────────────┐
│  ┌──────────┐                                                   │
│  │    N     │  NullSec Control Center                          │
│  │  NullSec │                                                   │
│  └──────────┘                                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   CPU ████████████░░░░░░░░  58%     Memory ██████░░░░░░░  42%  │
│   Disk █████░░░░░░░░░░░░░░  28%     Uptime 4d 12h 37m          │
│                                                                 │
│  ┌─ Security Tools ────────────────────────────────────────┐   │
│  │  🔐 Crypt   🔑 Vault   🛡️ Harden   🗑️ Shred   💬 Whisper │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ┌─ Network Tools ─────────────────────────────────────────┐   │
│  │  📡 Scan   👁️ NetWatch   🌐 Proxy   ⬇️ Torrent   ✅ Verify │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 🎯 Who Is This For?

- **Security Researchers** - Comprehensive toolset for vulnerability assessment
- **Penetration Testers** - Everything you need in one place
- **Privacy Advocates** - Maximum privacy with Tor integration
- **System Administrators** - Powerful monitoring and hardening
- **Developers** - Secure development environment
- **Power Users** - Full control over your system

## 📦 Installation

### Quick Install (Recommended)

```bash
# Download the ISO
wget https://github.com/nullsec-linux/releases/latest/nullsec-linux.iso

# Verify checksum
sha256sum -c nullsec-linux.iso.sha256

# Write to USB (replace sdX)
sudo dd if=nullsec-linux.iso of=/dev/sdX bs=4M status=progress
```

### Install Tools on Existing System

```bash
# Clone the repository
git clone https://github.com/nullsec-linux/nullsec-tools.git
cd nullsec-tools

# Run installer
./install.sh

# Add to PATH
export PATH="$HOME/.local/bin:$PATH"
```

### Windows Installation

Download the Windows package and run `install.bat`:

```
1. Download nullsec-windows-1.0.0.zip
2. Extract to any folder
3. Run install.bat
4. Use NullSec-Menu.bat or add to PATH
```

## 🔧 Quick Start Guide

### Encrypt a File

```bash
nullsec-crypt encrypt secret-document.pdf
# Enter password when prompted
# Output: secret-document.pdf.enc
```

### Scan a Network

```bash
nullsec-scan 192.168.1.0/24 --profile full
```

### Manage Passwords

```bash
# Initialize vault
nullsec-vault init

# Add password (auto-generate)
nullsec-vault add github --generate

# Retrieve password
nullsec-vault get github
```

### Harden Your System

```bash
# Run security audit
sudo nullsec-harden --audit

# Apply recommended hardening
sudo nullsec-harden --apply
```

### Launch Control Center

```bash
nullsec-turbo
# Open http://localhost:3000
```

## 🎨 Themes

NullSec includes 8 professionally designed themes:

| Theme | Primary Color | Description |
|-------|---------------|-------------|
| **Cyber** | `#00ff41` | Classic hacker green |
| **Void** | `#6366f1` | Deep purple mystery |
| **Blood** | `#ff3333` | Aggressive red |
| **Arctic** | `#00d4ff` | Cool ice blue |
| **Toxic** | `#b8ff00` | Radioactive lime |
| **Phantom** | `#ffffff` | Minimal white |
| **Neon** | `#ff00ff` | Vibrant magenta |
| **Stealth** | `#333333` | Low-profile dark |

Apply with: `nullsec-theme apply cyber`

## 🔒 Security Philosophy

1. **Transparency** - All tools are open source
2. **No Telemetry** - Zero data collection
3. **Encryption by Default** - Protect everything
4. **Minimal Attack Surface** - Only essential services
5. **Regular Updates** - Daily security improvements

## 📊 Comparison

| Feature | NullSec | Kali | Parrot | Ubuntu |
|---------|---------|------|--------|--------|
| Security Tools | ✅ 21+ Custom | ✅ 600+ | ✅ 400+ | ❌ |
| Control Center | ✅ Web Dashboard | ❌ | ❌ | ❌ |
| Windows Tools | ✅ Native Ports | ❌ | ❌ | ❌ |
| Auto Hardening | ✅ Built-in | ❌ | ⚠️ Limited | ❌ |
| Theme System | ✅ 8 Themes | ❌ | ❌ | ⚠️ Limited |
| Daily Updates | ✅ Automated | ⚠️ | ⚠️ | ⚠️ |
| Privacy Focus | ✅ Maximum | ⚠️ | ✅ | ❌ |

## 🌐 Community

- **GitHub**: [github.com/nullsec-linux](https://github.com/nullsec-linux)
- **Documentation**: [github.com/nullsec-linux/nullsec-docs](https://github.com/nullsec-linux/nullsec-docs)
- **Issues**: [Report bugs or request features](https://github.com/nullsec-linux/nullsec-linux/issues)

## 📄 License

NullSec Linux is released under the **NullSec Public License v1.0**.

You are free to:
- Use for any purpose
- Modify and distribute
- Create derivative works

With conditions:
- Include license and attribution
- Don't use for malicious purposes
- Mark modifications clearly

---

<div align="center">

**NullSec Linux - Security Through Transparency**

*"In a world of surveillance, privacy is power."*

[![Download](https://img.shields.io/badge/Download-Latest%20Release-00ff41?style=for-the-badge)](https://github.com/nullsec-linux/releases)

</div>
