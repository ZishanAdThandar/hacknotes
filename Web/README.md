This note is written to Solve Web Application CTFs, Bug Bounty or Web App Penetration Testing.

Check my [Bug Bounty Hunting Methodology](https://github.com/ZishanAdThandar/pentest/blob/main/notes/BugBountyHuntingMethodology.md) to learn some bonus.

You can use my script [Hackify](https://github.com/ZishanAdThandar/hackify) to install tools and wordlist on your linux system.

- [Installing Tools and Wordlists](#installing-tools-and-wordlists)
- [Recon](#recon)
    - [Basic Recon](#basic-recon)
    - [Subdomain Enumeration](#subdomain-enumeration)
    - [Directory Busting](#directory-busting)
    - [Crawling](#crawling)
    - [Parameter Fuzzing](#parameter-fuzzing)
    - [Common File Checks](#common-file-checks)
    - [Known Vulnerablity in Software or Services](#known-vulnerablity-in-software-or-services)
- [Scanning](#scanning)
    - [CMS Test](#cms-test)
    - [Dorking](#dorking)
    - [Automated Scan](#automated-scan)
    - [One Liners](#one-liners)
- [Manual Testing](#manual-testing)
    - [Manual Methods](#manual-methods)


## Installing Tools and Wordlists
- [HackiFy](https://github.com/ZishanAdThandar/hackify) should be used to install important tools and wordlists.
    ```bash
    git clone https://github.com/ZishanAdThandar/hackify.git
    cd hackify
    chmod +x hackify.sh; bash hackify.sh # tools
    chmod +x wordlist.sh; bash wordlist.sh # wordlist
    ```
- [Top tools list](./notes/TOOLS.md): Remaining tools can be installed manually.
--- 
# Recon 
## Basic Recon
- dig `dig axfr @<ip_address> target.tld`
- nslookup
- whois
  
## Subdomain Enumeration
- Gobuster `gobuster vhost -u http://monitorsthree.htb --append-domain -w /opt/wordlists/SecLists/Discovery/DNS/namelist.txt -r`
- ffuf `ffuf -w /opt/wordlists/SecLists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://domain.tld -H 'Host: FUZZ.domain.tld'` [For vpn file and ctf]
- ffuf `ffuf -w /opt/wordlists/SecLists/Discovery/DNS/dns-Jhaddix.txt:FUZZ -fw 18 -mc all -ac -u http://FUZZ.domain.tld` [For Real World]
- subauto [Use [Hackify](https://github.com/ZishanAdThandar/hackify) to install] `subauto domain.tld` [Very useful for real world subdomain enumeration.]

  
## Directory Busting
- Recursive directory busting `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -ic -recursion -recursion-depth 3 -u https://target.com/FUZZ`
- Directory`ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://target.com/FUZZ/`
- dirsearch `dirsearch -e php,html,txt -t 50 -u http://domain.tld/`
- Files `ffuf -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-files.txt -u https://target.com/FUZZ/`
- `feroxbuster -w /opt/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u http://target.tld/`

## Crawling
- [LinkFinder by GerbenJavado](https://github.com/GerbenJavado/LinkFinder)

## Parameter Fuzzing
- `arjun -u target.tlf=d`
- Burpsuite plugin `parmafinder++`
- webarchive `https://web.archive.org/cdx/search/cdx?url=*.domanin.tld&fl=original&collapse=urlkey`
- [x8 Paramter Discovery](https://github.com/Sh1Yo/x8)
- ffuf

## Common file checks
- `robots.txt`, `secrets.txt` etc file could reveal sensetive information
- use `dirb` to find common files. `dirb http://target.tld`
- Check source code for any sensetive information leak

## Known Vulnerablity in Software or Services
- Searching on Google
- Using searchsploit
- shodan
- censys
- We can also utilize online exploit databases to search for vulnerabilities, like [Exploit DB](https://www.exploit-db.com), [Rapid7 DB](https://www.rapid7.com/db/), or [Vulnerability Lab](https://www.vulnerability-lab.com).

---
# Scanning
## CMS Test
- wpscan `wpscan --url https://domain.tld/wordpress-blog/ -e u,ap --api-token=<API_TOKEN>` Check https://wpscan.com/profile for api token.
- Search for other CMS Scanner and use them on particular CMS
- Known CVE: Check outdated or vulnerable version for any service or software using exploitdb and google.

## Dorking
- [DorkScout](https://github.com/R4yGM/dorkscout): Golang tool to automate google dork scan against the entiere internet or specific targets.
- [pagodo (Passive Google Dork)](https://github.com/opsdisk/pagodo)
- FGDS `curl https://raw.githubusercontent.com/IvanGlinkin/Fast-Google-Dorks-Scan/master/FGDS.sh -s |bash -s domain.com`
- [sitedorks by Zarcolio](https://github.com/Zarcolio/sitedorks)
- [git-hound](https://github.com/tillson/git-hound)
    - Install git-hound with Hackify or from repo release then `which git-hound`
    - Login Details: `nano /root/go/bin/config.yml` Example: https://github.com/tillson/git-hound/blob/main/config.example.yml
    - Entering OTP `git-hound --otp-code 1234568`
    - `git-hound --config-file /root/go/bin/config.yml --subdomain-file subdomains.txt`
 
## Automated Scan
- Burp Suite Pro: with different extensions like [HUNT by BugCrowd](https://github.com/bugcrowd/HUNT). Bug Bounty Pro could be used.
- [nuclei](https://github.com/projectdiscovery/nuclei) with [nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) or external templates
    - nuclei template install (as root): `nuclei -ut`
    - nuclei command: `nuclei -l httpsubdomain.txt -resume nuclei.txt -nmhe` [`rate-limit 10`/second to avoid error of rapid request, `-nmhe` to skip error]
- Acunetix Pro 
    - Creating Acunetix CSV list from https links `for i in $(cat domain.comhttpssubdomain.txt); do echo \"$i\", \" \"; done > domain.comacunetix.csv`
- [Afrog](https://github.com/zan8in/afrog) `afrog -T domain.comhttpsubs.txt`
- [Owasp NetTracker](https://github.com/OWASP/Nettacker) 
- Wapiti [Linux]
- [XAttacker](https://github.com/Moham3dRiahi/XAttacker) `perl XAttacker.pl -l list.txt`
- theharvester
    
## Exploitation Tools
- RCE:  [Commix](https://github.com/commixproject/commix)
- Cross Site Scripting: [XSStrike](https://github.com/s0md3v/XSStrike), [XSSxrapy](https://github.com/DanMcInerney/xsscrapy)
- File inclusion: [LFIMap](https://github.com/hansmach1ne/LFImap), [liffy](https://github.com/mzfr/liffy)
- Fileupload: [fuxploider](https://github.com/almandin/fuxploider) 
- CORS: [Corsy](https://github.com/s0md3v/Corsy) 
- CRLF Injection: [crlfuzz](https://github.com/dwisiswant0/crlfuzz) 
- GraphQL: [batchql by assetnote](https://github.com/assetnote/batchql), [INQL Scanner Burpsuite Extension](https://portswigger.net/bappstore/296e9a0730384be4b2fffef7b4e19b1f) or [INQL Script](https://pypi.org/project/inql/)
- 403 bypass: [bypass-403 by iamj0ker](https://github.com/iamj0ker/bypass-403), [403bypasser by yunemse48](https://github.com/yunemse48/403bypasser), [4-ZERO-3 by Dheerajmadhukar](https://github.com/Dheerajmadhukar/4-ZERO-3) or [403 Bypasser Burpsuite Extension](https://portswigger.net/bappstore/444407b96d9c4de0adb7aed89e826122)
- GF Pattern Commands: [Gf-Patterns](https://github.com/1ndianl33t/Gf-Patterns)


## One Liners
- [Bug Bounty oneliners by thevillagehacker](https://github.com/thevillagehacker/Bug-Hunting-Arsenal/blob/main/Bug%20Bounty%20Tips/files/oneliners.md)
- [Bug Bounty Hunters oneliners by codelively](https://www.codelivly.com/powerful-one-liner-scripts-for-bug-bounty-hunters)

---
# Manual Testing
- Burp Extenders from BApp store or : Turbo Intruder or many others https://github.com/snoopysecurity/awesome-burp-extensions
- Burp BChecks: [BChecks Collection](https://github.com/emadshanab/BChecks-Collection), [PortSwigger BChecks](https://github.com/PortSwigger/BChecks/), Custom BChecks etc
## Manual Methods
- [Login Bypass](./LogInBypass.md)
- [SQL Injection](./SQLInjection.md)





