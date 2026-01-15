# 04 - Troubleshooting Scenarios (Ticket Style)

Each ticket follows a support workflow:
Reported Issue > Investigation > Resolution > Validation > Prevention/Notes.

---

## Ticket 001 - Domain logon fails (DNS)
### Reported Issue
User cannot log on with domain credentials; domain cannot be contacted.

### Investigation
- Checked client network config (ipconfig /all)
- Verified DNS points to the Domain Controller
- Tested name resolution (nslookup LAB.local, nslookup <DC_HOSTNAME>)
- Confirmed DC services running (DNS/AD DS)

### Resolution
- Corrected client DNS to Domain Controller IP
- ipconfig /flushdns
- ipconfig /registerdns

### Validation
- Domain logon successful
- whoami confirms domain context
- gpresult /r confirms policies apply

### Evidence (example paths)
- docs/assets/screenshots/troubleshooting/Ticket001-ipconfig.png
- evidence/commands/ticket001-nslookup.txt
