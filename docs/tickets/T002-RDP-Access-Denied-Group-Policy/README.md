# T002 – RDP Access Denied (Group Policy)

## Issue Summary

A domain user was unable to connect to a Windows 11 machine using Remote Desktop.

The system returned an "Access Denied" error despite the machine being online and reachable.

---

## Environment

- Domain: LAB.local  
- Target Machine: Windows 11 Pro (Domain Joined)  
- Server: Windows Server 2022 Domain Controller  
- Services: Active Directory, Group Policy, Remote Desktop  

---

## Investigation

The following troubleshooting steps were performed:

1. Verified the target machine was powered on and reachable  
2. Confirmed Remote Desktop was enabled  
3. Checked Windows Firewall rules for RDP  
4. Tested connectivity using Remote Desktop Connection  
5. Reviewed local group membership (Remote Desktop Users)  
6. Ran Group Policy Result:

gpresult /r

7. Analysed applied Group Policy Objects affecting RDP access  

---

## Root Cause

A Group Policy Object (GPO) was restricting Remote Desktop access by not including the required user or group in the allowed logon settings.

The policy "Allow log on through Remote Desktop Services" did not include the correct users.

---

## Resolution

The issue was resolved by modifying the Group Policy settings.

Steps performed:

1. Opened Group Policy Management Console  
2. Located the relevant GPO affecting the client machine  
3. Edited:
- Allow log on through Remote Desktop Services  
4. Added the appropriate user/group  
5. Forced Group Policy update:

gpupdate /force

6. Re-tested Remote Desktop access  

---

## Validation

Validation steps performed:

1. Re-attempted Remote Desktop connection  
2. Successfully authenticated with the domain account  
3. Verified full desktop session access  
4. Confirmed policy application via:

gpresult /r


The issue was resolved successfully.

---

## Tools Used

- Remote Desktop Connection  
- Group Policy Management Console  
- gpresult  
- gpupdate  
- Local Security Policy  

---

## Skills Demonstrated

- Group Policy troubleshooting  
- Remote Desktop access control  
- Active Directory administration  
- Permission analysis  
- Structured incident documentation  

---

## Evidence

Screenshots and logs are stored in the `/evidence` directory.
