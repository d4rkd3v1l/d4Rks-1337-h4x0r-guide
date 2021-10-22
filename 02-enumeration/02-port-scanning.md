# Port scanning

## Nmap

> The Network Mapper - Free Security Scanner  
[Nmap](https://nmap.org)

* Standalone
[static-tools/nmap at master · ZephrFish/static-tools · GitHub](https://github.com/ZephrFish/static-tools/blob/master/nmap/nmap)

* XSL Bootstrap
[GitHub - honze-net/nmap-bootstrap-xsl: A Nmap XSL implementation with Bootstrap.](https://github.com/honze-net/nmap-bootstrap-xsl)

### TCP

#### Common options

option | description
--- | ---
`-p` | port ranges (default: most common 1000 ports), -p- all ports (1-65536)
`-sV` | version scanning
`-sC` |	script scanning
`-O` | OS detection
`-A` | Aggressive scan options, combines: -O, -sV, -sC, --traceroute
`-T<0-5>` | Set timing template (higher is faster), aka paranoid\|sneaky\|polite\|normal\|aggressive\|insane (default: 3, aka normal)
`-oA` |	basename (Output to all formats)
`-sU` | UDP scan
`--max-retries` | set to 1 or 0 to considerably speed up scan (but gets a bit less accurate)

#### Examples

Light scan
```bash
nmap <ip> --top-ports 10 --open -oA nmap_light
```

Heavy scan
```bash
nmap <ip> -p- -sV -sC --reason -oA nmap_heavy
```

Scan for vulns

```bash
nmap --script "vuln and safe" -oA nmap_vuln <ip>
```

```bash
nmap -p 139,445 --script smb-vuln* <ip>
```

### UDP

```bash
nmap -sU -oA nmap_udp <ip>
```

### Useful stuff

Get open ports comma separated

```bash
grep -oP '\d{1,5}/open' nmap.gnmap | cut -d  "/" -f 1 | paste -s -d ','
```

### Nmap scripts

#### banner plus 

Quicker scanning and smarter identification

[GitHub - scan-tools/banner-plus.nse](https://github.com/hdm/scan-tools/blob/master/nse/banner-plus.nse)

#### vulners

NSE script based on Vulners.com API

[GitHub - vulnersCom/nmap-vulners](https://github.com/vulnersCom/nmap-vulners)

### nmapAutomator

A script that you can run in the background!

[GitHub - 21y4d/nmapAutomator](https://github.com/21y4d/nmapAutomator)
```bash
./nmapAutomator <ip> All
```

## netcat (nc)

TCP/IP swiss army knife

[The GNU Netcat -- Official homepage](http://netcat.sourceforge.net)

### TCP

Connect scan (only validates if ports are open)

```bash
nc -nvv -w 1 -z <ip> <port-range>
```

### UDP

```bash
nc -nv -u -z -w 1 <ip> <port-range>
```

No response means port is open, otherwise a ICMP packet `port unreachable` is sent back.  
**BUT:** Response may get dropped (firewalls, routers, ...) -> false positive

## Port knocking

> In computer networking, port knocking is a method of externally opening ports on a firewall by generating a connection attempt on a set of prespecified closed ports.
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Port_knocking)</cite>

```bash
knockd
/etc/knockd.conf
```

Actually knock to a port
```bash
nmap -Pn -sT --host_timeout 201 --max-retries 0 -p <port> <ip>
```
or
```bash
echo "" > /dev/tcp/<ip>/<port>
```

## Simple bash port scanner

```bash
#!/bin/bash
host=<host>
for port in {1..65535}; do
	timeout .1 bash -c "echo >/dev/tcp/$host/$port" && echo "port $port is open"
done
echo "Done"
```
