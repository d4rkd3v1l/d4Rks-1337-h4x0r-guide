# Webserver scanning

# TODO
- [ ] [GitHub - hakluke/hakrawler: Simple, fast web crawler designed for easy, quick discovery of endpoints and assets within a web application](https://github.com/hakluke/hakrawler)
- [ ] Builtwith
- [ ] Securityheaders.com
- [ ] ssllabs.com
- [ ] What CMS [Detect which CMS a site is using - What CMS?](https://whatcms.org)

## Related

[TCP 80/443: HTTP(S)](bear://x-callback-url/open-note?id=7F1339AE-96E5-433F-8DDD-17D50A5109F7-13133-00015BE530577C46)

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

Directory/File, DNS and VHost busting tool written in Go
[GitHub - OJ/gobuster](https://github.com/OJ/gobuster)

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

Web application fuzzer
[GitHub - xmendez/wfuzz](https://github.com/xmendez/wfuzz)

```bash
wfuzz -w <wordlist-file> —-hc 404 <host>/FUZZ/FUZ2Z
```

```bash
wfuzz -c -w /usr/share/seclists/Discovery/Web-Content/common.txt --sh BBB <host>/file.php?param=FUZZ
```

## nikto

Nikto web server scanner
[GitHub - sullo/nikto](https://github.com/sullo/nikto)

```bash
nikto -h <ip> -Format txt -o .
```

## dotdotpwn

DotDotPwn - The Directory Traversal Fuzzer
[GitHub - wireghoul/dotdotpwn](https://github.com/wireghoul/dotdotpwn)

```bash
dotdotpwn -m http -h <ip> -f <file>
```

## dirb

DIRB is a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the response.
[DIRB | Penetration Testing Tools](https://tools.kali.org/web-applications/dirb)

```bash
dirb <host>
```

## dirbuster

DirBuster is a multi threaded java application designed to brute force directories and files names on web/application servers.
[DirBuster | Penetration Testing Tools](https://tools.kali.org/web-applications/dirbuster)

```bash
dirbuster
```

## wappalyzer
(firefox add-on)
[Firefox Addons](bear://x-callback-url/open-note?id=8F18F978-74A0-4CF3-A773-3B37C760CC47-456-00003D4EDE872B04)
