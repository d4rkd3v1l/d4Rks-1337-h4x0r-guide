# TCP 3389: RDP
> Remote Desktop Protocol is a proprietary protocol developed by Microsoft, which provides a user with a graphical interface to connect to another computer over a network connection. The user employs RDP client software for this purpose, while the other computer must run RDP server software.  

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

local user
```bash
xfreerdp /u:<user> /v:<ip> +clipboard
```

domain user
```bash
xfreerdp /d:<domain> /u:<user> /v:<ip> +clipboard
```

## Exploits

[BlueKeep - Wikipedia](https://en.wikipedia.org/wiki/BlueKeep)