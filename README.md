# Helpdesk Homelab (pfSense, Windows Domain, Intune MDM)

## What I built
- pfSense firewall/router providing a lab WAN/LAN boundary and DHCP on the internal LAN
- Windows Server domain controller with AD DS and DNS (lab.local)
- Windows 10 client joined to the domain
- Microsoft Intune enrollment of the domain-joined Windows 10 client (MDM) with compliance policy and reporting validation
- Ticket-style runbooks documenting troubleshooting steps and outcomes

## Skills demonstrated
- Customer support style troubleshooting and documentation (case notes, escalation cues)
- Windows domain support: users/groups, password resets/unlocks, GPO basics
- Networking fundamentals: DNS, DHCP, connectivity troubleshooting
- Remote support basics: RDP and endpoint firewall rules
- MDM basics: Intune enrollment, compliance policy, reporting

## Architecture
- See: docs/00-overview/architecture.md
- IP plan: docs/00-overview/ip-plan.md
- Diagram: docs/00-overview/network-diagram.mmd

## Build guide
1. VirtualBox networks: docs/01-build-guide/01-virtualbox-networks.md
2. pfSense install: docs/01-build-guide/02-pfsense-install.md
3. Windows Server AD DS/DNS: docs/01-build-guide/03-windows-server-ad.md
4. Windows 10 domain join: docs/01-build-guide/04-windows10-domain-join.md
5. Intune MDM enrollment: docs/01-build-guide/05-intune-mdm-enrollment.md

## Runbooks (ticket-style)
- Template: docs/02-runbooks/ticket-template.md
- Ticket 001: Domain login failure
- Ticket 002: RDP connectivity failure
- Ticket 003: DNS resolution issue
- Ticket 004: DHCP lease issue
- Ticket 005: Intune device non-compliant

## Proof (screenshots)
See docs/03-proof/proof-checklist.md and docs/03-proof/screenshots/

## Next improvements
- Add segmentation (VLANs) and tighter pfSense LAN rules
- Add a second Windows client and standardize baseline policies
- Add Hybrid Entra ID Join (phase 2)
