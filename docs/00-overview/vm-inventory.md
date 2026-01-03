# VM Inventory

## pfSense
- vCPU: 2
- RAM: 2 GB
- Disk: 20 GB
- NIC 1 (WAN): VirtualBox NAT Network (NATNET-WAN)
- NIC 2 (LAN): VirtualBox Host-Only (LAB-LAN)
- LAN IP: 192.168.56.1/24
- DHCP: Enabled on LAN (192.168.56.100 to 192.168.56.199)

## Windows Server (Domain Controller)
- vCPU: 2
- RAM: 4 to 6 GB
- Disk: 60 GB
- Network: LAB-LAN
- IP: 192.168.56.10 (static)
- Roles: AD DS, DNS
- Domain: lab.local

## Windows 10 Client
- vCPU: 2
- RAM: 4 GB
- Disk: 60 GB
- Network: LAB-LAN
- IP: DHCP from pfSense
- Domain join: lab.local
- MDM: Enrolled into Intune (licensed test user)
