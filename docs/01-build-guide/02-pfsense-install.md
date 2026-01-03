# Build Step 02: pfSense Install and Base Configuration

## Goal
Deploy pfSense as the lab gateway/firewall with WAN internet access and a LAN for all lab VMs. Provide DHCP on the LAN.

## VM configuration (VirtualBox)
- VM name: pfSense
- vCPU: 2
- RAM: 2 GB
- Disk: 20 GB
- Network adapters:
  - Adapter 1 (WAN): NAT Network `NATNET-WAN`
  - Adapter 2 (LAN): Host-Only `LAB-LAN`

## Install
1. Boot from pfSense ISO.
2. Complete installation with default options.
3. Reboot into pfSense.

## Interface assignment
- WAN: Adapter 1 (DHCP from NATNET-WAN)
- LAN: Adapter 2 (static)

## LAN settings
- LAN IP: `192.168.56.1/24`
- Enable DHCP on LAN:
  - Range: `192.168.56.100` to `192.168.56.199`
  - DNS option: set later to Windows Server DNS `192.168.56.10` after AD DS/DNS is deployed

## Firewall rules (initial)
- Keep default rule allowing LAN to any (for initial build and testing)
- Tighten rules later once the lab is stable

## Validation
- pfSense WAN receives an IP address (DHCP) and has internet connectivity
- pfSense LAN is `192.168.56.1/24`
- A client VM on LAB-LAN receives a DHCP lease in `192.168.56.100-199`

## Proof screenshots to capture
- pfSense interfaces page showing WAN and LAN assignments
- DHCP Server page showing LAN scope
- Firewall rules summary (LAN rule)

## Common issues
- Client VM does not get DHCP: ensure Host-Only DHCP is disabled and pfSense DHCP is enabled on LAN
- No internet on WAN: confirm Adapter 1 is NAT Network `NATNET-WAN` (not plain NAT)
- Wrong interface mapping: re-check which NIC is WAN vs LAN
