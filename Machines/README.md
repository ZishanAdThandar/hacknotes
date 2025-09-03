This is a basic note for Red Teamers, Pentesters, Offsec Enthusiast, CTF Players etc

For Activity Directory notes check [Active Directory](https://github.com/ZishanAdThandar/pentest/blob/main/notes/ActiveDirectory.md).

You can use my script [Hackify](https://github.com/ZishanAdThandar/hackify) to install tools and wordlist on your linux system.

# CTF Box Solving Manual

- [Recon Tools and Commands](#recon-tools-and-commands)
- [Linux Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)
- [Windows Priviledge Escalation](https://github.com/ZishanAdThandar/hacknotes)

## Recon Tools and Commands

- Autorecon
   - https://github.com/21y4d/nmapAutomator `nmapAutomator -H <target> -t Full`
   - https://github.com/Tib3rius/AutoRecon/
- Port Scan
   - rustscan
      - TCP `rustscan -r 1-65535 -a <target> -b 10000 -- -sC -sV -A -Pn`
      - udp `rustscan --udp -r 1-65535 -a <target> -b 10000 -- -sC -sV -A -Pn`
   - naabu
      - tcp all `naabu -p - -host <target>`
      - `naabu --nmap-cli "nmap -sC -sV -A -Pn" -p - -rate 10000 -host <target>`
   - nmap
      - Basic All port `nmap -Pn --min-rate 5000 -T5 -A -sS -sU -p- -oN nmapfull.txt -oX nmapfull.xml <target>`
      - All port with vuln scripts `nmap --script vuln --min-rate 5000 -Pn -p- -T5 -A -oN nmapvuln.txt <target>`
      - Windows AD Specific `nmap -p 53,88,135,139,389,445,464,593,636,3268,3269,3389,5985,9389,49152-65535 --script smb-enum-shares,smb-enum-users,ldap-rootdse,ldap-search,krb5-enum-users,smb-os-discovery,smb-vuln-ms17-010,smb-enum-domains,smb-enum-sessions,smb-enum-processes,smb2-security-mode,smb2-capabilities,smb-system-info,msrpc-enum,smb-brute,rdp-enum-encryption,rdp-vuln-ms12-020,rdp-ntlm-info,ssl-cert,ssl-enum-ciphers,smb-protocols,ms-sql-info,smb-vuln-regsvc-dos -oN nmapAD.txt <target> `


- Domain or IP Recon
   - dig `dig axfr @<ip_address> target.tld`
     
- Wordlist generator
   `cewl http://domain.tld/ | grep -v CeWL > custom-wordlist.txt`

- Subdomain Enumeration
   - Gobuster `gobuster vhost -u http://monitorsthree.htb --append-domain -w /usr/share/seclists/Discovery/DNS/namelist.txt -r`
   - ffuf `ffuf -w /usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'` [For vpn file and ctf]
   - ffuf `ffuf -w /usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://FUZZ.domain.tld` [For Real World]
   - subauto [Use [Hackify](https://github.com/ZishanAdThandar/hackify) to install] `subauto domain.tld` [Very useful for real world subdomain enumeration.]

- BruteForce: ssh, kerbrute or any other service using hydra, medusa or any specific tool like kerbrute etc.

- Check outdated or vulnerable version for any service or software using exploitdb and google

- Default Crecdentials, Check any software or service is using default credential or easy to crack username password






