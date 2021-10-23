# Wget

> GNU Wget is a computer program that retrieves content from web servers. It is part of the GNU Project. Its name derives from World Wide Web and get. It supports downloading via HTTP, HTTPS, and FTP. Its features include recursive download, conversion of links for offline viewing of local HTML, and support for proxies.  
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Wget)</cite>

## Options

Recursive 
```bash
wget -r <ip>:<port>/file.txt
```

Read from file
```bash
wget -i <file>
```

Download complete ftp
```bash
wget --mirror 'ftp://<name>:<pw>@<host>'
```
