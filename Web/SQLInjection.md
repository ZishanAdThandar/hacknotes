# SQL Injection

- [Common Weakness Enumeration by Mitre Corporation](#common-weakness-enumeration-by-mitre-corporation)  
- [Types of SQL Injection](#types-of-sql-injection)
- [Types of Databases](#types-of-databases)
- [Manual SQLi Method](#manual-sqli-method)
  - [Checking SQLi Vulnerablity](#checking-sqli-vulnerablity)
  - 
- [Top WAF Bypass Methods](#top-waf-bypass-methods)
- [SQL Injection Automation Tools](#sql-injection-automation-tools)
- [Practice Labs](#practice-labs)
- [Resources and Notes](#resources-and-notes)

## Common Weakness Enumeration by Mitre Corporation
- CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')
- CWE-94: Improper Control of Generation of Code ('Code Injection')
- CWE-116: Improper Encoding or Escaping of Output
- CAPEC-66: SQL Injection

## Types of SQL Injection
- SQLi Categories  
  - In-Band SQLi (Direct Interaction with Database)  
    - Error-Based SQLi (Error Message Exploitation, **EBSqli**)  
    - Union-Based SQLi (Using `UNION SELECT` to Extract Data, **UBSqli**)  
  - Blind SQLi (No Direct Output)  
    - Boolean-Based Blind SQLi (True/False Responses, **BBSqli**)  
    - Time-Based Blind SQLi (Response Delay Exploitation, **TBSqli**)  
  - Out-of-Band SQLi (External Communication Exploitation, **OOB Sqli**)  
    - DNS-Based SQLi (Exfiltrating Data via DNS Requests, **DNS-Sqli**)  
    - HTTP-Based SQLi (Using HTTP Requests for Exfiltration, **HTTP-Sqli**)  
    - SMB-Based SQLi (Leaking Data via SMB Protocol, **SMB-Sqli**)  
    - FTP-Based SQLi (Exploiting FTP Connections for Data Theft, **FTP-Sqli**)  

- Order-Based SQLi (Execution Timing Matters)  
  - First-Order SQLi (Immediate Execution, **FOSqli**)  
  - Second-Order SQLi (Stored and Later Triggered, **SOSqli**)  

- Data-Type Based SQLi (Input Type Matters)  
  - String-Based SQLi (Injecting SQL Through String Input, **SBSqli**)  
  - Integer-Based SQLi (Injecting SQL in Numeric Fields, **IBSqli**)  

- Context-Specific SQLi (Location-Specific Exploits)  
  - Login Form SQLi (Bypassing Authentication)  
  - Search Query SQLi (Exploiting User Search Inputs)  
  - Header-Based SQLi (Injecting SQL in `User-Agent`, `Referer`)  
  - Cookie-Based SQLi (Tampering Cookies for Injection)  
  - Stored SQLi (Persisted Injection for Future Execution)  
  - XML SQLi (Injecting SQL Through XML Data, **XXE-Sqli**)  

- Advanced SQLi Techniques (Specialized & Evasive Techniques)  
  - Batch SQLi (Executing Multiple Queries in One Request)  
  - Stacked Queries SQLi (Executing Multiple Statements, **Stacked-Sqli**)  
  - WAF Bypass SQLi (Evading Security Filters via Encoding & Obfuscation)  
  - XOR-Based SQLi (Using XOR Logic for Bypassing Filters, **XOR-Sqli**)  
  - Hybrid SQLi (Combining Multiple SQLi Techniques for Stronger Attacks)  
  - Automated SQLi (Using Tools like SQLmap for Automated Exploitation)  

## Types of Databases
Payloads and exploitation method will vary by database type.
There are ten major types of SQL databases,
- MySQL
- MSSQL (Microsoft SQL Server)
- Oracle Database
- PostgreSQL
- MariaDB
- SQLite
- IBM Db2
- Sybase (SAP ASE)
- Firebird
- CockroachDB

## Manual SQLi Method
### Checking SQLi Vulnerablity 
#### Error Based and Union Based
```SQL
'  
"  
' --  
" --  
' #  
" #  
' /*  
" /*  
```
or encodings of them will give SQL error.
#### Boolean Based
#### Time Based
#### Identifying SQL version


## Top WAF Bypass Methods
- Encoding (Hex, Base64, URL encoding, Unicode)
- Case Changing (UnIoN SeLeCt instead of UNION SELECT)
- Comments (--, #, /**/ to obfuscate queries)
- Concatenation (CONCAT(), ||, +, UNION ALL SELECT ''||'payload')
- HTTP Header Injection (X-Forwarded-For, User-Agent, Referer)
- Escaping & Special Characters (\, \x00, %00, NULL bytes)
- Whitespace Manipulation (/**/, TAB, NEWLINE tricks)
- Time Delays (SLEEP(), pg_sleep(), WAITFOR DELAY)
- Case-Sensitive Function Call Variations (SeLeCt(), uNiOn())

## SQL Injection Automation Tools
1. SQLMAP
2. JQL Injection
3. Havij (Outdated)
   
## Practice Labs
- [PortSwiggerLab Labs](https://portswigger.net/web-security/all-labs#sql-injection)
- [VulnWeb by acunetix](http://vulnweb.com/)

## Resources and Notes
- [Advnaced SQL Injection Cheatsheet](https://github.com/kleiton0x00/Advanced-SQL-Injection-Cheatsheet) Proper Notes with payloads by each SQL Database and SQLi type
- [PortSwiggerLab](https://portswigger.net/web-security/sql-injection#what-is-sql-injection-sqli)




