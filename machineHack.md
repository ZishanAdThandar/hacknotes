
# CTF Box Solving Manual

- [Recon Tools and Commands](#recon-tools-and-commands)
- [Linux Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)
- [Windows Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)

## Recon Tools and Commands

- Autorecon
   - https://github.com/21y4d/nmapAutomator
   - https://github.com/Tib3rius/AutoRecon/
- naabu + nmap
   - Basic `naabu -nmap-cli 'nmap -Pn -T5 -A -oN nmapbasic.txt' -host domain.com`
   - Basic All port `naabu -p 0-65535 -nmap-cli 'nmap -Pn -T5 -A -oN nmapallport.txt' -host domain.com`
   - All port with vuln scripts `naabu -p 0-65535 -nmap-cli 'nmap --script vuln -Pn -T5 -A -oN nmapvuln.txt' -host domain.com | tee -a nmap.txt`
   - Windows AD Specific `nmap -p 53,88,135,139,389,445,464,593,636,3268,3269,3389,5985,9389,49152-65535 --script smb-enum-shares,smb-enum-users,ldap-rootdse,ldap-search,krb5-enum-users,smb-os-discovery,smb-vuln-ms17-010,smb-enum-domains,smb-enum-sessions,smb-enum-processes,smb2-security-mode,smb2-capabilities,smb-system-info,msrpc-enum,smb-brute,rdp-enum-encryption,rdp-vuln-ms12-020,rdp-ntlm-info,ssl-cert,ssl-enum-ciphers,smb-protocols,ms-sql-info,smb-vuln-regsvc-dos -oN nmapAD.txt <target> `

- Wordlist generator
   `cewl http://domain.tld/ | grep -v CeWL > custom-wordlist.txt`
- Subdomain Enumeration
   1. Gobuster ```gobuster vhost -u http://monitorsthree.htb --append-domain -w /opt/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -r```
   2. ffuf ```ffuf -w /opt/wordlists/SecLists/Discovery/DNS/namelist.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'```
- Directory Busting
   1. Recursive directory busting `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -ic -recursion -recursion-depth 3 -u https://target.com/FUZZ`
   2. Directory`ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://target.com/FUZZ/`
   3. Files `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt -u https://target.com/FUZZ/`
- Parameter Fuzzing
   1. Paramter ``` ```
- BruteForce
- Check outdated or vulnerable version for any service or software using exploitdb and google
- Default Crecdentials, Check any software or service is using default credential or easy to crack username password






