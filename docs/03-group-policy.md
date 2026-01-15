# 03 - Group Policy

## Objective
Demonstrate practical Group Policy management aligned to desktop support:
- Baseline configuration
- RDP access controls (if used)
- Local admin management (group-based)
- User experience policies (optional)

## Recommended validation flow
1. gpupdate /force
2. gpresult /r
3. gpresult /h C:\Temp\gpresult.html
4. Review Group Policy Operational logs:
   Applications and Services Logs > Microsoft > Windows > GroupPolicy > Operational

## Common troubleshooting checks
- Correct OU placement
- Correct GPO link and enforcement
- Security filtering / group membership
- DNS connectivity to DC
- Time sync

## Evidence location
- Screenshots: docs/assets/screenshots/group-policy/
- Logs/outputs: evidence/ (sanitized)
