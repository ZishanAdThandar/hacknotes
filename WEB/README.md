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

- Login Bypass
  - Default Credential
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
  - HTTP Parameter Pollution
  - File Inclusion to access admin panel Directly
  - Exploiting Forgot Password Flow
  - Debug Mode can lead to disclose sensitive info from errors
  - Hardcoded Username Password in source code
  - Session Fixation
  - Token Hijacking
  - Insecure Direct Object References (IDOR)
- Check outdated or vulnerable version for any service or software using exploitdb and google
- Default Crecdentials, Check any software or service is using default credential or easy to crack username password





