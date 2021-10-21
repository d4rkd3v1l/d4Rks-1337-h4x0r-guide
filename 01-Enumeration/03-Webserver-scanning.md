# Webserver scanning

## Related

[Services/TCP/TCP 80, 443: HTTP(S)](../02-services/01-tcp/TCP-80-443-HTTP.md)

## Common wordlists

[SecLists by Daniel Miessler](https://github.com/danielmiessler/SecLists)

General
* `/usr/share/seclists/Discovery/Web-Content/common.txt`
* `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

CGI
* `/usr/share/seclists/Discovery/Web-Content/CGIs.txt`

SharePoint
* `/usr/share/wordlists/SecLists/Discovery/Web_Content/sharepoint.txt`

## gobuster

[GitHub - OJ/gobuster](https://github.com/OJ/gobuster) - Directory/File, DNS and VHost busting tool written in Go

```bash
gobuster dir -w /usr/share/seclists/Discovery/Web-Content/common.txt -s '200,204,301,302,307,403,500' -e -o gobuster -t 50 -u <host>
```

### File extensions

IIS
```bash
-x 'asp, aspx, html, txt'
```

Apache / nginx
```bash
-x 'php, cgi, jsp, html, txt'
```

## wfuzz

[GitHub - xmendez/wfuzz](https://github.com/xmendez/wfuzz) - Web application fuzzer

```bash
wfuzz -w <wordlist-file> —-hc 404 <host>/FUZZ/FUZ2Z
```

```bash
wfuzz -c -w /usr/share/seclists/Discovery/Web-Content/common.txt --sh BBB <host>/file.php?param=FUZZ
```

## nikto

[GitHub - sullo/nikto](https://github.com/sullo/nikto) - Web server scanner

```bash
nikto -h <ip> -Format txt -o .
```

## dotdotpwn

[GitHub - wireghoul/dotdotpwn](https://github.com/wireghoul/dotdotpwn) - The Directory Traversal Fuzzer

```bash
dotdotpwn -m http -h <ip> -f <file>
```

## dirb

[DIRB](https://tools.kali.org/web-applications/dirb) is a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the response.

```bash
dirb <host>
```

## DirBuster

[DirBuster](https://tools.kali.org/web-applications/dirbuster) is a multi threaded java application designed to brute force directories and files names on web/application servers.

```bash
dirbuster
```

## wappalyzer
(firefox add-on)
[Firefox Addons](bear://x-callback-url/open-note?id=8F18F978-74A0-4CF3-A773-3B37C760CC47-456-00003D4EDE872B04)
