# Helpdesk Homelab (pfSense, Windows Domain, Intune MDM)

This repository documents a pfSense-based virtual homelab built in VirtualBox to practice real helpdesk workflows: Active Directory administration, DNS and DHCP troubleshooting, Group Policy validation, remote support, and Microsoft Intune (MDM) enrollment with compliance reporting.

## What I built
- pfSense firewall/router providing a WAN/LAN boundary and DHCP on the internal lab LAN
- Windows Server domain controller with AD DS and DNS (lab.local)
- Windows 10 client joined to the domain
- Microsoft Intune enrollment of the domain-joined Windows 10 client (MDM) with compliance policy and reporting validation
- Ticket-style runbooks documenting troubleshooting steps, outcomes, and escalation cues

## Skills demonstrated
- Customer support style troubleshooting and documentation (case notes, follow-up, escalation)
- Windows domain support: users and groups, password resets/unlocks, basic access troubleshooting
- Networking fundamentals: DNS, DHCP, connectivity troubleshooting
- Remote support basics: RDP and endpoint firewall rules
- MDM fundamentals: Intune enrollment, compliance policy, reporting

## Architecture
- Overview: docs/00-overview/architecture.md
- IP plan: docs/00-overview/ip-plan.md
- VM inventory: docs/00-overview/vm-inventory.md
- Diagram: docs/00-overview/network-diagram.mmd

## Build guide
1. VirtualBox networks: docs/01-build-guide/01-virtualbox-networks.md
2. pfSense install: docs/01-build-guide/02-pfsense-install.md
3. Windows Server AD DS and DNS: docs/01-build-guide/03-windows-server-ad.md
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

## Notes
This lab is designed to mirror first-line product support workflows: triage, reproduce, isolate, resolve, document, and escalate when appropriate.
