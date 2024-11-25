# hacknotes

Private Notes of Zishan Ahamed Thandar
# Penetration Testing Workflow


## 1. Network Scan
- Identify live hosts
- Scan for open ports
- Identify services and versions
- Tools: Nmap, Masscan

## 2. Recon
- Passive Reconnaissance
  - WHOIS Lookup
  - Shodan
  - OSINT Tools: Recon-ng, Maltego
- Active Reconnaissance
  - Subdomain Enumeration
  - Directory Enumeration: Dirbuster, Gobuster
  - Tools: Nikto, Wappalyzer

## 3. Exploitation
- Identify vulnerabilities
  - CVE Search
  - Vulnerability Scanners: Nessus, OpenVAS
- Use exploit frameworks
  - Metasploit
  - Exploit-DB
- Custom Exploits
  - Write or modify exploits for specific vulnerabilities.

## 4. Pivoting and Tunneling
- Use compromised machines to access restricted networks.
- Techniques:
  - SSH Tunneling
  - Proxychains
  - VPN or SOCKS proxies
- Tools: Chisel, Ligolo, SSH, Metasploit

## 5. Privilege Escalation
### 5.1 Privilege Escalation for Linux
- Common Techniques:
  - `sudo -l`
  - Exploiting misconfigured SUID binaries
  - Kernel Exploits
  - Exploiting writable `PATH` or `.bashrc`
- Tools:
  - LinPEAS
  - Linux Exploit Suggester
  - GTFOBins

### 5.2 Privilege Escalation for Windows
- Common Techniques:
  - Enumerating user privileges: `whoami /priv`
  - Searching for misconfigured services
  - Registry Exploits
  - DLL Hijacking
- Tools:
  - WinPEAS
  - PowerUp
  - Windows Exploit Suggester




