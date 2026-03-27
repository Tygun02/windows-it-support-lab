# T004 – Domain Join Failure

## Issue Summary

A Windows 11 workstation was unable to join the domain.

An error was displayed during the domain join process indicating that the domain could not be contacted.

---

## Environment

- Domain: LAB.local  
- Client Machine: Windows 11 Pro  
- Server: Windows Server 2022 Domain Controller  
- Services: Active Directory, DNS  

---

## Investigation

ping 8.8.8.8

2. Attempted to contact domain controller:

ping dc01.lab.local

3. Tested DNS resolution:

nslookup dc01.lab.loacl   

4. Checked client DNS configuration  
5. Reviewed network adapter settings  
6. Checked Event Viewer for domain join errors  
7. Verified domain controller was online  

---

## Root Cause

The client machine was configured with an incorrect DNS server.

Instead of using the domain controller, it was pointing to an external DNS server, preventing domain name resolution.

As a result, the system could not locate the domain controller.

---

## Resolution

The DNS configuration on the client machine was corrected.

Steps performed:

1. Open Network Adapter Settings  
2. Access IPv4 properties  
3. Set Preferred DNS Server to the Domain Controller IP address  
4. Apply settings  
5. Retry domain join process  

---

## Validation

Validation steps performed:

1. Verified DNS resolution:

nslookup dc01/lab.local

2. Successfully joined the domain  
3. Verified domain login functionality  
4. Confirmed computer object created in Active Directory  

The issue was resolved successfully.

---

## Tools Used

- nslookup  
- ping  
- Event Viewer  
- Network Adapter Settings  
- Active Directory Users and Computers  

---

## Skills Demonstrated

- Domain join troubleshooting  
- DNS diagnostics  
- Active Directory administration  
- Network configuration  
- Root cause analysis  

---

## Evidence

Screenshots and logs are stored in the `/evidence` directory.
The following troubleshooting steps were performed:

1. Verified network connectivity:
