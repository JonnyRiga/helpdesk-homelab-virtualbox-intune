# Proof Checklist (Screenshots)

Purpose: Capture a small set of high-signal screenshots that prove the lab is built, functional, and documented. Keep the total set to 10 to 15 images.

Store screenshots in:
docs/03-proof/screenshots/

---

## 1) Architecture and VirtualBox
Save to: docs/03-proof/screenshots/architecture/
- [ ] VirtualBox network configuration showing:
  - NAT Network: NATNET-WAN
  - Host-Only: LAB-LAN (Host-Only DHCP disabled)
- [ ] pfSense VM settings showing 2 adapters:
  - Adapter 1: NAT Network NATNET-WAN (WAN)
  - Adapter 2: Host-Only LAB-LAN (LAN)

---

## 2) pfSense (Gateway, DHCP, Firewall)
Save to: docs/03-proof/screenshots/pfsense/
- [ ] Interfaces overview showing:
  - WAN assigned and receiving an address (DHCP)
  - LAN set to 192.168.56.1/24
- [ ] DHCP Server (LAN) showing scope 192.168.56.100 to 192.168.56.199
- [ ] Firewall rules showing LAN allow rule (initial baseline)
- [ ] DHCP settings showing DNS server option set to 192.168.56.10 (Windows DNS)

---

## 3) Windows Server (AD DS and DNS)
Save to: docs/03-proof/screenshots/ad/
- [ ] AD Users and Computers showing OU structure (Users, Workstations, Groups)
- [ ] Example user and security group objects (names visible)
- [ ] DNS Manager showing forward lookup zone for lab.local

---

## 4) Windows 10 Client (Domain Join and Network)
Save to: docs/03-proof/screenshots/client/
- [ ] System page showing the device joined to domain lab.local
- [ ] IP details showing:
  - DHCP address in 192.168.56.100 to 192.168.56.199
  - Gateway 192.168.56.1
  - DNS 192.168.56.10

Optional (if you enabled RDP):
Save to: docs/03-proof/screenshots/client/
- [ ] Remote Desktop enabled page or successful connection proof

---

## 5) Group Policy (GPO)
Save to: docs/03-proof/screenshots/gpo/
- [ ] Group Policy Management showing a GPO linked to an OU
- [ ] One example setting applied on the client (proof of policy effect)

---

## 6) Intune (MDM Enrollment and Compliance Reporting)
Save to: docs/03-proof/screenshots/intune/
- [ ] Intune Windows devices list showing WIN10-CLIENT enrolled/managed
- [ ] Device overview page showing management state and last check-in time
- [ ] Compliance policy assignment (policy assigned to user/device group)
- [ ] Compliance status page showing Compliant or Not compliant (with reason details)

---

## 7) Documentation proof (what recruiters value most)
Save to: docs/03-proof/screenshots/architecture/ or docs/03-proof/screenshots/
- [ ] Screenshot of Runbooks index page rendering in GitHub
- [ ] Screenshot of Ticket 001 or Ticket 005 runbook showing your structure (triage, steps, resolution, verification, escalation)

---

## Notes
- Crop screenshots tightly. Remove unnecessary UI clutter.
- Use consistent filenames (examples):
  - pfsense-interfaces.png
  - pfsense-dhcp-scope.png
  - ad-ou-structure.png
  - win10-domain-join.png
  - intune-compliance-status.png
- Redact sensitive identifiers if needed (tenant IDs, emails other than your own).
