# Wireshark

> Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education. Originally named Ethereal, the project was renamed Wireshark in May 2006 due to trademark issues.
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Wireshark)</cite>

## Packet filtering

* [Building Display Filter Expressions](https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html)

### Operators:  

* [Display Filter comparison operators](https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html#DispCompOps)
* [Display Filter Logical Operations](https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html#FiltLogOps)

### Examples

IP address (any)
```
ip.addr == <ip-address>
```

Source and destination IP addresses
```
ip.src == <src-ip-address> and ip.dst == <dst-ip-address>
```

Protocol (e.g. `http`)
```
<protocol-name>
```

TCP port
```
tcp.port eq <port>
```

UDP port
```
udp.port eq <port>
```

## Capture packets

```bash
ssh <user>@<ip> "/usr/sbin/tcpdump -i ens33 -U -s0 -w - 'not port 22'" > bla.cap
wireshark bla.cap
```

Alternative approach
```bash
ssh <user>@<ip> "/usr/sbin/tcpdump -i lo -U -s0 -w - 'not port 22'" | wireshark -k -i -
```
