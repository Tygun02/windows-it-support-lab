# T001 – DNS Name Resolution Failure

## Issue Summary

A domain-joined Windows 11 client was unable to resolve the hostname of the domain controller.

Users reported:
- Inability to access shared resources
- Failure to authenticate with domain services
- Network-related errors when attempting to connect to internal systems

---

## Environment

- Domain: LAB.local  
- Client Machine: Windows 11 Pro (Domain Joined)  
- Server: Windows Server 2022 (Domain Controller)  
- Services: Active Directory, DNS  

---

## Investigation

The following troubleshooting steps were performed:

1. Verified network connectivity using:

ping 8.8.8.8


2. Checked DNS configuration on the client machine

3. Tested DNS resolution:

nslookup dc01.lab.local


4. Reviewed network adapter settings

---

## Root Cause

The client machine was configured to use an external DNS server instead of the domain controller.

In an Active Directory environment, clients must use the domain controller as their primary DNS server for proper name resolution and authentication.

---

## Resolution

The DNS configuration on the client machine was corrected.

Steps performed:

1. Open Network Adapter Settings  
2. Access IPv4 properties  
3. Set Preferred DNS Server to the Domain Controller IP address  
4. Apply and save configuration  

---

## Validation

Validation steps performed:

1. Re-tested DNS resolution:

nslookup dc01.lab.local


2. Verified domain login functionality  
3. Confirmed access to network resources  
4. Checked Group Policy application  

All tests completed successfully.

---

## Tools Used

- nslookup  
- ping  
- Network Adapter Settings  
- Windows DNS Client  
- Event Viewer  

---

## Skills Demonstrated

- DNS troubleshooting  
- Active Directory support  
- Network diagnostics  
- Root cause analysis  
- Structured incident documentation  

---

## Evidence

Supporting screenshots and logs are stored in the `/evidence` directory.
