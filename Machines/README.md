
# CTF Box Solving Manual

- [Recon Tools and Commands](#recon-tools-and-commands)
- [Linux Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)
- [Windows Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)

## Recon Tools and Commands

- Autorecon
   - https://github.com/21y4d/nmapAutomator
   - https://github.com/Tib3rius/AutoRecon/
- Port Scan
   - rustscan
      - tcp `rustscan -a <target>`
      - udp `rustscan --udp -a <target>`
   - nmap
      - Basic All port `nnmap -Pn -T5 -A -sS -sU -p- -oN nmapfull.txt -oX nmapfull.xml <target>`
      - All port with vuln scripts `nmap --script vuln -Pn -p- -T5 -A -oN nmapvuln.txt <target>`
      - Windows AD Specific `nmap -p 53,88,135,139,389,445,464,593,636,3268,3269,3389,5985,9389,49152-65535 --script smb-enum-shares,smb-enum-users,ldap-rootdse,ldap-search,krb5-enum-users,smb-os-discovery,smb-vuln-ms17-010,smb-enum-domains,smb-enum-sessions,smb-enum-processes,smb2-security-mode,smb2-capabilities,smb-system-info,msrpc-enum,smb-brute,rdp-enum-encryption,rdp-vuln-ms12-020,rdp-ntlm-info,ssl-cert,ssl-enum-ciphers,smb-protocols,ms-sql-info,smb-vuln-regsvc-dos -oN nmapAD.txt <target> `


- Domain or IP Recon
   - dig `dig axfr @<ip_address> target.tld`
     
- Wordlist generator
   `cewl http://domain.tld/ | grep -v CeWL > custom-wordlist.txt`
- Subdomain Enumeration
   1. Gobuster ```gobuster vhost -u http://monitorsthree.htb --append-domain -w /opt/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -r```
   2. ffuf ```ffuf -w /opt/wordlists/SecLists/Discovery/DNS/namelist.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'```
- Directory Busting
   1. Recursive directory busting `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -ic -recursion -recursion-depth 3 -u https://target.com/FUZZ`
   2. Directory`ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://target.com/FUZZ/`
   3. Files `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt -u https://target.com/FUZZ/`
- BruteForce: ssh, kerbrute or any other service using hydra or any specific tool
- Check outdated or vulnerable version for any service or software using exploitdb and google
- Default Crecdentials, Check any software or service is using default credential or easy to crack username password






