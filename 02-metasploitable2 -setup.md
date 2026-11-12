# 02 - Metasploitable 2 Setup

## Goal
Get Metasploitable 2 running as a target VM and confirm Kali can reach it.

## VM Configuration
- Type: Linux / Ubuntu (32-bit)
- RAM: 8 GB
- Disk: existing Metasploitable.vmdk attached under Storage
- Network: Host-Only Adapter (same network as Kali)

## Steps
1. Created a new VM in VirtualBox and attached the existing .vmdk disk.
2. Booted the VM and reached the login screen.
3. Logged in with the default credentials (msfadmin / msfadmin).
4. Switched both VMs to Host-Only networking.
5. Checked the IP address with ifconfig.
   

## Network Details
| Machine | IP address |
|---|---|
| Kali | 192.168.56.102 |
| Metasploitable 2 | 192.168.56.101 |

## Screenshots
- login screen

  <img width="720" height="400" alt="Metasploit login screen" src="https://github.com/user-attachments/assets/fd3b24d8-0b71-400e-8309-8fed9c494054" />

- ifconfig output

<img width="720" height="400" alt="ip add" src="https://github.com/user-attachments/assets/da12b078-de49-4a70-92f7-73cc52b6bd10" />

- VirtualBox network settings

  <img width="970" height="652" alt="metasploit network settings" src="https://github.com/user-attachments/assets/a81d777c-747e-4ca3-8517-d051b218eb02" />


## Snapshot
- Took a "Clean Metasploitable" snapshot after setup.

## What I Learned
- Metasploitable 2 is intentionally vulnerable, so it has to stay on an isolated Host-only network
- since it's Host-only networking so it won't be exposed to the Internet or my Home network
- snapshots let me break things and roll back, so I can practice safely

## Next
- 03: Connectivity test and Nmap scan
