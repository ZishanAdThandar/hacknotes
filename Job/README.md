- [Job Hunting](#job-hunting)
- [CV](#cv)
- [Interview Prerequisites](#interview-prerequisites)
  - [Interview Preparation Guide](#interview-preparation-guide)
  - [Communication Tips](#communication-tips)
  - [Practical Interview Preparation](#practical-interview-preparation)
  - [Additional Tips](#additional-tips)
- [Topics to learn](#topics-to-learn)
- [Practical Prep for Cybersecurity Interviews](#practical-prep-for-cybersecurity-interviews)
- [Interview Question Answers](#interview-question-answers)

## Job Hunting
- LinkedIn
  - Search using LinkedIn Job Search with filters
  - Search using Post Search with filters
- [NinjaJobs.org](https://ninjajobs.org)
- Company Career Pages
  - Google dork for random companies
  - find in top companies.
    - [TryHackMe](https://careers.tryhackme.com/)
    - [HackTheBox](https://jobs.hackthebox.com/)
- Country based Job Platforms: Find jobs on job search sites of particular region
- Referal or Networks
  - Ask for referal via people in social media platforms like LinkedIn, facebook etc.
  - Chat servers like discord, facebook groups, telegram groups etc.

## CV
- [Sample CV](https://zishanadthandar.github.io/CV.pdf)    
- [Latex code for CV](./CVLatext.tex)

# Interview
## Interview Prerequisites
- ### **Interview Preparation Guide**
  - Ensure a quiet, distraction-free environment without background noise. 
  - Use a high-quality microphone, earphones, and camera for optimal communication.
  - Inform family members or roommates in advance to avoid interruptions. 
    - In case of an interruption, stay calm:
      - Politely ignore it or ask for pardon from the interviewers.
      - Gently request others to remain silent if needed.
- ### **Communication Tips**
  - **Market yourself confidently:** Don't hesitate to showcase your skills and achievements.
  - **Speak gently and calmly:** Maintain a slow and clear pace with a positive smile.
  - **Relax about linguistic errors:** Don't worry too much about minor mistakes in grammar or language.
  - **Engage actively:** Listen attentively and respond thoughtfully to questions.
- ### **Practical Interview Preparation**
  - Verify that your PC is functioning properly:
    - Ensure all hardware and peripherals are in working order.
    - Test your internet connection for stability.
  - Close unnecessary applications to optimize system performance.
  - Pre-install, configure, and test any tools or environments you may need:
    - Ensure you have all pentesting tools (e.g., Burp Suite, Nmap, Metasploit) ready.
    - Confirm access to virtual machines or labs if required.
  - Keep a backup system ready in case of technical issues.
- ### **Additional Tips**
  - **Practice common questions:** Review potential technical and behavioral questions beforehand.
  - **Take notes:** Keep a pen, notebook, or digital notes handy for key points during the discussion.
  - **Be punctual:** Join the interview a few minutes early to show professionalism.
  - **Follow up:** Send a polite thank-you email after the interview to leave a positive impression.

## Topics to learn
### 1. Fundamentals of Cybersecurity
- CIA Triad (Confidentiality, Integrity, Availability)
- Security Controls (Preventive, Detective, Corrective)
- Authentication, Authorization, and Accounting (AAA)
- Risk Assessment & Management
### 2. Networking & Protocols
- OSI & TCP/IP Model
- Common Protocols (HTTP(S), FTP, SSH, DNS, SMTP, etc.)
- Firewalls, VPNs, IDS/IPS, and Proxies
- Subnetting, VLANs, NAT, and Packet Analysis (Wireshark)
### 3. Web Application Security
- OWASP Top 10 Vulnerabilities (SQL Injection, XSS, CSRF, SSRF, etc.)
- Web Pentesting Methodologies
- HTTP Headers and Cookies Security
- API Security (JWT, OAuth, Rate Limiting, API Pentesting)
### 4. System Security
- Windows & Linux Security (File Permissions, Logging, Hardening)
- Active Directory Security (LDAP, Kerberos, NTLM)
- Privilege Escalation (Windows & Linux)
- Malware Analysis & Reverse Engineering Basics
### 5. Penetration Testing & Exploitation
- Reconnaissance (OSINT, Nmap, Shodan, Google Dorking)
- Vulnerability Scanning (Nessus, OpenVAS)
- Exploitation Techniques (Buffer Overflow, RCE, LFI/RFI, Shellcode)
- Post-Exploitation & Lateral Movement
### 6. Cryptography & Secure Communication
- Hashing vs. Encryption (MD5, SHA, AES, RSA, ECC)
- Digital Certificates, PKI, and SSL/TLS
- Secure Coding Practices
### 7. Cloud & DevSecOps Security
- AWS, Azure, and GCP Security (IAM, S3, Security Groups)
- Container Security (Docker, Kubernetes)
- CI/CD Pipeline Security
### 8. Threat Intelligence & Incident Response
- Cyber Kill Chain & MITRE ATT&CK Framework
- SIEM & Log Analysis (Splunk, ELK)
- Digital Forensics (Memory, Disk, Network Forensics)
- Incident Handling & Response Plans
### 9. Certifications & Hands-on Labs
- OSCP, CRTP, CEH, CISSP (Certification-Oriented Questions)
- Hack The Box, TryHackMe, CTFs (Hands-on Practice)

## Practical Prep for Cybersecurity Interviews
- Red Team
  - Tools: Nmap, Shodan, theHarvester, Amass, Burp Suite, OWASP ZAP, SQLmap, Wfuzz, Gobuster, Metasploit, Impacket, CrackMapExec, Mimikatz, LinPEAS, WinPEAS, AWS CLI, Postman, JWT Toolkit
  - Bug Categories: SQLi, XSS, CSRF, SSRF, RCE, JWT Tampering, AD Attacks, Pass-the-Hash, Kerberoasting, Lateral Movement, S3 Misconfigs, IAM Issues
  - Practice Platforms: TryHackMe, Hack The Box, VulnHub, PortSwigger Academy
- Blue Team
  - Tools:Wireshark, Suricata, Zeek, Splunk, ELK, Velociraptor, Sysmon
  - Bug Categories: Phishing, Log Tampering, Malware Analysis, Threat Hunting, AD Attacks, Lateral Movement
  - Practice Platforms: Blue Team Labs Online, Splunk Boss of the SOC, LetsDefend



## Interview Question Answers
- General Interview
- Technical Assessment
  - Online Test  
    - Multiple-Choice Questions
    - Tools: Burp Suite, Wireshark, Metasploit, Nmap, IDS/IPS concepts, Splunk, Wazuh
    - Knowledge of ISO 27001, GDPR, NIST, and OWASP Top 10 may be tested.
    - Candidates are given a vulnerable machine or website to exploit.
  - CTF Challenge
    - Web Exploitation (SQLi, XSS, SSRF)
    - Reverse Engineering (basic CrackMe)
    - Privilege Escalation (Linux/Windows)
    - Network Pentesting
    - Platforms: Hack The Box, TryHackMe, CyberTalents, PicoCTF, portswiggerlabs
- Techinical Round Thoery
  - Core Cybersecurity Concepts
  - Practical & Scenario-Based Questions
- HR Round
  - General questions on teamwork, problem-solving, and company fit
  - Possible salary negotiation discussions
- Final Managerial / Offer Discussion (Optional)
  - For Senior Roles (Security Engineer, Architect, Manager, etc.)
  - Handling incident response scenarios
  - Experience in compliance, risk management, security architecture


