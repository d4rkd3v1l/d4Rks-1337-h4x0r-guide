# Proxy
## ssh
**D**ynamic port forwarding (SOCKS?)
`ssh -D <new-port> <target-ip>`

**L**ocal port forwarding
`ssh -L <fromPort>:<toHost>:<toPort> user@<viaHost>`
-> `toHost` and `viaHost` may be the same machine -> toHost=localhost (viaHost's point of view)

## proxychains
A tool that forces any TCP connection made by any given application to follow through proxy like TOR or any other SOCKS4, SOCKS5 or HTTP(S) proxy.  
[GitHub - haad/proxychains: proxychains](https://github.com/haad/proxychains)

```/etc/proxychains.conf
socks5 127.0.0.1 1080
```

`proxychains <cmd>`

- - - -