# IP Plan

## LAB-LAN (Host-Only)
- Subnet: 192.168.56.0/24
- pfSense LAN: 192.168.56.1
- Windows Server DC (static): 192.168.56.10
- DHCP range (pfSense): 192.168.56.100 to 192.168.56.199
- Optional Ubuntu Server: 192.168.56.20 (static or reservation)

## DNS Plan
- Primary DNS for clients: 192.168.56.10 (Windows Server DNS)
- Gateway for clients: 192.168.56.1 (pfSense)

## NATNET-WAN (VirtualBox NAT Network)
- Network: 10.10.10.0/24
- pfSense WAN: DHCP from NAT network
