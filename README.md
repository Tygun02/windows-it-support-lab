# Windows IT Support Lab

A hands-on Windows IT Support lab designed to simulate real-world Help Desk and IT Support scenarios using Windows Server 2022 and Windows 11.

This repository focuses on troubleshooting, investigation, and resolution of common IT issues within a domain environment.

The lab environment uses Active Directory, DNS, Group Policy, and PowerShell to replicate common enterprise support tasks.

---

## Purpose of This Project

The goal of this project is to demonstrate practical skills used by Help Desk and IT Support engineers.

Rather than just building infrastructure, this repository focuses on **diagnosing and resolving technical issues** in a structured way similar to real IT ticket workflows.

Each scenario includes:

- A reported issue
- Investigation steps
- Root cause identification
- Resolution steps
- Validation testing
- Supporting screenshots

---

## Lab Environment

## Lab Architecture

The diagram below shows the structure of the homelab environment used to simulate enterprise IT support scenarios.

![Lab Architecture](docs/Active-Directory-Homelab-Architecture.svg)

---
### Host Machine
- VMware Workstation
- Windows 11 Host

### Virtual Machines

- Windows Server 2022 (Domain Controller)
- Windows 11 Pro (Domain Client)

### Domain

`LAB.local`

---

## Technologies Demonstrated

- Active Directory Domain Services
- DNS configuration and troubleshooting
- Group Policy Management
- Domain join administration
- Remote Desktop configuration
- PowerShell administration
- Windows troubleshooting tools

---

## Troubleshooting Workflow

Each issue is investigated using a structured process similar to enterprise IT support practices.

1. **User Issue Reported**
2. **Initial Investigation**
3. **Technical Diagnosis**
4. **Root Cause Identification**
5. **Remediation Steps**
6. **Validation and Testing**
7. **Documentation of Resolution**

---

## Example Support Scenarios

| Scenario | Issue | Tools Used | Link |
|--------|------|------|------|
| DNS Name Resolution Failure | Client unable to resolve hostname | nslookup, DNS Manager | [View Ticket](docs/tickets/T001-DNS-Name-Resolution-Failure) |
| RDP Access Issue | User unable to connect via Remote Desktop | Group Policy, Local Groups | [View Ticket](docs/tickets/T002-RDP-Access-Denied-Group-Policy) |
| Group Policy Not Applying | Policy not applied on client | gpresult, RSOP | [View Ticket](docs/tickets/T003-Group-Policy-Not-Applying) |
| Domain Join Failure | Workstation unable to join domain | DNS, Event Viewer | Coming Soon |

---

## Skills Demonstrated

### Active Directory Administration

- User account creation
- Group management
- Organizational Unit configuration
- Domain authentication troubleshooting

### Group Policy Management

- GPO creation and linking
- Policy troubleshooting using `gpresult`
- Policy scope and inheritance analysis

### Networking Troubleshooting

- DNS resolution troubleshooting
- Domain connectivity diagnostics
- DHCP lease validation

### Windows Support Tools

- Event Viewer
- `gpresult`
- `nslookup`
- Remote Desktop troubleshooting
- Command-line diagnostics

---

## Documentation Approach

Each support scenario is documented in a structured format similar to an IT service desk ticket.

Documentation includes:

- Issue description
- Investigation steps
- Root cause
- Remediation process
- Validation steps
- Screenshots of results

This approach demonstrates both **technical troubleshooting ability and documentation discipline**, which are key skills for IT Support roles.

---

## Why This Project Is Relevant for Employers

This project demonstrates the practical abilities expected from Tier 1 / Tier 2 IT Support professionals, including:

- Structured troubleshooting methodology
- Windows domain support
- DNS and authentication diagnostics
- Remote access troubleshooting
- Clear technical documentation

---

## Future Improvements

Planned improvements include:

- Additional troubleshooting scenarios
- Security policy testing
- Advanced Group Policy scenarios
- Additional PowerShell automation
- Simulated enterprise incident workflows

---

## Related Projects

Active Directory Infrastructure Lab  
https://github.com/Tygun02/ActiveDirectory-Lab-Homelab

Help Desk Scenario Portfolio  
https://github.com/Tygun02/help-desk-portfolio

---

**Location:** Netherlands  
**Role Target:** IT Support / Help Desk / Junior System Administrator
