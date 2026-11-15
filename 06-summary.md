# Summary

## What This Lab Covers
A hands-on walkthrough of attacking Metasploitable 2 from Kali Linux, from initial setup through two confirmed exploits with root access.

## Environment
- Windows laptop, 8 GB RAM, VirtualBox
- Kali Linux 2026.3 (attacker)
- Metasploitable 2 (target)
- Host-Only networking between both VMs

## Vulnerabilities Found & Exploited

| Service | Version | CVE / Module | Result |
|---|---|---|---|
| vsftpd | 2.3.4 | CVE-2011-2523 | Root via Meterpreter |
| UnrealIRCd | 3.2.8.1 | exploit/unix/irc/unreal_ircd_3281_backdoor | Root via Meterpreter |

Both were planted backdoors — confirmed first by Nmap's --script vuln, then exploited with Metasploit.

## Skills Practiced
- VM networking (Host-Only mode) and troubleshooting login/network issues
- Reconnaissance: `ping`, `nmap -sV`
- Vulnerability research: `searchsploit`, `nmap --script vuln`
- Exploitation with Metasploit (RHOSTS, LHOST, payloads)
- Post-exploitation basics: Meterpreter vs. shell commands, `getuid`, `sysinfo`

## Key Takeaways
- Going in, I expected exploitation to be the hard part
- It turned out setup and networking (login issues, DNS crashes, LHOST errors) ate more time than the actual exploits
-  which ran in seconds once the right module was found
-If I did this again, I'd check for DNS/network quirks on Host-Only setups earlier instead of hitting them mid-scan.

## What's Next
- Samba and other remaining services have known exploits (per searchsploit) but weren't confirmed by the vuln scan — a possible future target
- Moving on to Linux fundamentals and Network+ before returning for a deeper round (privilege escalation, pivoting, more services)
