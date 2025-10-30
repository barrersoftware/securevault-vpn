# SecureVault VPN - Linux Client

**Branch:** `client`  
**Platform:** Linux (Debian/Ubuntu)  
**Package:** `securevault-vpn-client`

---

## Overview

Linux command-line VPN client for SecureVault VPN. Manages WireGuard tunnels with simple commands.

## Installation

### Via APT Repository

```bash
# Add SecureOS repository
echo "deb http://repo.secureos.xyz noble main" | sudo tee /etc/apt/sources.list.d/secureos.list

# Update and install
sudo apt update
sudo apt install securevault-vpn-client
```

### Manual Installation

```bash
# Download DEB
wget https://github.com/barrersoftware/securevault-vpn/releases/download/v1.0.0/securevault-vpn-client_1.0.0_amd64.deb

# Install
sudo dpkg -i securevault-vpn-client_1.0.0_amd64.deb
sudo apt --fix-broken install
```

---

## Usage

### Basic Commands

```bash
# Connect to VPN
securevault-vpn up myserver

# Disconnect
securevault-vpn down

# Check status
securevault-vpn status

# List available configs
securevault-vpn list

# Import config
securevault-vpn import ~/myserver.conf

# Remove config
securevault-vpn remove myserver

# Show help
securevault-vpn help
```

---

## Configuration

### Config File Location

```
/etc/wireguard/
├── myserver.conf
├── office.conf
└── home.conf
```

### Config File Format

```ini
[Interface]
PrivateKey = your-private-key
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = server-public-key
Endpoint = vpn.example.com:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

---

## Features

- ✅ Multiple tunnel management
- ✅ Import configs from files
- ✅ Easy connect/disconnect
- ✅ Status monitoring
- ✅ Systemd integration
- ✅ Auto-start capability
- ✅ DNS management
- ✅ Split tunneling support

---

## Examples

### Import and Connect

```bash
# Import a config
securevault-vpn import ~/work-vpn.conf

# Connect
securevault-vpn up work-vpn

# Check status
securevault-vpn status
```

### Auto-start on Boot

```bash
# Enable auto-start
sudo systemctl enable wg-quick@myserver

# Disable auto-start
sudo systemctl disable wg-quick@myserver
```

### Manual Config Creation

```bash
# Generate keys
wg genkey | tee privatekey | wg pubkey > publickey

# Create config
sudo nano /etc/wireguard/myserver.conf

# Set permissions
sudo chmod 600 /etc/wireguard/myserver.conf

# Connect
securevault-vpn up myserver
```

---

## Dependencies

Required packages (auto-installed):
- `wireguard`
- `wireguard-tools`
- `resolvconf`
- `iproute2`

---

## Troubleshooting

### VPN Won't Connect

```bash
# Check WireGuard status
sudo wg show

# Check system logs
sudo journalctl -u wg-quick@*

# Test connectivity
ping 10.0.0.1  # Your VPN gateway
```

### DNS Not Working

```bash
# Check resolv.conf
cat /etc/resolv.conf

# Restart resolvconf
sudo systemctl restart resolvconf
```

### Permission Denied

```bash
# Check config permissions
ls -l /etc/wireguard/

# Fix permissions
sudo chmod 600 /etc/wireguard/*.conf
```

---

## Uninstallation

```bash
# Remove package
sudo apt remove securevault-vpn-client

# Remove configs (optional)
sudo rm -rf /etc/wireguard/
```

---

## Support

- **GitHub Issues:** https://github.com/barrersoftware/securevault-vpn/issues
- **Email:** admin@barrersoftware.com
- **Documentation:** https://barrersoftware.com/securevault-vpn/docs

---

## License

Apache 2.0 - Based on WireGuard® by Jason A. Donenfeld

---

**SecureVault VPN Client v1.0.0**  
*Secure. Simple. Private.*
