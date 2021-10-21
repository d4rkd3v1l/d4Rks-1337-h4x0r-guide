# TCP 143, 993: IMAP(S)

> In computing, the Internet Message Access Protocol is an Internet standard protocol used by email clients to retrieve email messages from a mail server over a TCP/IP connection. IMAP is defined by RFC 3501.  

## General

Connect
```bash
nc -nv <IP> 143
```

```bash
nmap -sV --script=imap-ntlm-info <ip>
```

### Nmap scripts

imap-brute.nse
imap-capabilities.nse
imap-ntlm-info.nse
