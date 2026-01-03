# Build Step 03: Windows Server Domain Controller (AD DS and DNS)

## Goal
Deploy a Windows Server domain controller to provide centralized identity (Active Directory) and internal name resolution (DNS) for the lab.

## VM configuration (VirtualBox)
- VM name: WS2022-DC (or similar)
- vCPU: 2
- RAM: 4 to 6 GB
- Disk: 60 GB
- Network adapter: Host-Only `LAB-LAN`

## Network settings (static)
Set a static IP on the server:
- IP address: 192.168.56.10
- Subnet mask: 255.255.255.0
- Default gateway: 192.168.56.1 (pfSense)
- Preferred DNS: 192.168.56.10 (itself)

## Install roles
Install:
- Active Directory Domain Services (AD DS)
- DNS Server

## Promote to Domain Controller
- Create a new forest and domain: `lab.local`
- Reboot after promotion

## Create baseline directory structure (for helpdesk scenarios)
Create OUs:
- OU=Users
- OU=Workstations
- OU=Groups
- OU=Admins (optional)

Create test users:
- j.smith (standard user)
- a.support (helpdesk-style user)
- it.admin (admin account for lab management)

Create security groups:
- GG-IT-Support
- GG-Lab-Users

Add memberships:
- a.support -> GG-IT-Support
- j.smith -> GG-Lab-Users

## Update pfSense DHCP to use Windows DNS
In pfSense DHCP Server (LAN):
- DNS servers: 192.168.56.10

## Validation
- Domain `lab.local` exists
- DNS forward lookup zone for `lab.local` exists
- Client devices on LAB-LAN receive DHCP and use 192.168.56.10 as DNS
- You can log on locally to the DC using domain admin credentials

## Proof screenshots to capture
- AD Users and Computers showing OU structure
- DNS Manager showing the lab.local zone
- pfSense DHCP settings showing DNS server 192.168.56.10

## Common issues
- Clients cannot resolve names: verify pfSense DHCP DNS option points to 192.168.56.10
- Server loses connectivity: confirm gateway is 192.168.56.1 and NIC is on LAB-LAN
- Time drift breaks domain operations: ensure server time is reasonable (VM settings)
