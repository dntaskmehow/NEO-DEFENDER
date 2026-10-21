# **NEO-DEFENDER - A MICROSOFT DEFENDER BYPASS FRAMEWORK**
## ZERO-DAY PRIVILEGE ESCALATION SYSTEM

> Researcher: dontaskmehow

> CVE-2026-33825 | Defender LPE | SYSTEM Escalation

[![Status](https://img.shields.io/badge/Status-Weaponized-red)](https://github.com/Bitcoinjimmy/NEFENDER)
[![Target](https://img.shields.io/badge/Target-Microsoft_Defender-blue)](https://github.com/Bitcoinjimmy/NEFENDER)
[![Impact](https://img.shields.io/badge/Impact-Local_Privilege_Escalation-orange)](https://github.com/Bitcoinjimmy/NEFENDER)

`NEO-DEFENDER` is a weaponized local privilege escalation framework targeting Microsoft Defender through a re-weaponized version of CVE-2026-33825.
It abuses insufficient access control granularity and a race condition in Defender’s service control manager interactions to escalate execution from a standard user to `NT AUTHORITY\SYSTEM`.

> Bypasses Defender’s token isolation to elevate from Standard User → NT AUTHORITY\SYSTEM.
Exploits CWE-1220 (Improper Access Control) via a race condition in Defender’s service control manager (SCM) interactions.
Requires no user interaction (CVSS: AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H).

----------------------------------------

## / SYS-ESCALATION / THREAT OVERVIEW

This framework is engineered to:

- bypass Defender token isolation
- elevate privileges from Standard User → `SYSTEM`
- exploit improper access control (CWE-1220)
- trigger a local privilege escalation without user interaction

Severity profile:

- Attack Vector: Local
- Complexity: Low
- Privileges Required: Low
- User Interaction: None
- Scope: Unchanged
- Confidentiality: High
- Integrity: High
- Availability: High

----------------------------------------

## / CORE PAYLOADS /

### 1. PowerShell Exploit
`neo_defender_lpe.ps1`

A weaponized LPE exploit designed to abuse the CVE-2026-33825 flaw and establish `SYSTEM`-level execution.

Run:
```powershell
powershell -ep bypass -f neo_defender_lpe.ps1```

The framework includes:

PowerShell Exploit (neo_defender_lpe.ps1) – Weaponized LPE exploit.
JavaScript Payload (neo_defender_bypass.js) – Persistence and post-exploitation.


## POWERSHELL EXPLOIT: neo_defender_lpe.ps1

```(Save as neo_defender_lpe.ps1 and execute with: powershell -ep bypass -f neo_defender_lpe.ps1)```



## JAVASCRIPT PAYLOAD: neo_defender_bypass.js

```(Deployed post-LPE for persistence and C2. Save as neo_defender_bypass.js and execute with: node neo_defender_bypass.js)```



## EXPLOIT WORKFLOW

Execute neo_defender_lpe.ps1
Exploits CVE-2026-33825 to elevate privileges to NT AUTHORITY\SYSTEM.
Drops a temporary payload to verify LPE success.

Deploy neo_defender_bypass.js
Bypasses Defender’s real-time protection via API unhooking.
Establishes persistence (registry + scheduled task).
Connects to C2 for command execution.

