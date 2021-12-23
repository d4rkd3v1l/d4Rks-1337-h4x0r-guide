# Proxy

## ssh

**D**ynamic port forwarding (SOCKS proxy)
```bash
ssh -D <port> <user>@<viaHost>
```

E.g.  
```bash
ssh -D 1337 user@myserver.com
```

**L**ocal port forwarding
```bash
ssh -L <fromPort>:<toHost>:<toPort> <user>@<viaHost>
```

E.g.  
Accessing localhost:`1337` will load `google.com:80` via `myserver.com` using `user`s account.
```bash
ssh -L 1337:google.com:80 user@myserver.com
```

**R**emote port forwarding
```bash
ssh -R <fromPort>:<toHost>:<toPort> <user>@<viaHost>
```

E.g.  
Accessing myserver.com:`1337` will load `localhost:80` via `myserver.com` using `user`s account.
```bash
ssh -R 1337:localhost.com:80 user@myserver.com
```

## proxychains

> A tool that forces any TCP connection made by any given application to follow through proxy like TOR or any other SOCKS4, SOCKS5 or HTTP(S) proxy.  
[GitHub - haad/proxychains: proxychains](https://github.com/haad/proxychains)

```/etc/proxychains.conf
socks5 127.0.0.1 1080
```

```bash
proxychains <cmd>
```
