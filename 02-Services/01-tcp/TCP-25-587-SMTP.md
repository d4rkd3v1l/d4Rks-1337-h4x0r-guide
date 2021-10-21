# TCP 25, 587: SMTP

> The Simple Mail Transfer Protocol is a communication protocol for electronic mail transmission. As an Internet standard, SMTP was first defined in 1982 by RFC 821, and updated in 2008 by RFC 5321 to Extended SMTP additions, which is the protocol variety in widespread use today.  

## Related

[SMTP and POP3 commands](https://www.suburbancomputer.com/tips_email.htm)

## Enumeration

Connect
```bash
nc -nv <ip> 25
```

### Verify users

Manually
```bash
VRFY <user>
```
-> 250 success, 550 not found

Automated
```bash
/usr/share/legion/scripts/smtp-user-enum.pl -M RCPT -U <users-file> -t <ip>
```

Automated #2
```bash
for user in $(cat users.txt); do echo VRFY $user | nc -nv -w 1 <ip> 25 2>/dev/null | grep ^"250"; done
```

### Nmap scripts

smtp-brute.nse
smtp-commands.nse
smtp-enum-users.nse
smtp-ntlm-info.nse
smtp-open-relay.nse
smtp-strangeport.nse
smtp-vuln-cve2010-4344.nse
smtp-vuln-cve2011-1720.nse
smtp-vuln-cve2011-1764.nse
