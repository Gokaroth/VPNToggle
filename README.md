# VPN Management System for Garuda Linux

## Overview
Built a complete VPN management system with smart daemon control and country selection. The system automatically handles NordVPN and OpenVPN server switching, only running services when needed to save resources.

## Main Script Features
- **Smart daemon management** - Services only run when active
- **Country selection** - Connect to specific countries or use presets
- **Intelligent cycling** - Automatically switches between states
- **Service conflict prevention** - Stops conflicting services cleanly

## File Structure
```
~/scripts/vpn-toggle.sh     # Main VPN control script
~/.bashrc                   # Contains all aliases
```

## Key Commands

### Basic VPN Control
```bash
vpn                   # Cycle through states (off → nordvpn → server → off)
vpnstatus            # Show detailed VPN status
vpnoff               # Disconnect all VPNs, stop services
vpnserver            # Start OpenVPN server
vs                   # Quick status check
```

### Country-Specific Connections
```bash
vpnus                # Connect to United States
vpnuk                # Connect to United Kingdom  
vpnde                # Connect to Germany
vpnnl                # Connect to Netherlands
vpnse                # Connect to Sweden
vpnch                # Connect to Switzerland
vpnca                # Connect to Canada
vpnjp                # Connect to Japan
vpnfr                # Connect to France
vpnno                # Connect to Norway
```

### Smart Presets
```bash
vpnpriv              # Switzerland (maximum privacy)
vpnfast              # Netherlands (fastest speeds)  
vpnstream            # United States (streaming services)
```

### Advanced Functions
```bash
vpncountry     # Connect to any available country
smartvpn    # Connect based on purpose
vpnlist              # Show complete help menu
```

### Smart VPN Purposes
```bash
smartvpn privacy     # Auto-connect to Switzerland
smartvpn speed       # Auto-connect to Netherlands
smartvpn streaming   # Auto-connect to United States
smartvpn nearby      # Auto-connect to Germany
smartvpn random      # Random privacy-focused country
```

### Cybersecurity Integration
```bash
vpntest              # Check IP and VPN status
vpncheck             # Verify VPN effectiveness
myip                 # Show current public IP
whereami             # Show geographic location
```

## Script Usage Examples
```bash
# Direct script usage with countries
~/scripts/vpn-toggle.sh nordvpn switzerland
~/scripts/vpn-toggle.sh nordvpn privacy
~/scripts/vpn-toggle.sh server
~/scripts/vpn-toggle.sh off

# Show available options
~/scripts/vpn-toggle.sh countries
~/scripts/vpn-toggle.sh help
```

## System Integration

### Service Management
The script automatically handles systemd services:
- **nordvpnd** - NordVPN daemon
- **openvpn-server@server** - OpenVPN server service

### Service States
- **enabled** - Starts automatically at boot
- **running** - Currently active
- **disabled** - Manual start only

### Systemctl Commands Used
```bash
systemctl status nordvpnd
systemctl is-active servicename
systemctl is-enabled servicename
sudo systemctl start servicename
sudo systemctl stop servicename
sudo systemctl enable servicename
sudo systemctl disable servicename
```

## Troubleshooting Commands
```bash
# Check service states
systemctl status nordvpnd
systemctl status openvpn-server@server.service

# View logs
journalctl -u nordvpnd -f
journalctl -u openvpn-server@server.service -f

# Debug script execution  
bash -x ~/scripts/vpn-toggle.sh nordvpn

# Check network interfaces
ip addr show | grep -E "(tun|tap)"
```

## Security Benefits
- **Minimal attack surface** - Only runs needed services
- **No root execution** - Uses sudo only when required  
- **Clean state management** - Proper service startup/shutdown
- **Geographic privacy** - Easy country switching for anonymity

## Country Selection Strategy
- **Switzerland/Sweden** - Maximum privacy laws
- **Netherlands** - Best speed in Europe
- **United States** - Streaming service access
- **Germany** - Balanced privacy and speed
- **Canada** - Good privacy, close to US content

## Workflow Examples
```bash
# Quick privacy browsing
vpnpriv && curl ipinfo.io

# Stream Netflix
vpnstream

# Start lab server
vpnserver

# Check anonymity
vpntest

# Cycle through all states
vpn  # Repeat to cycle: off → nord → server → off
```

## Installation Summary
1. Created VPN toggle script with country selection
2. Added comprehensive aliases to `~/.bashrc`
3. Set up NordVPN permissions and daemon
4. Configured OpenVPN server management
5. Added cybersecurity integration commands

This system provides professional-grade VPN management with one-command switching between privacy modes, streaming access, and secure server hosting.
