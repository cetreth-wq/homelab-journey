# 03 - Connectivity Test & Service Scan

## Goal
Confirm Kali can reach Metasploitable2 over the network, then enumerate open services.

## Connectivity Test
ping -c 4 <target-ip>
Result: 4/4 packets received, 0% packet loss — confirms both VMs are on the same Host-Only network and can communicate.

## Service Scan
nmap -sV -n <target-ip>
Used -n to skip DNS resolution — without it, Nmap crashed with a resolver assertion error on this Host-Only network (no DNS server present).

Result: 23 open ports, including:
- FTP (vsftpd 2.3.4)
- SSH (OpenSSH 4.7p1)
- Telnet, rexec/rlogin/rsh
- SMTP (Postfix), DNS (BIND 9.4.2)
- HTTP (Apache 2.2.8), Tomcat (8180)
- Samba, NFS, MySQL, PostgreSQL, VNC, IRC (UnrealIRCd)

## Analysis
Old software versions across almost every service, plus several unnecessary services exposed (telnet, rexec, VNC) — a large attack surface, several of which have known backdoors or exploits.

## Screenshots
- ping output

  <img width="1920" height="922" alt="ping output" src="https://github.com/user-attachments/assets/d51be99b-b8c5-46ea-82d8-5bdfd80d2f60" />

- Nmap crashed with a resolver assertion error on this Host-Only network (no DNS server present)


<img width="1920" height="922" alt="nmap crash" src="https://github.com/user-attachments/assets/e5abdad0-278e-41f4-9030-4101eb171be6" />


- full nmap -sV output (usen -n to skip DNS resolution


  <img width="1920" height="922" alt="nmap output" src="https://github.com/user-attachments/assets/cb8aad3e-1ead-475c-8d91-9ffb00e52400" />


## Next
- 04: Vulnerability research (searchsploit, nmap --script vuln) and exploitation
