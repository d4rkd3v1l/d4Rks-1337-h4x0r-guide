# Wireshark
## Capture packets
`ssh <user>@<ip> "/usr/sbin/tcpdump -i ens33 -U -s0 -w - 'not port 22'" > bla.cap`
`wireshark bla.cap`

alternative approach
`ssh <user>@<ip> "/usr/sbin/tcpdump -i lo -U -s0 -w - 'not port 22'" | wireshark -k -i -`

- - - -