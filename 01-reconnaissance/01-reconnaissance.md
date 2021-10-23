# Reconnaissance

## Related

[Bug bounty/Tools](/21-bug-bounty/02-tools.md)

## Subdomain discovery

### SSL/TLS Certificates

Find subdomains via ssl-certificates.  
E.g. using [crt.sh](https://crt.sh)

### Google

Exclude default `www` subdomain and look for any other subdomains.
```
-site:www.domain.com site:*.domain.com
```

### dnsrecon
```bash
dnsrecon -t brt -d <domain>
```

### Sublist3r
> Sublist3r is a python tool designed to enumerate subdomains of websites using OSINT.  
[Sublist3r](https://github.com/aboul3la/Sublist3r)

```bash
/sublist3r.py -d <domain>
```

### Non-public DNS

E.g. private DNS server or specified locally in `/etc/hosts`

### fuff

See also [Webserver scanning](/02-enumeration/03-webserver-scanning.md)

```bash
ffuf -w <wordlist-file> -H "Host: FUZZ.domain.com" -u http://<ip>
```

