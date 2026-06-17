# Alex's Investigation Notes — AfricanFalls

**Investigator:** Alex Ojo
**Case:** AfricanFalls — CyberDefenders
**Date Started:** June 2026
**Date Completed:** June 2026
**Role:** Blue Team Analyst

---

## Case Summary
- **Suspect:** John Doe
- **Image File:** DiskDrigger.ad1
- **Image Type:** Custom Content Image (AD1)
- **Image Created:** June 15, 2021
- **MD5 Hash:** 9471e69c95d8909ae60ddff30d50ffa1 ✅ Verified
- **SHA1 Hash:** 167aa08db25dfeeb876b0176ddc329a3d9f2803a ✅ Verified
- **Tools Used:** FTK Imager 8.2, DB Browser for SQLite, WinPrefetchView, hashes.com

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
- **Source:** Chrome History (AppData/Local/Google/Chrome/User Data/Default/History)
- **Method:** DB Browser for SQLite → urls table → filtered by last_visit_time timestamp

### Q3 — FTP Server IP Address ✅
- **Answer:** 192.168.1.20
- **Source:** AppData/Roaming/FileZilla/recentservers.xml
- **Additional Info:** Port 21, Username: kali (Kali Linux machine)

### Q4 — Date/Time Password List Deleted ✅
- **Answer:** 2021-04-29 18:22:17 UTC
- **Source:** $Recycle.Bin → $IW9BJ2Z.txt metadata file
- **File deleted:** $RW9BJ2Z.txt (common password wordlist)

### Q5 — Tor Browser Run Count ✅
- **Answer:** 0
- **Source:** Windows Prefetch folder
- **Finding:** Only the installer prefetch exists — Tor Browser was never launched

### Q6 — Suspect Email Address ✅
- **Answer:** dreammaker82@protonmail.com
- **Source:** Chrome History — ProtonMail inbox URL

### Q7 — FQDN Port Scanned ✅
- **Answer:** dfir.science
- **Source:** AppData/Roaming/Microsoft/Windows/PowerShell/PSReadLine/ConsoleHost_history.txt
- **Command found:** nmap dfir.science

### Q8 — Country of Photo "20210429_152043.jpg" ✅
- **Answer:** Zambia
- **Source:** EXIF metadata GPS coordinates
- **Coordinates:** Latitude 16°0'0.00"S, Longitude 23°0'0.00"E → Nalolo District, Zambia

### Q9 — Parent Folder of "20210429_151535.jpg" ✅
- **Answer:** Camera
- **Source:** ShellBags analysis
- **Finding:** Image originated from LG Q7 phone → Internal storage/DCIM/Camera

### Q10 — Cracked Password Hash ✅
- **Hash:** 3DE1A36F6DDB8E036DFD75E8E20C4AF4
- **Answer:** AFR1CA!
- **Method:** hashes.com online hash cracker

### Q11 — John Doe's Windows Login Password ✅
- **Answer:** ctf2021
- **Source:** SAM database registry hive → Mimikatz hash extraction → hashes.com

---

## MITRE ATT&CK Mapping
| Technique | ID | Evidence |
|-----------|-----|---------|
| Collection | TA0009 | bettercap, FileZilla FTP to 192.168.1.20 |
| Defense Evasion | TA0005 | SDelete, Tor Browser installed |
| Discovery | TA0007 | Nmap scan of dfir.science, ipscan |
| Credential Access | TA0006 | Password lists, Cain & Abel, hash cracking |
| Command & Control | TA0011 | FTP connection to Kali machine |

---

## Timeline of Events
| Date & Time | Event |
|-------------|-------|
| 2021-04-25 17:57 | Machine first set up |
| 2021-04-28 18:17 | Nmap and bettercap downloaded |
| 2021-04-29 16:04 | FileZilla installed |
| 2021-04-29 18:17:38 | Searched "password cracking lists" |
| 2021-04-29 18:19:55 | Password list downloaded |
| 2021-04-29 18:22:17 | Password list deleted from Recycle Bin |
| 2021-04-29 18:22:32 | Tor Browser installer executed |
| 2021-04-29 | Photos taken in Zambia transferred from LG Q7 |
| 2021-04-29 | FTP connection to 192.168.1.20 (Kali machine) |
| 2021-04-29 | Nmap scan of dfir.science |
| 2021-04-30 | bettercap actively used |
| 2021-06-15 | Disk image acquired by investigator |
