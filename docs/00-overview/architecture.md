```mermaid
flowchart LR
  Internet((Internet)) --> NATNET[NAT Network: NATNET-WAN 10.10.10.0/24]
  NATNET --> pfWAN[pfSense WAN (DHCP)]
  pfWAN --> pfLAN[pfSense LAN 192.168.56.1/24]
  pfLAN --> LABLAN[Host-Only: LAB-LAN 192.168.56.0/24]

  LABLAN --> DC[Windows Server DC 192.168.56.10\nAD DS + DNS]
  LABLAN --> W10[Windows 10 Client (DHCP)\nDomain Joined]
  LABLAN --> UBU[Ubuntu Server (Optional)\nAdmin practice]
  
  W10 --> Intune[Intune Admin Center\nMDM Enrollment + Compliance]


## Proof checklist (docs/03-proof/proof-checklist.md)
```md
# Proof Checklist (Screenshots)

## Architecture
- [ ] VirtualBox network list showing NATNET-WAN and LAB-LAN
- [ ] pfSense VM network adapters (WAN on NATNET-WAN, LAN on LAB-LAN)

## pfSense
- [ ] LAN interface set to 192.168.56.1/24
- [ ] DHCP Server enabled with scope 192.168.56.100-199
- [ ] Firewall rules summary (LAN allow rule)

## Windows Server (AD DS/DNS)
- [ ] AD Users and Computers showing OU structure
- [ ] DNS forward lookup zone for lab.local
- [ ] User and group objects created

## Windows 10 Client
- [ ] System properties showing domain join (lab.local)
- [ ] IP configuration showing DHCP from pfSense

## Group Policy
- [ ] Example GPO linked to Workstations OU (or Users OU)
- [ ] Evidence of a policy applied on the client

## Intune
- [ ] Device appears in Intune (Windows devices list)
- [ ] Device overview page (management state, last check-in)
- [ ] Compliance policy assignment
- [ ] Compliance status page (Compliant or Not compliant with reason)
