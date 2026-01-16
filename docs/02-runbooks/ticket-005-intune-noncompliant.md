# Ticket 005: Intune Device Non-compliant (Compliance policy failure)

## Summary
A domain-joined Windows 10 device enrolled in Intune reports as Not compliant. Compliance details show a specific setting failing.

## User impact
Potential conditional access restrictions, security posture impact, and reduced manageability. Priority depends on whether access is blocked.

## Environment
- Device: WIN10-CLIENT (domain-joined)
- MDM: Microsoft Intune
- Compliance policy: Windows 10 compliance baseline (lab)
- Network: pfSense-based lab with internet access via WAN

## Symptoms
- Device appears in Intune but shows Not compliant
- Compliance page indicates one or more failed settings
- User reports no direct error on device, but access may be impacted

## Triage questions
- Which compliance setting is failing (password, encryption, OS version, device health)?
- Is this one device or multiple devices under the same policy?
- When was the last check-in time?
- Was the policy recently changed?

## Troubleshooting performed
1. Opened the device record in Intune and reviewed:
   - Last check-in
   - Management status
   - Compliance status details
2. Identified the exact failing setting from the compliance policy report.
3. On the device, verified the corresponding local configuration:
   - Example: password/PIN requirement, device restart status, OS version level
4. Forced a sync from the device (Company Portal sync or Windows work/school sync).
5. Waited for the device to check in again and re-evaluated compliance.

## Findings / Root cause (example)
Compliance policy required a password/PIN, but the device did not have a compliant sign-in method configured, so the policy evaluation failed.

## Resolution
- Updated the device configuration to meet the compliance requirement (set a password/PIN per policy).
- Triggered device sync and confirmed policy re-evaluation.
- Confirmed device status changed to Compliant in Intune.

## Verification
- Device compliance status shows Compliant.
- Compliance details show no failed settings.
- Last check-in time updated successfully.

## Preventative / Knowledge base note
When a device reports Not compliant, always start with the compliance report to identify the exact failing control. Validate that the requirement is realistic for the device type and environment (for example, certain security controls may not be supported in a VM). Document the failing setting, remediation steps, and confirmation of compliance.

## Escalation notes
Escalate to an SME if:
- Multiple devices fail the same policy unexpectedly
- Last check-in is stale and sync attempts fail
- Policy requires unsupported features in the environment and needs redesign
