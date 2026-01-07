# Ticket 001: Domain Login Failure (User cannot sign in)

## Summary
Domain user cannot sign in to the Windows 10 workstation after joining the `lab.local` domain.

## User impact
User is blocked from accessing the workstation and any domain resources. High priority if affecting multiple users or a shared workstation.

## Environment
- Device: WIN10-CLIENT (domain-joined)
- Domain: lab.local
- DC/DNS: 192.168.56.10 (Windows Server AD DS + DNS)
- Gateway/DHCP: pfSense LAN 192.168.56.1 (DHCP scope 192.168.56.100-199)

## Symptoms
- Sign-in fails for domain user (example: `lab\j.smith`)
- Error indicates incorrect credentials or domain unavailable
- Local account sign-in still works (if applicable)

## Triage questions
- Is this happening for one user or multiple users?
- Did the password recently change or was the account locked?
- Can the user sign in on another domain-joined device (if available)?
- Was there any recent change to DNS, DHCP options, or network adapters?

## Troubleshooting performed
1. Verified basic network connectivity on WIN10-CLIENT (IP address, gateway, DNS server).
2. Confirmed WIN10-CLIENT is using DNS 192.168.56.10 (domain DNS) and not an external resolver.
3. Checked user account status in Active Directory:
   - Account locked out
   - Password expired
   - Disabled account
4. Performed password reset/unlock for the affected user (if needed).
5. Confirmed the workstation computer object exists in AD and is not disabled.
6. Checked for time skew between client and domain controller (common Kerberos sign-in issue).
7. Retested domain sign-in.

## Findings / Root cause (example)
Client DNS was not pointing to the domain DNS server (192.168.56.10). The client could not locate the domain controller for authentication.

## Resolution
- Corrected DHCP DNS option on pfSense to provide 192.168.56.10 as the DNS server for LAB-LAN.
- Renewed the client lease or restarted networking on WIN10-CLIENT so it received the updated DNS setting.
- Confirmed successful domain sign-in for the affected user.

## Verification
- User successfully signed in with domain credentials.
- Client resolves internal domain records (domain controller and lab.local).
- Issue does not reproduce after reboot.

## Preventative / Knowledge base note
If a domain-joined client cannot authenticate, verify DNS first. Domain authentication depends on the client using the AD DNS server. Ensure DHCP hands out the correct DNS server (192.168.56.10) and confirm the client is not using a public resolver.

## Escalation notes
Escalate to an SME if:
- Multiple users are affected and DNS settings are correct
- DC health indicators suggest replication/service issues
- Time synchronization cannot be corrected or Kerberos errors persist
