# Build Step 05: Intune (MDM) Enrollment for Domain-Joined Windows 10

## Goal
Enroll the domain-joined Windows 10 client into Microsoft Intune (MDM) and validate compliance status and reporting in the Intune admin center.

## Requirements
- Microsoft tenant (Entra ID)
- Intune-capable license assigned to the enrolling user (trial or paid)
- Windows 10 Pro recommended
- Device must have internet access (via pfSense WAN)

## Intune setup (admin center)
1. Confirm Intune is available in the tenant and the user has an Intune license.
2. Configure automatic MDM enrollment scope (MDM user scope):
   - Include the test user you will sign in with on the Windows 10 client (recommended: a cloud group).
3. Create a basic Windows compliance policy:
   - Require password (or PIN)
   - Optional: minimum OS version
   - Optional: device health settings depending on VM capabilities

## Enrollment on the Windows 10 client (domain-joined)
1. Sign in to the Windows 10 VM (domain user is fine).
2. Open Settings > Accounts > Access work or school > Connect.
3. Sign in with the licensed Entra ID user.
4. Approve allowing the organization to manage the device.
5. Wait for the device to appear in Intune.

## Validation in Intune
In Intune admin center:
- Devices > Windows > Windows devices
- Confirm:
  - The device is listed
  - Management state shows it is enrolled/managed
  - Last check-in time updates
  - Compliance state is visible

## Compliance reporting validation
1. Assign the compliance policy to the user or device group.
2. Confirm the device evaluates the policy.
3. Capture evidence of:
  - Compliance state (Compliant or Not compliant)
  - Reason details if Not compliant

## Proof screenshots to capture
- Intune device list showing the enrolled Windows 10 client
- Device overview page (management and last check-in)
- Compliance policy assignment
- Compliance status page and details

## Common issues
- Device does not appear in Intune: confirm license, MDM user scope, and internet access
- Device stuck not compliant: review the specific setting causing non-compliance and adjust VM or policy
- Enrollment fails: confirm time/date and that the VM can reach Microsoft services through pfSense
