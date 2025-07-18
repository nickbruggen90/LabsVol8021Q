# Project 1 Topology

## Management/WAN Network (192.168.19.0/24)
- 192.168.19.2 - WAN Gateway
- 192.168.19.128 - pfSense Branch 2 WAN (DHCP)
- 192.168.19.129 - pfSense Branch 1 WAN (DHCP)
- 192.168.19.135 - Sophos XG Firewall WAN (DHCP)

## Branch 1 Network (192.168.83.0/24)
- 192.168.83.50 - Ubuntu Server (rsyslog, NetData)
- 192.168.83.51 - Kali Client
- 192.168.83.52 - Ubuntu Client
- 192.168.83.100 - pfSense Branch 1 LAN
- 192.168.83.150 - Windows Server 2025 (AD)
- 192.168.83.151 - Windows 10 Client

## Branch 2 Network (192.168.84.0/24)
- 192.168.84.52 - Ubuntu Client
- 192.168.84.100 - pfSense Branch 2 LAN

## Sophos Network (192.168.85.0/24)
- 192.168.85.100 - Sophos XG Firewall LAN
