This note is written to Solve Web Application CTFs, Bug Bounty or Web App Penetration Testing.

Check my [Bug Bounty Hunting Methodology](https://github.com/ZishanAdThandar/pentest/blob/main/notes/BugBountyHuntingMethodology.md) to learn some bonus.

You can use my script [Hackify](https://github.com/ZishanAdThandar/hackify) to install tools and wordlist on your linux system.

- [Basic Recon](#basic-recon)
- [Basic Automation](#basic-recon-automation)
- [Subdomain Enumeration](#subdomain-enumeration)
- [Directory Busting](#directory-busting)
- [Crawling](#crawling)
- [CMS Test](#cms-test)
- [Parameter Fuzzing](#parameter-fuzzing)
- [Login Bypass](#login-bypass)

## Basic Recon
- dig `dig axfr @<ip_address> target.tld`
- nslookup
- whois
  
## Subdomain Enumeration
- Gobuster `gobuster vhost -u http://monitorsthree.htb --append-domain -w /opt/wordlists/SecLists/Discovery/DNS/namelist.txt -r`
- ffuf `ffuf -w /opt/wordlists/SecLists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'` [For vpn file and ctf]
- ffuf `ffuf -w /opt/wordlists/SecLists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://FUZZ.domain.tld` [For Real World]
- subauto [Use [Hackify](https://github.com/ZishanAdThandar/hackify) to install] `subauto domain.tld` [Very useful for real world subdomain enumeration.]

## Basic Automation
- nikto
- theharvester
- wapiti
- afrog
- nuclei
- acunetix
  
## Directory Busting
- feroxbuster -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-medium-directories.txt -u http://target.tld/
- Recursive directory busting `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -ic -recursion -recursion-depth 3 -u https://target.com/FUZZ`
- Directory`ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://target.com/FUZZ/`
- Files `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt -u https://target.com/FUZZ/`

## Crawling


## CMS Test
- wpscan `wpscan --url https://domain.tld/wordpress-blog/ -e u,ap --plugin-detection aggresive --api-token=<API_TOKEN>`
- Search for other CMS Scanner and use them on particular CMS
- Known CVE: Check outdated or vulnerable version for any service or software using exploitdb and google.

## Parameter Fuzzing
- `arjun -u target.tlf=d`
- Burpsuite plugin `parmafinder++`
- webarchive `https://web.archive.org/cdx/search/cdx?url=*.domanin.tld&fl=original&collapse=urlkey`
- ffuf

## Common file checks
- `robots.txt`, `secrets.txt` etc file could reveal sensetive information
- use `dirb` to find common files. `dirb http://target.tld`
- Check source code for any sensetive information leak

## search for vulnerablity in Software or Services
- Searching on Google
- Using searchsploit
- shodan
- censys
We can also utilize online exploit databases to search for vulnerabilities, like [Exploit DB](https://www.exploit-db.com), [Rapid7 DB](https://www.rapid7.com/db/), or [Vulnerability Lab](https://www.vulnerability-lab.com).

## Manual Methods

- [Login Bypass](./LogInBypass.md)
- [SQL Injection](./SQLInjection.md)





