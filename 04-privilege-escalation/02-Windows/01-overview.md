# Privilege Escalation

## Guides

* [Windows Privilege Escalation Guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
* [PayloadsAllTheThings/Windows - Privilege Escalation.md at master · swisskyrepo/PayloadsAllTheThings · GitHub](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md)
* [GitHub - frizb/Windows-Privilege-Escalation: Windows Privilege Escalation Techniques and Scripts](https://github.com/frizb/Windows-Privilege-Escalation)
* [Windows elevation of privileges](https://guif.re/windowseop)
* [GitHub - SecWiki/windows-kernel-exploits: windows-kernel-exploits   Windows平台提权漏洞集合](https://github.com/SecWiki/windows-kernel-exploits)
* [GitHub - WindowsExploits/Exploits: Windows Exploits](https://github.com/WindowsExploits/Exploits)

## Related

* [LOLBAS](https://lolbas-project.github.io)
* [GitHub - hfiref0x/UACME: Defeating Windows User Account Control](https://github.com/hfiref0x/UACME)
* [PowerSploit](/04-privilege-escalation/02-windows/03-power-sploit.md)
* [JAWS](/04-privilege-escalation/02-windows/05-jaws.md)
* [Juicy Potato, Rotten Potato (NG)](/04-privilege-escalation/02-windows/04-juicy-potato-rotten-potato.md) 
* [Mimikatz](/04-privilege-escalation/02-windows/02-mimikatz.md)
* [SILENTTRINITY](/04-privilege-escalation/02-windows/07-silenttrinity.md)
* [Empire](/04-privilege-escalation/02-windows/06-empire.md)

## Manual

Current users privs
```cmd
whoami /priv
```

List users/details
```cmd
net users
net user <username>
```

List other logged in users
```cmd
qwinsta
query session
```

List user groups
```cmd
net localgroup
net localgroup <groupname>
```

System info
```cmd
systeminfo
systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
hostname
```

Patch level
```cmd
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

Network connections
```cmd
netstat -ano
```

Scheduled tasks
```cmd
schtasks
schtasks /query /fo LIST /v
```

Driver
```cmd
driverquery
```

Installed software (slow)
```cmd
wmic product get name,version,vendor
```

Alternative
```cmd
wmic service list brief
```

Services
```cmd
sc query
```

Antivirus
```cmd
sc query windefend
sc queryex type=service
```

Searching files
```cmd
findstr /si <term> <ext>
findstr /si password *.txt
```

### DLL hijacking

Find a program with a missing dll, or make use for search path order, to execute your own dll.

### Unquoted service path

Finding unqoated service paths
```cmd
wmic service get name,displayname,pathname,startmode
```

```cmd
sc qc <service>
```

Check if we have write permission in a suitable path.
```cmd
.\accesschk64.exe /accepteula -uwdq <path>
```

## PowerShell

### SMB

Mount smb share
```powershell
New-PSDrive -Name "<share-name>" -PSProvider "FileSystem" -Root "\\<ip>\<smb-share>"
```

Access with
```powershell
cd <share-name>:
```

## Automated

### Exploit Suggester

> This tool compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target. It also notifies the user if there are public exploits and Metasploit modules available for the missing bulletins.  
[GitHub - AonCyberLabs/Windows-Exploit-Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)
[Windows Exploit Suggester - Next Generation (WES-NG)](https://github.com/bitsadmin/wesng)

```bash
windows-exploit-suggester.py –update
windows-exploit-suggester.py --database 2021-09-21-mssb.xls --systeminfo sysinfo_output.txt
```

### winPEAS

[winPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS)

```cmd
winpeas.exe > <output-file>
```

### PowerSploit

[PowerSploit](/04-privilege-escalation/02-windows/03-power-sploit.md)

### JAWS

[JAWS](/04-privilege-escalation/02-windows/05-jaws.md)

### Watson
> Enumerate missing KBs and suggest exploits for useful Privilege Escalation vulnerabilities  
[GitHub - rasta-mouse/Watson](https://github.com/rasta-mouse/Watson)

```
Watson.exe
```

### Seatbelt
> Seatbelt is a C# project that performs a number of security oriented host-survey "safety checks" relevant from both offensive and defensive security perspectives.  
[GitHub - GhostPack/Seatbelt](https://github.com/GhostPack/Seatbelt)

```
Seatbelt.exe all
```

### Sherlock
> Deprecated. Have a look at  [Watson](https://github.com/rasta-mouse/Watson)  instead.  

> PowerShell script to quickly find missing software patches for local privilege escalation vulnerabilities.  
[GitHub - rasta-mouse/Sherlock](https://github.com/rasta-mouse/Sherlock)

```
Sherlock.ps1
FindAllVulns
```

## Misc

### File inside a file

```
dir /r
powershell (Get-Content hm.txt -Stream root.txt)
```

### Run as

```
runas /netonly /user:<user> cmd
```

### Weak services

Replace files/programs running with SYSTEM permissions with exploited ones  
-> Check permissions `icacls <file>`
