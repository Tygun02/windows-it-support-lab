# 02 - Active Directory

## Objective
Demonstrate practical Active Directory administration aligned to Help Desk work:
- OUs for scoping and organisation
- Users/groups for access control
- Common support tasks (password reset, unlock, group membership)

## Scope
- Domain: LAB.local
- DC role: AD DS + DNS

## Typical tasks demonstrated
- Create users and groups
- Reset passwords and force password change at next logon
- Unlock accounts after lockout
- Add/remove group membership
- Move computer objects into correct OUs for GPO targeting

## Validation commands (sanitized)
- whoami
- whoami /groups
- gpresult /r
- gpresult /h C:\Temp\gpresult.html
- nslookup LAB.local

## Evidence location
- Screenshots: docs/assets/screenshots/active-directory/
- Logs/outputs: evidence/ (sanitized)
