
# 01 - Lab Setup

## Goal
So I Build an isolated cybersecurity lab on my laptop using VirtualBox.

## Environment
- Host: Windows laptop, 8 GB RAM
- Hypervisor: VirtualBox
- VM 1: Kali Linux 2026.3 (attacker machine)

## Steps

### 1. Downloaded Kali
I Downloaded the pre-built VirtualBox image for kali linux from kali.org.

### 2. Extracted the archive
Extracted it with WinRAR (unpacked size about 16 GB smthg) into a folder on my drive.
(I Recommend to have 20gb of free space in the drive)

### 3. Imported into VirtualBox
After the Download, Double-clicked the .vbox file, and Kali appeared in the VM list.

### 4. Configured the VM
- RAM: 2048 MB
- CPUs: 2
- Network: NAT (to allow updates)

### 5. First boot and update
Logged in with the default user given by kali, then ran:
sudo apt update && sudo apt full-upgrade -y
It will start updating and take few mins

## Problems I hit
- Two VirtualBox files in the folder: the .vbox is the one to open
- sudo showed no characters while typing the password (normal in Linux)

## What I learned
- Downloaded the VirtualBox with the intention of Homelabing which i found soo fun
- Created a Virtual Machine that Runs kali linux
- changed the default Password of kali by using command 'passwd'

## Next
- Take a "Clean Kali" snapshot
- Add Metasploitable 2 as the target
- Switch to a Host-only network
- First nmap scan
