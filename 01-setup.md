# 01 - Lab Setup

## Goal
I Built an isolated cybersecurity lab on my laptop using VirtualBox.

## Environment
- Host: Windows laptop, 8 GB RAM
- Hypervisor: VirtualBox
- VM 1: Kali Linux 2026.3 (attacker machine)

## Steps

### 1. Downloaded Kali
I Downloaded the pre-built VirtualBox image for kali Linux from kali.org.

### 2. Extracted the archive
Extracted it with WinRAR (unpacked size about 16.8 GB) into a folder on my drive.
(I recommend having 20 GB of free space)

### 3. Imported into VirtualBox
After downloading, Double-clicked the .vbox file, and Kali appeared in the VM list.

<img width="1917" height="1020" alt="Kali VM on VirtualBox" src="https://github.com/user-attachments/assets/05362273-228c-4fb8-b61c-e860d0a29cc4" />

### 4. Configured the VM
- RAM: 2048 MB
- CPUs: 2
  
  <img width="967" height="650" alt="Kali VM Memory settings" src="https://github.com/user-attachments/assets/d8fe3b8c-9a9a-4aee-acda-a8c5e2c88057" />

- Network: NAT (to allow updates)
  
<img width="977" height="642" alt="Kali VM Network settings" src="https://github.com/user-attachments/assets/c301d37e-3697-432b-aedd-abef5e9ab9fb" />


### 5. First boot and update
Logged in with the default user given by kali, then ran:
```
sudo apt update && sudo apt full-upgrade -y
```
It will start updating and The update takes a few mins 

<img width="1920" height="922" alt="kali VM updating" src="https://github.com/user-attachments/assets/5652a5e4-4fe2-47d5-a1e5-7b6fd4cc903d" />

<img width="1920" height="922" alt="kali desktop after login" src="https://github.com/user-attachments/assets/ed1732c9-2127-4766-9af9-446e3a38a089" />

## Problems I hit
- Two VirtualBox files in the folder: the `.vbox` is the one to open
- `sudo` showed no characters while typing the password (normal in Linux)

## What I learned
- Set up VirtualBox for my homelab, and I found it really fun
- Imported a pre-built kali Linux VM into VirtualBox
- changed the default kali Password with the `passwd` command

## Next
- Take a "Clean Kali" snapshot
- Add Metasploitable 2 as the target
- Switch to a Host-only network
- First nmap scan
