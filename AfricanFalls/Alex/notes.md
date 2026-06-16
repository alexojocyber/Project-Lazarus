# Alex's Investigation Notes — AfricanFalls

**Investigator:** Alex Ojo
**Case:** AfricanFalls — CyberDefenders
**Date Started:** June 2026
**Role:** Blue Team Analyst

---

## Case Summary
- **Suspect:** John Doe
- **Image File:** DiskDrigger.ad1
- **Image Type:** Custom Content Image (AD1)
- **Image Created:** June 15, 2021
- **MD5 Hash:** 9471e69c95d8909ae60ddff30d50ffa1 ✅ Verified
- **SHA1 Hash:** 167aa08db25dfeeb876b0176ddc329a3d9f2803a ✅ Verified
- **Tools Used:** FTK Imager 8.2, DB Browser for SQLite, hashes.com

---

## Suspicious Tools Found on Suspect's Machine
| Tool | Location | Purpose |
|------|----------|---------|
| Tor Browser | Desktop | Anonymous browsing |
| Nmap/Zenmap | Desktop | Network scanning |
| Quick Crypto | Desktop | File encryption |
| bettercap | Downloads | Network attack/MITM tool |
| SDelete | Downloads | Evidence wiping tool |
| ipscan | Downloads | IP network scanner |
| FileZilla | Installed | FTP client |
| Cain & Abel | Downloaded | Password cracking |
| Burp Suite | Downloaded | Web attack tool |

---

## Investigation Findings

### Q1 — MD5 Hash of Suspect Disk ✅
- **Answer:** 9471e69c95d8909ae60ddff30d50ffa1
- **Source:** DiskDrigger.ad1 text file

### Q2 — Search Phrase on 2021-04-29 18:17:38 UTC ✅
- **Answer:** password cracking lists
- **Source:** Chrome History file (AppData/Local/Google/Chrome/User Data/Default/History)
- **Method:** DB Browser for SQLite → urls table → filtered by last_visit_time

### Q3 — FTP Server IP Address ✅
- **Answer:** 192.168.1.20
- **Source:** AppData/Roaming/FileZilla/recentservers.xml
- **Additional Info:** Port 21, Username: kali (Kali Linux machine!)

### Q4 — Date/Time Password List Deleted ⏳
- **Status:** In progress — checking Recycle Bin

### Q5 — Tor Browser Run Count ⏳
- **Status:** In progress — checking Prefetch files

### Q6 — Suspect Email Address ✅
- **Answer:** dreammaker82@protonmail.com
- **Source:** Chrome History — ProtonMail inbox URL

### Q7 — FQDN Port Scanned ⏳
- **Status:** In progress — checking Zenmap logs

### Q8 — Country of Photo "20210429_152043.jpg" ⏳
- **Status:** In progress — checking EXIF metadata

### Q9 — Parent Folder of "20210429_151535.jpg" ⏳
- **Status:** In progress — checking ShellBags

### Q10 — Cracked Password Hash ✅
- **Hash:** 3DE1A36F6DDB8E036DFD75E8E20C4AF4
- **Answer:** AFR1CA!
- **Method:** hashes.com

### Q11 — John Doe's Windows Login Password ⏳
- **Status:** In progress — checking registry hives

---

## MITRE ATT&CK Mapping
| Technique | ID | Evidence |
|-----------|-----|---------|
| Collection | TA0009 | bettercap, FileZilla FTP |
| Defense Evasion | TA0005 | SDelete, Tor Browser |
| Discovery | TA0007 | Nmap/Zenmap, ipscan |
| Credential Access | TA0006 | Cain & Abel, password lists |

---

## Timeline of Key Events
| Date | Event |
|------|-------|
| 2021-04-25 | Machine first set up |
| 2021-04-29 | Suspect searched "password cracking lists" |
| 2021-04-29 | Suspect logged into ProtonMail |
| 2021-04-29 | Photos taken (Contact folder) |
| 2021-04-30 | bettercap actively used |
| 2021-06-15 | Disk image acquired by investigator |
