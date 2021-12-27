# Network discovery

## netdiscover

[netdiscover(8)](https://manpages.debian.org/unstable/netdiscover/netdiscover.8.en.html) - active/passive ARP reconnaissance tool

```bash
netdiscover -i eth0
```

```bash
netdiscover -r <ip>/24
```

## nmap

```bash
nmap -sn <ip>/24
```

## bash

```bash
for i in {1..255}; do (ping -c 1 xxx.xxx.xxx.${i} | grep "bytes from" &); done
```
