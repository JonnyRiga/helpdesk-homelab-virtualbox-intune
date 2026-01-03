# Architecture Overview

## Goal
Build a pfSense-based virtual lab to practice helpdesk workflows: identity and access support, DNS/DHCP troubleshooting, policy validation, remote support, and Intune device management.

## Topology
- VirtualBox NAT Network provides WAN access to pfSense.
- VirtualBox Host-Only network is the internal lab LAN.
- pfSense acts as the router/firewall between WAN and LAN.
- Windows Server provides AD DS and DNS for the domain.
- Windows 10 client is domain-joined and enrolled into Intune (MDM).

## VirtualBox Networks
- NAT Network: NATNET-WAN (example 10.10.10.0/24)
- Host-Only: LAB-LAN (192.168.56.0/24)

## Components
- pfSense
  - WAN: DHCP via NATNET-WAN
  - LAN: 192.168.56.1/24
  - DHCP Server on LAN: 192.168.56.100 to 192.168.56.199
- Windows Server (Domain Controller)
  - Static IP: 192.168.56.10
  - Roles: AD DS, DNS
  - Domain: lab.local
- Windows 10 Client
  - DHCP from pfSense
  - Joined to lab.local
  - Enrolled into Intune for MDM and compliance reporting
