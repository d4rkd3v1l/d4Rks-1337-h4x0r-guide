# TCP 23: Telnet

> Telnet is an application protocol used on the Internet or local area network to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection.  

## Basics

```bash
telnet <ip> <port>
```

## Brute force

```bash
hydra -l root -P /usr/share/seclists/Passwords/Common-Credentials/10-million-password-list-top-100.txt <ip> telnet
```
