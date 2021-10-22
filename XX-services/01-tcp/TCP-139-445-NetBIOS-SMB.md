# TCP 139, 445: NetBIOS, SMB

> NetBIOS is a protocol used for File and Print Sharing under all current versions of Windows. While this in itself is not a problem, the way that the protocol is implemented can be. There are a number of vulnerabilities associated with leaving this port open.  
>   
> **NetBios services:**  
> NETBIOS Name Service (TCP/UDP: 137)  
> NETBIOS Datagram Service (TCP/UDP: 138)  
> NETBIOS Session Service (TCP/UDP: 139)  

> TCP port 445 is used for direct TCP_IP MS Networking access without the need for a NetBIOS layer. This service is only implemented in the more recent verions of Windows (e.g. Windows 2K / XP). The SMB (Server Message Block) protocol is used among other things for file sharing in Windows NT/2K_XP. In Windows NT it ran on top of NetBT (NetBIOS over TCP_IP, ports 137, 139 and 138_udp). In Windows 2K_XP, Microsoft added the possibility to run SMB directly over TCP_IP, without the extra layer of NetBT. For this they use TCP port 445.  

## Related

[UDP 137, 138, TCP 139: NetBIOS](bear://x-callback-url/open-note?id=E0AA4FC2-1382-437C-B64D-B9F1F8E72984-962-000006165E66E247)

## Enumeration

### nbtscan

```bash
sudo nbtscan -r <ip-range>
```

### nmap

```bash
nmap -p139,445 <ip> --open
```

```bash
ls -l /usr/share/nmap/scripts | grep smb
```

```bash
nmap -p139,445 --script "smb*" --script-timeout 30 -oA nmap_smb <ip>
```

```bash
nmap -p139,445 --script "smb-vuln*" --script-timeout 30 -oA nmap_smb-vuln <ip>
```

### Enum4Linux

**enum4linux** is a tool for enumerating information from Windows and Samba systems 
```bash
enum4linux -a <ip>
```

Run this in parallel to grep the samba version
```bash
sudo ngrep -i -d tun0 's.?a.?m.?b.?a.*[[:digit:]]'
```

### SMBMap

SMBMap is a handy SMB enumeration tool  
[GitHub - ShawnDEvans/smbmap](https://github.com/ShawnDEvans/smbmap)
```bash
apt install smbmap
```

List files on target
```bash
smbmap -H <ip> -R --depth 5
```

Enumerate authenticated
```bash
smbmap -d <domain> -u <user> -p <hash:hash or pw> -H <ip>
```

Find file
```bash
smbmap -R <folder> -H <ip> -A Groups.xml -q
```

## Tools

### smbclient

FTP-like client to access SMB/CIFS resources on servers

**list shares**  
Unauthenticated
```bash
smbclient -N -L //<ip>
```

Authenticated
```bash
smbclient -L //<ip> -U <user>%<pass>
smbclient \\\\$ip\\$share
```

Mount share
```bash
smbclient //<ip>/share
```
(look for files, containing `password`, `pwd`, `admin`, `user`, `connect`, etc.)  

Download file
```bash
get <file>
```

Pull all files from (readable) share
```bash
recurse ON
prompt OFF
mget *
```

### mount

Mount smb share locally
```bash
mount -t cifs -o username=<user>,password=<pw> //<ip>/<share> /mnt/<share>
```

### gpp-decrypt

A simple ruby script that will decrypt a given GPP encrypted string.
```bash
apt install gpp-decrypt
```

```bash
gpp-decrypt <Groups.xml-cpassword>
```

### smbexec

A rapid psexec style attack with samba tools  
* [GitHub - brav0hax/smbexec](https://github.com/brav0hax/smbexec)
* [GitHub - 404NetworkError/smbexec at fixes](https://github.com/404NetworkError/smbexec/tree/fixes)

grab password hashes from domain controller
```bash
./smbexec
```
-> 3 "obain hashes"  
-> 2 "domain controllers"  

### crackmapexec

TODO

## null sessions

Pre Windows 2003, XP SP2
```bash
rpcclient -U "" <ip>
```
-> Enter empty password

```bash
srvinfo
enumdomusers
getdompwinfo
querydominfo
netshareenum
netshareenumall
```

## Metasploit

### smb version

Get samba version
```bash
use auxiliary/scanner/smb/smb_version
```

### psexec

```bash
use auxiliary/admin/smb/psexec_command
```
