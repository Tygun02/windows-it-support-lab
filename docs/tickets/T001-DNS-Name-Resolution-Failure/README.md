# T001 – DNS Name Resolution Failure

## Ticket ID
T001

## Title
User Unable to Access Internal Resources by Hostname

## Priority
Medium

## User Impact
User reports inability to access internal domain resources using hostname. Network connectivity is functional, but name resolution fails.

## Environment
- Windows 11 Pro (Domain-Joined Client – TestWin11)
- Windows Server 2022 (Domain Controller – DC01)
- DNS hosted on Domain Controller
- Domain: LAB.local

---

## Issue Description (User-Reported)

User states:

> “I can’t access shared resources. It says the server can’t be found.”

User confirms internet access works normally.

---

## Initial Assessment

Since external connectivity is functional, issue likely relates to internal DNS resolution rather than general network connectivity.

---

## Investigation Steps

### 1. Verified Hostname

Command used:

hostname


Confirmed correct system identity.

(Screenshot: 02-hostname.png)

---

### 2. Verified DNS Configuration

Command used:

ipconfig /all

Observed DNS server configuration.

(Screenshot: 03-dns-server-config.png)

---

### 3. Tested Name Resolution

Command used:

nslookup dc01.lab.local


Result indicated resolution failure.

(Screenshot: 04-nslookup.png)

---

### 4. Confirmed Error Condition

(Screenshot: 01-error.png)

---

## Root Cause

Client machine was not properly configured to use the internal Domain Controller as its primary DNS server.

Active Directory environments require clients to use internal DNS for domain services.

---

## Resolution

Updated client DNS configuration to point to DC01 (internal IP address).

Flushed DNS cache:

ipconfig /flushdns

Renewed IP configuration:

ipconfig /release
ipconfig /renew


---

## Validation

- Successful `nslookup` resolution.
- Hostname resolves correctly.
- User able to access internal resources.
- No further errors observed.

---

## Lessons Learned

Internal DNS configuration is critical for domain-joined systems.

Improper DNS settings can break authentication, GPO processing, and resource access.

Always validate DNS configuration first when troubleshooting AD-related issues.

