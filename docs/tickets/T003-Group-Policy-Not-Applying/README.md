# T003 – Group Policy Not Applying

## Issue Summary

A Group Policy Object (GPO) configured on the domain controller was not applying to a domain-joined Windows 11 client.

Expected settings were not reflected on the client machine after login.

---

## Environment

- Domain: LAB.local  
- Client Machine: Windows 11 Pro (Domain Joined)  
- Server: Windows Server 2022 Domain Controller  
- Services: Active Directory, Group Policy  

---

## Investigation

The following troubleshooting steps were performed:

1. Verified the client was joined to the domain  
2. Checked network connectivity to the domain controller  
3. Ran Group Policy Result:

gpresult /r

4. Reviewed applied and denied GPOs  
5. Checked Organizational Unit (OU) placement of the client  
6. Verified GPO link status and scope  
7. Confirmed security filtering settings  
8. Forced Group Policy update:

grupdate /force

---

## Root Cause

The GPO was not applying due to incorrect scope configuration.

The client machine was either:
- located in the wrong Organizational Unit (OU), or  
- not included in the GPO’s security filtering  

As a result, the policy was not being applied to the target system.

---

## Resolution

The issue was resolved by correcting the GPO scope and targeting.

Steps performed:

1. Moved the client machine to the correct OU  
2. Verified the GPO was linked to the correct OU  
3. Updated security filtering to include the appropriate group or computer  
4. Forced Group Policy update:

gpupdate /force   

5. Rebooted the client machine  

---

## Validation

Validation steps performed:

1. Ran:

gpresult/r

2. Confirmed the GPO appeared under Applied Group Policy Objects  
3. Verified that expected settings were applied on the client  
4. Confirmed consistent behaviour after restart  

The issue was resolved successfully.

---

## Tools Used

- Group Policy Management Console  
- gpresult  
- gpupdate  
- Active Directory Users and Computers  
- Command Prompt  

---

## Skills Demonstrated

- Group Policy troubleshooting  
- OU and scope management  
- Active Directory administration  
- Policy validation and testing  
- Structured incident documentation  

---

## Evidence

Screenshots and logs are stored in the `/evidence` directory.
