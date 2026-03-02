# T002 – RDP Access Denied Due to Group Policy

## Ticket ID
T002

## Title
Domain User Unable to Access Workstation via Remote Desktop (RDP)

## Priority
High

## User Impact
User reports being unable to remotely access a domain-joined workstation. RDP session fails with access denied message.

## Environment
- Windows Server 2022 (Domain Controller – DC01)
- Windows 11 Pro (Domain-Joined Client – TestWin11)
- Domain: LAB.local
- Group Policy managing security configuration

---

## Issue Description (User-Reported)

User states:

> “I can connect to the machine, but it says access is denied.”

User confirms:
- Network connectivity is working
- Machine is online
- Credentials are correct

---

## Initial Assessment

Since authentication credentials are valid and network connectivity exists, issue likely relates to:

- Group Policy configuration
- RDP user rights assignment
- Security filtering

---

## Investigation Steps

### 1. Verified Computer OU Placement

Confirmed workstation is located in correct Organizational Unit.

(Screenshot: 01-computer-ou-placement.png)

---

### 2. Verified GPO Link and Security Filtering

Checked that GPO restricting RDP access was linked and applied to target computers.

(Screenshot: 02-gpo-link-filtering.png)

---

### 3. Confirmed RDP Deny Policy Configuration

Reviewed Group Policy settings:

Computer Configuration → Policies → Windows Settings → Security Settings → Local Policies → User Rights Assignment

Confirmed "Deny log on through Remote Desktop Services" policy configured.

(Screenshot: 03-deny-rdp-configured.png)

---

### 4. Tested RDP Connection

Attempted RDP login using domain test account.

Access denied error reproduced.

(Screenshot: 04-rdp-access-denied.png)

---

### 5. Verified Event Viewer Logs

Checked Security log for failed logon attempts.

Observed log entries confirming denial due to user rights assignment.

(Screenshot: 05-eventviewer-logon-denied.png)

---

## Root Cause

A Group Policy Object was configured to deny RDP logon rights to specific security groups.

The affected user account was either:

- Included in a restricted group
- Not included in the permitted RDP group
- Or affected by GPO security filtering

---

## Resolution

Identified restrictive GPO settings.

Adjusted policy configuration to:

- Remove deny rule
- Or correctly configure "Allow log on through Remote Desktop Services"

Forced policy update:

```
gpupdate /force
```

Validated updated security group membership.

---

## Validation

- RDP connection successful after policy correction
- No further access denied messages
- Event logs show successful authentication

---

## Lessons Learned

User Rights Assignment policies override standard group membership permissions.

When troubleshooting RDP access issues in a domain environment:

1. Always verify OU placement
2. Review linked GPOs
3. Inspect User Rights Assignment settings
4. Check Event Viewer security logs
