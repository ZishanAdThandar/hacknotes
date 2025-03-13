# SQL Injection

- [Common Weakness Enumeration by Mitre Corporation](#Common-Weakness-Enumeration-by-Mitre-Corporation)
- [Types of SQL Injection](#types-of-sql-injection)
- 

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

## Identifying SQL 
## Identifying SQL version




