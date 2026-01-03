# Build Step 01: VirtualBox Networks

## Goal
Create a WAN and LAN separation so pfSense functions as the lab gateway and firewall.

## Networks to create
1. NAT Network (WAN uplink)
   - Name: NATNET-WAN
   - Network: 10.10.10.0/24
   - DHCP: Enabled or Disabled (either works, pfSense WAN will use DHCP if enabled)

2. Host-Only Network (internal lab LAN)
   - Name: LAB-LAN
   - Subnet: 192.168.56.0/24
   - Host interface IP: 192.168.56.1
   - DHCP: Disabled (pfSense will provide DHCP)

## Validation
- NATNET-WAN exists under VirtualBox NAT Networks
- LAB-LAN exists under Host-Only Networks
- Host-Only DHCP server is disabled

## Common issues
- Host-Only DHCP left enabled causes conflicting DHCP on the LAN
- Wrong adapter type selected on VMs (ensure pfSense WAN uses NATNET-WAN, pfSense LAN uses LAB-LAN)
