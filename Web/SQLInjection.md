# SQL Injection

- [](#)

## Types of SQL Injection
- SQL Injection Categories  
  - In-Band SQL Injection (Direct Interaction with Database)  
    - Error-Based SQL Injection (Error Message Exploitation, **EBSqli**)  
    - Union-Based SQL Injection (Using `UNION SELECT` to Extract Data, **UBSqli**)  
  - Blind SQL Injection (No Direct Output)  
    - Boolean-Based Blind SQL Injection (True/False Responses, **BBSqli**)  
    - Time-Based Blind SQL Injection (Response Delay Exploitation, **TBSqli**)  
  - Out-of-Band SQL Injection (External Communication Exploitation)  
    - DNS-Based SQL Injection (Exfiltrating Data via DNS Requests, **DNS-Sqli**)  
    - HTTP-Based SQL Injection (Using HTTP Requests for Exfiltration, **HTTP-Sqli**)  
    - SMB-Based SQL Injection (Leaking Data via SMB Protocol, **SMB-Sqli**)  
    - FTP-Based SQL Injection (Exploiting FTP Connections for Data Theft, **FTP-Sqli**)  

- Order-Based SQL Injection (Execution Timing Matters)  
  - First-Order SQL Injection (Immediate Execution, **FOSqli**)  
  - Second-Order SQL Injection (Stored and Later Triggered, **SOSqli**)  

- Data-Type Based SQL Injection (Input Type Matters)  
  - String-Based SQL Injection (Injecting SQL Through String Input, **SBSqli**)  
  - Integer-Based SQL Injection (Injecting SQL in Numeric Fields, **IBSqli**)  

- Context-Specific SQL Injection (Location-Specific Exploits)  
  - Login Form SQL Injection (Bypassing Authentication)  
  - Search Query SQL Injection (Exploiting User Search Inputs)  
  - Header-Based SQL Injection (Injecting SQL in `User-Agent`, `Referer`)  
  - Cookie-Based SQL Injection (Tampering Cookies for Injection)  
  - Stored SQL Injection (Persisted Injection for Future Execution)  
  - XML SQL Injection (Injecting SQL Through XML Data, **XXE-Sqli**)  

- Advanced SQL Injection Techniques (Specialized & Evasive Techniques)  
  - Batch SQL Injection (Executing Multiple Queries in One Request)  
  - Stacked Queries SQL Injection (Executing Multiple Statements, **Stacked-Sqli**)  
  - WAF Bypass SQL Injection (Evading Security Filters via Encoding & Obfuscation)  
  - XOR-Based SQL Injection (Using XOR Logic for Bypassing Filters, **XOR-Sqli**)  
  - Hybrid SQL Injection (Combining Multiple SQLi Techniques for Stronger Attacks)  
  - Automated SQL Injection (Using Tools like SQLmap for Automated Exploitation)  

## Identifying SQL 
## Identifying SQL version




