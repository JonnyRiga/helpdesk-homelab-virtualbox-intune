# Build Step 04: Windows 10 Client Install and Domain Join

## Goal
Deploy a Windows 10 workstation on the lab LAN, join it to the domain, and validate that domain authentication and core network services work.

## VM configuration (VirtualBox)
- VM name: WIN10-CLIENT
- vCPU: 2
- RAM: 4 GB
- Disk: 60 GB
- Network adapter: Host-Only `LAB-LAN`

## Install Windows 10
- Install Windows 10 Pro (recommended for business features)
- Complete initial setup

## Network validation (before domain join)
Confirm the client receives:
- IP address in 192.168.56.100 to 192.168.56.199 (pfSense DHCP)
- Default gateway 192.168.56.1 (pfSense)
- DNS server 192.168.56.10 (Windows Server DNS)

## Join the domain
1. Rename the PC to: WIN10-CLIENT (optional but recommended)
2. Join domain: `lab.local`
3. Reboot

## Validate domain sign-in
- Sign in with a domain user (example: j.smith or a.support)
- Confirm the device appears in AD under Computers (or move it into OU=Workstations)

## Optional: enable Remote Desktop for helpdesk scenarios
- Enable RDP on the client
- Ensure Windows Defender Firewall allows RDP inbound traffic
- Test an RDP session from another admin box (or from host if you use bridged or suitable access)

## Proof screenshots to capture
- System page showing domain join to lab.local
- Client IP details showing gateway and DNS
- ADUC showing WIN10-CLIENT in the directory (preferably in OU=Workstations)

## Common issues
- Domain join fails: check DNS points to 192.168.56.10 and DC is reachable
- Login fails after join: confirm time is correct and user credentials are valid
- No DHCP lease: re-check pfSense DHCP is enabled and VirtualBox Host-Only DHCP is disabled

