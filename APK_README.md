# SecureVault VPN - Android APK

**Branch:** `apk`  
**Platform:** Android 5.0+ (Lollipop and above)  
**Package:** `com.barrersoftware.securevaultvpn`

---

## Overview

Native Android VPN client based on WireGuard. Fast, modern, secure VPN for your Android device.

## Download

### Latest Release

**v1.0.0** - [Download APK](https://github.com/barrersoftware/securevault-vpn/releases/download/v1.0.0/securevault-vpn-v1.0.0-signed.apk)

**File:** `securevault-vpn-v1.0.0-signed.apk`  
**Size:** 17 MB  
**Signed:** Production keystore  
**Architectures:** arm64-v8a, armeabi-v7a, x86, x86_64

---

## Installation

### Step 1: Download APK

Download from:
- GitHub Releases (above)
- https://barrersoftware.com/downloads

### Step 2: Enable Unknown Sources

1. Open **Settings**
2. Go to **Security** (or **Apps & notifications**)
3. Enable **Unknown sources** (or **Install unknown apps**)
4. Allow your browser/file manager

### Step 3: Install

1. Tap downloaded APK file
2. Tap **Install**
3. Wait for installation
4. Tap **Open**

---

## First Use

### Import Config

**Method 1: QR Code (Easiest)**
1. Open SecureVault VPN
2. Tap **+** (Add tunnel)
3. Tap **Scan from QR code**
4. Scan QR code from your VPN provider
5. Tap **Save**

**Method 2: Config File**
1. Download `.conf` file
2. Open SecureVault VPN
3. Tap **+** (Add tunnel)
4. Tap **Import from file**
5. Select config file
6. Tap **Save**

**Method 3: Manual Entry**
1. Open SecureVault VPN
2. Tap **+** (Add tunnel)
3. Tap **Create from scratch**
4. Enter tunnel details:
   - Name
   - Private key (generate or paste)
   - Addresses
   - DNS servers
   - Peer public key
   - Endpoint
   - Allowed IPs
5. Tap **Save**

---

## Usage

### Connect to VPN

1. Open SecureVault VPN
2. Tap tunnel name
3. Toggle switch to **ON**
4. Grant VPN permission (first time)
5. ✅ Connected!

### Disconnect

1. Toggle switch to **OFF**
2. Disconnected

### View Statistics

- Tap connected tunnel
- View:
  - Data sent/received
  - Connection time
  - Latest handshake
  - Transfer rates

---

## Features

### Core Features
- ✅ Fast WireGuard protocol
- ✅ Multiple tunnel support
- ✅ QR code import
- ✅ Config file import
- ✅ Manual configuration
- ✅ Connection statistics
- ✅ Auto-reconnect
- ✅ Always-on VPN
- ✅ Kill switch

### Security
- ✅ State-of-the-art cryptography
- ✅ Modern protocol (WireGuard)
- ✅ No logs
- ✅ Open source
- ✅ Minimal attack surface

### Performance
- ✅ Faster than OpenVPN
- ✅ Lower battery usage
- ✅ Minimal CPU usage
- ✅ Fast handshakes
- ✅ Roaming support

---

## Configuration Format

### Example Config File

```ini
[Interface]
PrivateKey = yAnz5TF+lXXJte14tji3zlMNq+hd2rYUIgJBgB3fBmk=
Address = 10.0.0.2/24
DNS = 1.1.1.1, 1.0.0.1

[Peer]
PublicKey = HIgo9xNzJMWLKASJiL0GLS5cFkVYaTQe/3+gAv7bGh0=
Endpoint = vpn.example.com:51820
AllowedIPs = 0.0.0.0/0, ::/0
PersistentKeepalive = 25
```

### Config Sections

**[Interface]**
- `PrivateKey` - Your private key (keep secret!)
- `Address` - Your VPN IP address
- `DNS` - DNS servers (optional)
- `MTU` - Maximum transmission unit (optional)

**[Peer]**
- `PublicKey` - Server public key
- `Endpoint` - Server address:port
- `AllowedIPs` - Which IPs to route through VPN
- `PersistentKeepalive` - Keep connection alive (seconds)

---

## Advanced Settings

### Always-On VPN

1. Open **Settings**
2. Go to **Network & internet**
3. Tap **VPN**
4. Tap **⚙️** next to SecureVault VPN
5. Enable **Always-on VPN**
6. Enable **Block connections without VPN** (kill switch)

### Excluded Apps

1. Open SecureVault VPN
2. Tap tunnel
3. Tap **Edit**
4. Tap **Excluded applications**
5. Select apps to bypass VPN

### Custom DNS

1. Edit tunnel
2. Under `[Interface]`, add:
   ```
   DNS = 1.1.1.1, 8.8.8.8
   ```

### Split Tunneling

Route only specific IPs through VPN:

```ini
[Peer]
AllowedIPs = 10.0.0.0/8, 192.168.0.0/16
```

---

## Troubleshooting

### Can't Connect

**Check:**
- ✅ VPN permission granted
- ✅ Internet connection active
- ✅ Server is running
- ✅ Correct endpoint address
- ✅ Firewall allows UDP traffic

**Try:**
1. Toggle VPN off/on
2. Restart app
3. Restart phone
4. Re-import config

### No Internet When Connected

**Check:**
- ✅ `AllowedIPs` includes `0.0.0.0/0`
- ✅ Server has internet access
- ✅ Server NAT is configured
- ✅ DNS is configured

**Test:**
- Try ping from server
- Check server logs
- Test with different DNS

### Connection Drops

**Solutions:**
- Add `PersistentKeepalive = 25`
- Enable Always-on VPN
- Check battery optimization settings
- Exclude app from battery saver

### App Crashes

1. Clear app cache
2. Reinstall app
3. Report issue on GitHub

---

## Battery Optimization

### Exclude from Battery Saver

1. Open **Settings**
2. Go to **Apps**
3. Find **SecureVault VPN**
4. Tap **Battery**
5. Select **Unrestricted** or **Don't optimize**

This prevents Android from killing VPN connection.

---

## Security

### Keep Private Key Secure

- ⚠️ **Never share** your private key
- ⚠️ **Never screenshot** config files
- ⚠️ **Use secure channels** when sharing configs
- ⚠️ **Generate new keys** if compromised

### Verify APK Signature

```bash
# On computer with Android SDK
apksigner verify --verbose securevault-vpn-v1.0.0-signed.apk
```

Expected:
- Signer #1 certificate DN: CN=Barrer Software
- Verified using v1, v2, v3 schemes

---

## Supported Architectures

### Included in APK

- **arm64-v8a** - Modern 64-bit ARM (most phones)
- **armeabi-v7a** - 32-bit ARM (older phones)
- **x86** - 32-bit Intel (emulators, some tablets)
- **x86_64** - 64-bit Intel (emulators, ChromeOS)

Your device automatically uses the correct architecture.

---

## Requirements

### Minimum
- **Android:** 5.0 (Lollipop)
- **RAM:** 100 MB free
- **Storage:** 30 MB
- **Permissions:** VPN connection

### Recommended
- **Android:** 8.0+ (Oreo or newer)
- **Internet:** WiFi or mobile data

---

## Permissions

### Required
- **VPN connection** - To create VPN tunnel

### Optional
- **Camera** - For QR code scanning
- **Storage** - To import config files

No other permissions needed. No tracking. No ads.

---

## Building from Source

### Prerequisites

```bash
# Install Android SDK
sudo apt install android-sdk

# Install Gradle
sudo apt install gradle

# Clone repo
git clone https://github.com/barrersoftware/securevault-vpn.git
cd securevault-vpn
git checkout apk
```

### Build APK

```bash
# Build debug APK
./gradlew assembleDebug

# Build release APK
./gradlew assembleRelease

# Output
ls -l ui/build/outputs/apk/release/
```

### Sign APK

```bash
# Create keystore
keytool -genkey -v -keystore release.keystore \
  -alias mykey -keyalg RSA -keysize 2048 -validity 10000

# Sign APK
jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 \
  -keystore release.keystore \
  app-release-unsigned.apk mykey

# Verify
jarsigner -verify -verbose -certs app-release.apk
```

---

## Comparison with Other VPNs

| Feature | SecureVault VPN | OpenVPN | IPSec |
|---------|-----------------|---------|-------|
| **Speed** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Setup** | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐ |
| **Security** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Battery** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Code Size** | 4,000 lines | 600,000 lines | Complex |

Based on WireGuard protocol - faster and simpler than alternatives.

---

## FAQ

### Is it free?

Yes, the app is free. VPN server access depends on your provider.

### Is it open source?

Yes, source code available on GitHub under Apache 2.0 license.

### Does it collect data?

No. Zero logging. No analytics. No tracking.

### Can I use multiple tunnels?

Yes, create as many as you need. One active at a time.

### Does it work with my VPN provider?

If your provider supports WireGuard, yes!

### Can I run my own server?

Yes! Install `securevault-vpn-server` on Linux.

---

## Support

### Get Help

- **GitHub Issues:** https://github.com/barrersoftware/securevault-vpn/issues
- **Email:** admin@barrersoftware.com
- **Website:** https://barrersoftware.com

### Report Bugs

1. Go to GitHub Issues
2. Click **New Issue**
3. Describe problem
4. Include:
   - Android version
   - Device model
   - Error messages
   - Steps to reproduce

---

## Credits

### Based on WireGuard®

**Original Author:** Jason A. Donenfeld  
**Website:** https://www.wireguard.com  
**License:** Apache 2.0

### Modifications

- Package name: `com.barrersoftware.securevaultvpn`
- App name: SecureVault VPN
- Branding: Barrer Software
- Documentation: Enhanced guides

---

## Legal

### License

Apache License 2.0

Copyright 2025 Barrer Software

Based on WireGuard® Android application  
Copyright Jason A. Donenfeld

### Trademark

WireGuard® is a registered trademark of Jason A. Donenfeld.

This app is not affiliated with or endorsed by WireGuard.

---

## Version History

### v1.0.0 (2025-10-30)

- ✅ Initial public release
- ✅ Based on WireGuard Android
- ✅ SecureVault branding
- ✅ Multi-architecture support
- ✅ Production signed
- ✅ Full documentation

---

## Updates

### Check for Updates

Visit GitHub Releases for latest version:
https://github.com/barrersoftware/securevault-vpn/releases

### Auto-Update (Future)

Planned for v2.0:
- In-app update notifications
- One-tap updates
- Background updates

---

**SecureVault VPN for Android v1.0.0**  
*Fast. Secure. Private.*

Based on WireGuard® - The fastest VPN protocol.

---

**Download Now:**  
[securevault-vpn-v1.0.0-signed.apk](https://github.com/barrersoftware/securevault-vpn/releases/download/v1.0.0/securevault-vpn-v1.0.0-signed.apk)

**17 MB** | **Production Signed** | **All Architectures**
