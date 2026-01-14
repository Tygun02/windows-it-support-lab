# 01 - Environment Setup

## Objective
Build a Windows support lab that mirrors typical internal IT / MSP environments:
- Windows Server 2022 as Domain Controller (AD DS + DNS)
- Windows 11 Pro as a domain-joined workstation
- Documented configuration with repeatable steps and evidence

## Components
- Hypervisor: VMware Workstation (or equivalent)
- Server VM: Windows Server 2022 (Domain Controller)
- Client VM: Windows 11 Pro (domain-joined)
- Domain: LAB.local

## Build standards
- Static IP for the Domain Controller
- DNS hosted on the Domain Controller
- Clear naming conventions
- Evidence: screenshots + sanitized command outputs

## Evidence location
- Screenshots: docs/assets/screenshots/environment/
- Logs/outputs: evidence/ (sanitized)

## Do not upload
- ISOs, VMDKs/VHDXs/OVAs
- Credentials, tokens, keys
- Personal data you do not want public
