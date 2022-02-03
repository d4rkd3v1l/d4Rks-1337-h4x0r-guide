# TCP 139, 445: NetBIOS, SMB

> NetBIOS is a protocol used for File and Print Sharing under all current versions of Windows. While this in itself is not a problem, the way that the protocol is implemented can be. There are a number of vulnerabilities associated with leaving this port open.  
>   
> **NetBios services:**  
> NETBIOS Name Service (TCP/UDP: 137)  
> NETBIOS Datagram Service (TCP/UDP: 138)  
> NETBIOS Session Service (TCP/UDP: 139)  

> TCP port 445 is used for direct TCP_IP MS Networking access without the need for a NetBIOS layer. This service is only implemented in the more recent verions of Windows (e.g. Windows 2K / XP). The SMB (Server Message Block) protocol is used among other things for file sharing in Windows NT/2K_XP. In Windows NT it ran on top of NetBT (NetBIOS over TCP_IP, ports 137, 139 and 138_udp). In Windows 2K_XP, Microsoft added the possibility to run SMB directly over TCP_IP, without the extra layer of NetBT. For this they use TCP port 445.  

## Related

[UDP 137, 138, TCP 139: NetBIOS](../02-udp/UDP-137-138-TCP-139-NetBIOS.md)

## Enumeration

### nbtscan

```bash
sudo nbtscan -r <ip-range>
```

### nmap

Check default SMB ports are open
```bash
nmap -p139,445 <ip> --open
```

List SMB scripts
```bash
ls -l /usr/share/nmap/scripts | grep smb
```

Run all SMB scripts
```bash
nmap -p139,445 --script "smb*" --script-timeout 30 -oA nmap_smb <ip>
```

Run all SMB vuln scripts
```bash
nmap -p139,445 --script "smb-vuln*" --script-timeout 30 -oA nmap_smb-vuln <ip>
```

### enum4linux

**enum4linux** is a tool for enumerating information from Windows and Samba systems 
```bash
enum4linux -a <ip>
```

Run this in parallel to grep the samba version
```bash
sudo ngrep -i -d tun0 's.?a.?m.?b.?a.*[[:digit:]]'
```

### enum4linux-ng
> A next generation version of enum4linux (a Windows/Samba enumeration tool) with additional features like JSON/YAML export. Aimed for security professionals and CTF players.  
[GitHub - cddmp/enum4linux-ng](https://github.com/cddmp/enum4linux-ng)

```bash
python enum4linux-ng.py -A <ip>
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
smbclient -L //<ip> -U <user> -P <pass>
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

> A swiss army knife for pentesting networks  
[GitHub - byt3bl33d3r/CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec)  

-> [SMB Command Reference](https://github.com/byt3bl33d3r/CrackMapExec/wiki/SMB-Command-Reference)  

Display help (smb)  
```bash
cme smb --help
```

[Using Credentials, NULL Sessions, PtH Attacks](https://github.com/byt3bl33d3r/CrackMapExec/wiki/Using-Credentials,-NULL-Sessions,-PtH-Attacks)  
```bash
cme smb <ip> -u <user> -H <hash>
```

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
