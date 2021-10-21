# TCP 3389: RDP
> Remote Desktop Protocol is a proprietary protocol developed by Microsoft, which provides a user with a graphical interface to connect to another computer over a network connection. The user employs RDP client software for this purpose, while the other computer must run RDP server software.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol)</cite>

## Brute force credentials

### crowbar

```bash
crowbar -b -rdp -s <ip>/32 -u <user> -C <password-file> -n 1
```

### Ncrack

```bash
ncrack -vv --user <user> -P <password-file> rdp://<ip>
```

## Connect (authenticated)

Local user
```bash
xfreerdp /u:<user> /v:<ip> +clipboard
```

Domain user
```bash
xfreerdp /d:<domain> /u:<user> /v:<ip> +clipboard
```

## Exploits

[BlueKeep - Wikipedia](https://en.wikipedia.org/wiki/BlueKeep)
