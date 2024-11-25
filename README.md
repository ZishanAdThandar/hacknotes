# hacknotes

Private Notes of Zishan Ahamed Thandar
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

## Pivoting
- Use compromised machines to access restricted networks.
- Techniques:
  - SSH Tunneling
  - Proxychains
  - VPN or SOCKS proxies
- Tools: Chisel, Ligolo, SSH, Metasploit

## Tunneling
- Use compromised machines to create secure communication channels.
- Techniques:
  - Reverse Tunnels
  - Port Forwarding
  - Dynamic Tunnels
- Tools: SSH, Chisel, Ngrok, Socat


## Privilege Escalation
### Privilege Escalation for Linux
- Common Techniques:
  - `sudo -l`
  - Exploiting misconfigured SUID binaries
  - Kernel Exploits
  - Exploiting writable `PATH` or `.bashrc`
- Tools:
  - LinPEAS
  - Linux Exploit Suggester
  - GTFOBins

### Privilege Escalation for Windows
- Common Techniques:
  - Enumerating user privileges: `whoami /priv`
  - Searching for misconfigured services
  - Registry Exploits
  - DLL Hijacking
- Tools:
  - WinPEAS
  - PowerUp
  - Windows Exploit Suggester




