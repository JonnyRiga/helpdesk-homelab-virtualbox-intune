# Network Diagram

```mermaid
flowchart LR
  Internet((Internet)) --> NATNET[NAT Network: NATNET-WAN 10.10.10.0/24]
  NATNET --> pfWAN[pfSense WAN (DHCP)]
  pfWAN --> pfLAN[pfSense LAN 192.168.56.1/24]
  pfLAN --> LABLAN[Host-Only: LAB-LAN 192.168.56.0/24]

  LABLAN --> DC[Windows Server DC 192.168.56.10<br/>AD DS + DNS]
  LABLAN --> W10[Windows 10 Client (DHCP)<br/>Domain Joined]
  W10 --> Intune[Intune Admin Center<br/>MDM Enrollment + Compliance]
