# 🔐 SecureVault VPN

**Privacy-focused VPN client powered by WireGuard®**

Part of the SecureVault product family by [Barrer Software](https://barrersoftware.com)

---

## 🌟 Features

- 🔒 **Zero Logging** - No tracking, no data collection
- ⚡ **Lightning Fast** - WireGuard protocol performance
- 🛡️ **Secure by Design** - Modern cryptography
- 📱 **Android Native** - Optimized for mobile
- 🎨 **SecureVault Branding** - Professional interface
- 🔓 **Open Source** - Full transparency

---

## 📥 Download

### Latest Release

**Version:** 1.0.0  
**Size:** 17 MB  
**Platform:** Android 5.0+

[📱 Download APK](https://github.com/barrersoftware/securevault-vpn/releases)

---

## ⚙️ Installation

1. Download the APK from [Releases](https://github.com/barrersoftware/securevault-vpn/releases)
2. Enable "Install from Unknown Sources" in Android settings
3. Install the APK
4. Import your WireGuard configuration
5. Connect!

---

## 🔧 Configuration

SecureVault VPN uses standard WireGuard configuration files.

### Import Methods

- **QR Code** - Scan from your VPN provider
- **File Import** - `.conf` file
- **Manual Entry** - Enter details manually

### Example Configuration

```ini
[Interface]
PrivateKey = YOUR_PRIVATE_KEY
Address = 10.0.0.2/32
DNS = 1.1.1.1

[Peer]
PublicKey = SERVER_PUBLIC_KEY
Endpoint = vpn.example.com:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

---

## 🚀 Features

### Core Functionality

- ✅ Multiple tunnel support
- ✅ Quick toggle on/off
- ✅ Auto-connect on boot
- ✅ Exclude apps (split tunneling)
- ✅ Import/export configs
- ✅ QR code scanning

### Security

- ✅ ChaCha20-Poly1305 encryption
- ✅ Curve25519 key exchange
- ✅ BLAKE2s hashing
- ✅ No logs, no tracking
- ✅ Perfect forward secrecy

### Interface

- ✅ Clean, modern design
- ✅ SecureVault branding
- ✅ Quick connection status
- ✅ Data usage stats
- ✅ Dark mode support

---

## 🏗️ Building from Source

### Requirements

- Android Studio
- Android SDK (API 34+)
- Android NDK (26+)
- Java JDK 17+
- Git

### Build Steps

```bash
# Clone repository
git clone https://github.com/barrersoftware/securevault-vpn
cd securevault-vpn

# Initialize submodules
git submodule update --init --recursive

# Build release APK
./gradlew assembleRelease

# APK location:
# ui/build/outputs/apk/release/ui-release-unsigned.apk
```

---

## 📦 What's Included

- **SecureVault VPN** Android app
- WireGuard protocol implementation
- Native Android UI
- Professional branding

---

## 🔗 Related Projects

- [SecureVault Browser](https://github.com/barrersoftware/securevault-browser) - Privacy-focused web browser
- [SecureOS](https://github.com/barrersoftware/SecureOS) - Security-focused Linux distribution
- [AI Security Scanner](https://github.com/barrersoftware/ai-security-scanner) - Enterprise security tool

---

## 📄 License

This project is based on [WireGuard for Android](https://git.zx2c4.com/wireguard-android) by Jason A. Donenfeld.

**Apache License 2.0**

- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use

See [LICENSE](LICENSE) for full details.

---

## 🙏 Credits

**Based on WireGuard®**  
Created by Jason A. Donenfeld  
https://www.wireguard.com

**WireGuard** is a registered trademark of Jason A. Donenfeld.

---

## 🆘 Support

- **Website:** https://barrersoftware.com
- **Email:** admin@barrersoftware.com
- **Issues:** [GitHub Issues](https://github.com/barrersoftware/securevault-vpn/issues)

---

## 🔒 Security

Found a security issue? Please email: admin@barrersoftware.com

Do not create public GitHub issues for security vulnerabilities.

---

## 🌐 Part of SecureVault

SecureVault VPN is part of the SecureVault product family:

- **SecureVault Browser** - Privacy web browser
- **SecureVault VPN** - This app
- **SecureOS** - Security Linux distro

All focused on privacy, security, and user control.

---

**🛡️ Built by [Barrer Software](https://barrersoftware.com)**

*Secure. Private. Powerful.*
