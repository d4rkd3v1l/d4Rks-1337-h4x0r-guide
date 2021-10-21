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
* [PowerSploit](04-privilege-escalation/02-windows/03-power-sploit.md)
* [JAWS](04-privilege-escalation/02-windows/05-jaws.md)
* [Juicy Potato, Rotten Potato (NG)](04-privilege-escalation/02-windows/04-juicy-potato-rotten-potato.md) 
* [Mimikatz](04-privilege-escalation/02-windows/02-mimikatz.md)
* [SILENTTRINITY](04-privilege-escalation/02-windows/07-silenttrinity.md)
* [Empire](04-privilege-escalation/02-windows/06-empire.md)

## Exploit Suggester

> This tool compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target. It also notifies the user if there are public exploits and Metasploit modules available for the missing bulletins.  
[GitHub - AonCyberLabs/Windows-Exploit-Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)

## PowerShell

### SMB

mount smb share
```powershell
New-PSDrive -Name "<share-name>" -PSProvider "FileSystem" -Root "\\<ip>\<smb-share>"
```

access with
```powershell
cd <share-name>:
```

## Tools

### PowerSploit

[PowerSploit](04-privilege-escalation/02-windows/03-power-sploit.md)

### JAWS

[JAWS](04-privilege-escalation/02-windows/05-jaws.md)

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
replace files/programs running with SYSTEM permissions with exploited ones
-> check permissions `icacls <file>`
