## Login Bypass
- Default Credential: Search on search engines for platform or CMS specific credentials
- Credential Stuffing
 - Using same username password from another place
 - Look for username password in the app
 - Look username password in source code, encoded, or hidden stegnography etc.
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




