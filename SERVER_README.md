# SecureVault VPN - Linux Server

**Branch:** `server`  
**Platform:** Linux (Debian/Ubuntu)  
**Package:** `securevault-vpn-server`

---

## Overview

Linux VPN server setup and management tool. Easily deploy and manage WireGuard VPN servers.

## Installation

### Via APT Repository

```bash
# Add SecureOS repository
echo "deb http://repo.secureos.xyz noble main" | sudo tee /etc/apt/sources.list.d/secureos.list

# Update and install
sudo apt update
sudo apt install securevault-vpn-server
```

### Manual Installation

```bash
# Download DEB
wget https://github.com/barrersoftware/securevault-vpn/releases/download/v1.0.0/securevault-vpn-server_1.0.0_amd64.deb

# Install
sudo dpkg -i securevault-vpn-server_1.0.0_amd64.deb
sudo apt --fix-broken install
```

---

## Quick Start

### Initial Setup

```bash
# Run setup wizard
sudo securevault-vpn-server setup

# Follow prompts to configure:
# - Server IP/hostname
# - Port (default: 51820)
# - Network subnet (default: 10.0.0.0/24)
# - DNS servers
```

### Start Server

```bash
# Start VPN server
sudo securevault-vpn-server start

# Enable auto-start
sudo securevault-vpn-server enable
```

---

## Commands

### Server Management

```bash
# Setup server
sudo securevault-vpn-server setup

# Start server
sudo securevault-vpn-server start

# Stop server
sudo securevault-vpn-server stop

# Restart server
sudo securevault-vpn-server restart

# Check status
sudo securevault-vpn-server status

# Enable auto-start
sudo securevault-vpn-server enable

# Disable auto-start
sudo securevault-vpn-server disable
```

### Client Management

```bash
# Add client
sudo securevault-vpn-server add-client john

# Remove client
sudo securevault-vpn-server remove-client john

# List all clients
sudo securevault-vpn-server list-clients

# Show client config
sudo securevault-vpn-server show-client john

# Generate QR code for client
sudo securevault-vpn-server qr-code john
```

### Configuration

```bash
# Edit server config
sudo securevault-vpn-server edit-config

# Show server config
sudo securevault-vpn-server show-config

# Backup config
sudo securevault-vpn-server backup

# Restore config
sudo securevault-vpn-server restore backup.tar.gz
```

---

## Configuration Files

### Server Config

```
/etc/wireguard/wg0.conf
```

Example:
```ini
[Interface]
PrivateKey = server-private-key
Address = 10.0.0.1/24
ListenPort = 51820
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

# Client: john
[Peer]
PublicKey = john-public-key
AllowedIPs = 10.0.0.2/32

# Client: jane
[Peer]
PublicKey = jane-public-key
AllowedIPs = 10.0.0.3/32
```

### Client Configs

```
/etc/wireguard/clients/
├── john.conf
├── jane.conf
└── bob.conf
```

---

## Features

- ✅ Easy setup wizard
- ✅ Client management
- ✅ QR code generation
- ✅ Auto-configuration
- ✅ NAT/Masquerading
- ✅ Systemd integration
- ✅ Backup/restore
- ✅ Traffic routing
- ✅ Multiple clients
- ✅ Security hardening

---

## Network Configuration

### Firewall Rules

```bash
# Allow VPN port
sudo ufw allow 51820/udp

# Enable IP forwarding (auto-configured by setup)
sudo sysctl -w net.ipv4.ip_forward=1
```

### Port Forwarding

If behind NAT, forward UDP port 51820 to your server.

### DNS Configuration

Server can provide DNS to clients:
- 1.1.1.1 (Cloudflare)
- 8.8.8.8 (Google)
- Custom DNS servers

---

## Security

### Best Practices

1. **Keep keys secure** - Never share private keys
2. **Use strong IPs** - Randomize VPN subnet
3. **Update regularly** - Keep packages updated
4. **Monitor logs** - Check for suspicious activity
5. **Limit access** - Only add trusted clients
6. **Backup configs** - Regular backups

### Monitoring

```bash
# Check active connections
sudo wg show

# Monitor traffic
sudo iftop -i wg0

# Check logs
sudo journalctl -u wg-quick@wg0

# View systemd status
sudo systemctl status wg-quick@wg0
```

---

## Client Distribution

### Generate Client Config

```bash
# Add client
sudo securevault-vpn-server add-client mobile-phone

# Get config file
sudo cat /etc/wireguard/clients/mobile-phone.conf

# Or generate QR code
sudo securevault-vpn-server qr-code mobile-phone
```

### Share with Client

**Option 1:** QR Code
- Client scans with WireGuard app

**Option 2:** Config File
- Send via secure channel
- Client imports into app

**Option 3:** Manual Entry
- Provide keys and settings
- Client enters manually

---

## Troubleshooting

### Server Won't Start

```bash
# Check status
sudo systemctl status wg-quick@wg0

# Check logs
sudo journalctl -xe -u wg-quick@wg0

# Verify config
sudo wg-quick strip wg0
```

### Clients Can't Connect

```bash
# Check firewall
sudo ufw status
sudo iptables -L -n

# Verify port is listening
sudo ss -tulpn | grep 51820

# Check IP forwarding
cat /proc/sys/net/ipv4/ip_forward  # Should be 1
```

### No Internet Access

```bash
# Check NAT rules
sudo iptables -t nat -L -n

# Verify routing
ip route show

# Test from server
ping -I wg0 8.8.8.8
```

---

## Advanced Configuration

### Split Tunneling

Only route specific IPs through VPN:

```ini
[Peer]
AllowedIPs = 10.0.0.0/8, 192.168.0.0/16
```

### Multiple Subnets

```ini
[Interface]
Address = 10.0.0.1/24, 10.1.0.1/24
```

### Custom DNS

```bash
# Edit client template
sudo nano /etc/wireguard/client-template.conf

# Add custom DNS
DNS = 10.0.0.1, 1.1.1.1
```

---

## Performance Tuning

### Optimize MTU

```ini
[Interface]
MTU = 1420
```

### Persistent Keepalive

```ini
[Peer]
PersistentKeepalive = 25
```

---

## Dependencies

Required packages (auto-installed):
- `wireguard`
- `wireguard-tools`
- `iptables`
- `net-tools`
- `qrencode` (for QR codes)

---

## Uninstallation

```bash
# Stop server
sudo securevault-vpn-server stop
sudo securevault-vpn-server disable

# Remove package
sudo apt remove securevault-vpn-server

# Remove configs (optional)
sudo rm -rf /etc/wireguard/
```

---

## System Requirements

- **OS:** Ubuntu 20.04+ / Debian 11+
- **Kernel:** Linux 5.6+ (WireGuard built-in)
- **RAM:** 512 MB minimum
- **CPU:** Any modern CPU
- **Network:** Public IP or port forwarding

---

## Support

- **GitHub Issues:** https://github.com/barrersoftware/securevault-vpn/issues
- **Email:** admin@barrersoftware.com
- **Documentation:** https://barrersoftware.com/securevault-vpn/docs

---

## License

Apache 2.0 - Based on WireGuard® by Jason A. Donenfeld

---

**SecureVault VPN Server v1.0.0**  
*Enterprise-grade VPN. Simplified.*
