# TCP 21: FTP

> The File Transfer Protocol is a standard network protocol used for the transfer of computer files between a client and server on a computer network. FTP is built on a client-server model architecture using separate control and data connections between the client and the server.  

## Commands

connect 
```bash
ftp <ip>
```

show all files
```bash
dir -a
```

use binary mode for file transfers
```bash
binary
```

download file
```bash
get <file>
```

upload file
```bash
put <localfile>
```
