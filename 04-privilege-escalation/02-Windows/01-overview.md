# Privilege Escalation
- - - -
## Guides
[Windows Privilege Escalation Guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
[PayloadsAllTheThings/Windows - Privilege Escalation.md at master · swisskyrepo/PayloadsAllTheThings · GitHub](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md)
[GitHub - frizb/Windows-Privilege-Escalation: Windows Privilege Escalation Techniques and Scripts](https://github.com/frizb/Windows-Privilege-Escalation)

[Windows elevation of privileges](https://guif.re/windowseop)


[GitHub - SecWiki/windows-kernel-exploits: windows-kernel-exploits   Windows平台提权漏洞集合](https://github.com/SecWiki/windows-kernel-exploits)
[GitHub - WindowsExploits/Exploits: Windows Exploits](https://github.com/WindowsExploits/Exploits)

- - - -
## Related
[LOLBAS](https://lolbas-project.github.io)
[GitHub - hfiref0x/UACME: Defeating Windows User Account Control](https://github.com/hfiref0x/UACME)
[PowerSploit](bear://x-callback-url/open-note?id=CD394257-02D0-4336-BC54-10F93C78DE37-524-00001A2EAF20362A)
[JAWS](bear://x-callback-url/open-note?id=E913BD5A-B7A6-45F9-BF7B-B8EBF8EBB674-576-00001011F8116580)
[JuicyPotato / RottenPotato(NG)](bear://x-callback-url/open-note?id=BA89C137-FF98-4AC4-AF04-B45B11729265-615-000062A9E6D1C4CB)
[SILENTTRINITY](bear://x-callback-url/open-note?id=C43353CE-40F3-4F3E-AA43-B52E92DEFE8A-524-00001A24E33BFEFC)
[Empire](bear://x-callback-url/open-note?id=4E37E590-28E3-4C96-B0C3-7656C769F037-524-00001B6FB21FD0EF)

- - - -
## Exploit Suggester
> This tool compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target. It also notifies the user if there are public exploits and Metasploit modules available for the missing bulletins.  
[GitHub - AonCyberLabs/Windows-Exploit-Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)

- - - -
## PowerShell
### SMB
mount smb share
`New-PSDrive -Name "<share-name>" -PSProvider "FileSystem" -Root "\\<ip>\<smb-share>"`

access with
`cd <share-name>:`

- - - -
## Tools
### PowerSploit
[PowerSploit](bear://x-callback-url/open-note?id=CD394257-02D0-4336-BC54-10F93C78DE37-524-00001A2EAF20362A)

### JAWS
[JAWS](bear://x-callback-url/open-note?id=E913BD5A-B7A6-45F9-BF7B-B8EBF8EBB674-576-00001011F8116580)

### Watson
> Enumerate missing KBs and suggest exploits for useful Privilege Escalation vulnerabilities  
[GitHub - rasta-mouse/Watson](https://github.com/rasta-mouse/Watson)

`Watson.exe`

### Seatbelt
> Seatbelt is a C# project that performs a number of security oriented host-survey "safety checks" relevant from both offensive and defensive security perspectives.  
[GitHub - GhostPack/Seatbelt](https://github.com/GhostPack/Seatbelt)

`Seatbelt.exe all`

### Sherlock
> Deprecated. Have a look at  [Watson](https://github.com/rasta-mouse/Watson)  instead.  

> PowerShell script to quickly find missing software patches for local privilege escalation vulnerabilities.  
[GitHub - rasta-mouse/Sherlock](https://github.com/rasta-mouse/Sherlock)

`Sherlock.ps1`
`FindAllVulns`

- - - -
## Misc
### file inside a file
`dir /r`
`powershell (Get-Content hm.txt -Stream root.txt)`

### Run as
`runas /netonly /user:<user> cmd`

### Weak services
replace files/programs running with SYSTEM permissions with exploited ones
-> check permissions `icacls <file>`

- - - -