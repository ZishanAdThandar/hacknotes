This note is written to Solve Web Application CTFs, Bug Bounty or Web App Penetration Testing.

Check my [Bug Bounty Hunting Methodology](https://github.com/ZishanAdThandar/pentest/blob/main/notes/BugBountyHuntingMethodology.md) to learn some bonus.

You can use my script [Hackify](https://github.com/ZishanAdThandar/hackify) to install tools and wordlist on your linux system.

- [Basic Recon](#basic-recon)
- [Basic Automation](#basic-recon-automation)
- [Subdomain Enumeration](#subdomain-enumeration)
- [Directory Busting](#directory-busting)
- [CMS Test](#cms-test)
- [Parameter Fuzzing](#parameter-fuzzing)
- [Login Bypass](#login-bypass)

## Basic Recon
- dig `dig axfr @<ip_address> target.tld`
- nslookup
- whois
  
## Subdomain Enumeration
- Gobuster ```gobuster vhost -u http://monitorsthree.htb --append-domain -w /opt/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -r```
- ffuf ```ffuf -w /opt/wordlists/SecLists/Discovery/DNS/namelist.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'```
- subauto [Use [Hackify](https://github.com/ZishanAdThandar/hackify) to install] `subauto domain.tld` [Mainly for real world subdomain enumeration.]

## Basic Automation
- nikto
- theharvester
- wapiti
- afrog
- nuclei
- acunetix
  
## Directory Busting
- DIRB `dirb https://target.com/`
- Recursive directory busting `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -ic -recursion -recursion-depth 3 -u https://target.com/FUZZ`
- Directory`ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://target.com/FUZZ/`
- Files `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt -u https://target.com/FUZZ/`

## CMS Test
- wpscan `wpscan --url https://domain.tld/wordpress-blog/ -e u,ap --plugin-detection aggresive --api-token=<API_TOKEN>`
- Search for other CMS Scanner and use them on particular CMS
- Known CVE: Check outdated or vulnerable version for any service or software using exploitdb and google.

## Parameter Fuzzing
- Paramter ``` ```

## Login Bypass
- Default Credential: Search on search engines for platform or CMS specific credentials
- Credential Stuffing
 - Using same username password from another place
 - Look for username password in the app
- SQL Injection
- NoSQL Injection
- Forced Browsing (Unprotected Admin Panels): Directory busting will show unprotected panels
- No Redirect
- Exploiting known CVE to bypass login for particular Software
- Bruteforce: Hydra, Burpsuite
 - Wordlist
   - Wordlist Generator `cewl http://domain.tld/ | grep -v CeWL > custom-wordlist.txt`
   - Known Wordlist: rockyou, SecLists
- Social Engineering: Cross Site Scripting Cookie Theft, Phishing, Pretexting etc
- Cookie Poisoning: `admin=True`, `roll=admin` etc.
- HTTP Parameter Pollution: e.g. `username=admin&username=attacker&password=123456`
- File Inclusion to access admin panel Directly: e.g. `http://target.com/file=http://127.0.0.1:3000/admin/dashboard.php` 
- Exploiting Forgot Password Flow
- Debug Mode can lead to disclose sensitive info from errors
- Hardcoded Username Password in source code
- Session Fixation
- Token Hijacking
- Insecure Direct Object References (IDOR): e.g. `GET /user/profile?userid=124`






