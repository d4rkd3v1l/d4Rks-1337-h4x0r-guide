# Wireshark

## Capture packets

```bash
ssh <user>@<ip> "/usr/sbin/tcpdump -i ens33 -U -s0 -w - 'not port 22'" > bla.cap
wireshark bla.cap
```

Alternative approach
```bash
ssh <user>@<ip> "/usr/sbin/tcpdump -i lo -U -s0 -w - 'not port 22'" | wireshark -k -i -
```
