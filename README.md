# HackNotes

Private Notes for Bug Hunters, CTF Players, Pentesters of Zishan Ahamed Thandar

## Contents
- [Machines](./Machines)
  - [Pivoting](./Machines/Pivoting.md)
  - [Tunneling](./Machines/Tunneling.md)
  - [Linux Priviledge Escalation](./Machines/LinPrivEsc.md)
  - [Windows Priviledge Escalation](./Machines/WinPrivEsc.md)
- [Web](./Web)
  - [Login Bypass](./Web/LogInBypass.md)
  - [SQL Injection](./Web/SQLInjection.md)
- [Reverse Engineering](./ReverseEngineering)
- [Binary Exploitation](./BinaryExploitation)
- [Job Notes](./Job)


You can also read for [Active Directory Notes](https://github.com/ZishanAdThandar/pentest/blob/main/notes/ActiveDirectory.md) and [Bug Bounty Methodology](https://github.com/ZishanAdThandar/pentest/blob/main/notes/BugBountyHuntingMethodology.md) from [My Pentester Guide Repo https://github.com/ZishanAdThandar/pentest](https://github.com/ZishanAdThandar/pentest).

# Penetration Testing Workflow


## Network Scan
- Identify live hosts
- Scan for open ports
- Identify services and versions
- Tools: Nmap, Masscan

## Recon
- Passive Reconnaissance
  - WHOIS Lookup
  - Shodan
  - OSINT Tools: Recon-ng, Maltego
- Active Reconnaissance
  - Subdomain Enumeration
  - Directory Enumeration: Dirbuster, Gobuster
  - Tools: Nikto, Wappalyzer

## Exploitation
- Identify vulnerabilities
  - CVE Search
  - Vulnerability Scanners: Nessus, OpenVAS
- Use exploit frameworks
  - Metasploit
  - Exploit-DB
- Custom Exploits
  - Write or modify exploits for specific vulnerabilities.






