# TCP 53: DNS

> The Domain Name System is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. It associates various information with domain names assigned to each of the participating entities.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Domain_Name_System)</cite>

## Host

Nameserver
```bash
host -t ns megacorpone.com
```

Mailserver
```bash
host -t mx megacorpone.com
```

Domain
```bash
host www.megacorpone.com
```

## Forward lookup

```bash
host <hostname>
```

```
alpha.thinc.local has address <ip>
```


```bash
#!/bin/bash
for name in $(cat list.txt); do
	host $name.megacorpone.com | grep "has address" | cut -d" " -f1,4
done
```

## Reverse lookup

```bash
host <ip>
```

```
<ip>.in-addr.arpa domain name pointer alpha.thinc.local.
```

```bash
#!/bin/bash
for ip in $(seq 72 91); do
	host 38.100.193.$ip | grep "megacorp" | cut -d" " -f1,5
done
```

## Zone transfer

A zone transfer is similar to a database replication act between related DNS servers. This process includes the copying of the zone file from a master DNS server to a slave server. 

```bash
host -l megacorpone.com ns1.megacorpone.com
```

```bash
#!/bin/bash
if [ -z "$1" ]; then
	echo "Usage : $0 <domain name>"
	exit 0
fi

for server in $(host -t ns $1 | cut -d" " -f4); do
	host -l $1 $server | grep "has address"
done
```

### Alternative

```bash
dig axfr @<ip> <hostname>
```

## Tools

### DNSRecon

```bash
dnsrecon -d <dns-server> -t axfr
dnsrecon -d <dns-server> -r 10.0.0.0/8
```

### DNSenum

```bash
dnsenum megacorpone.com
```

### nslookup
```bash
nslookup
> server <ip>
```
