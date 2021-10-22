# TCP 135: MSRPC

> Remote Procedure Call (RPC) port 135 is used in client_server applications (might be on a single machine) such as Exchange clients, the recently exploited messenger service, as well as other Windows NT/2K_XP software. If you have remote users who VPN into your network, you might need to open this port on the firewall to allow access to the Exchange server.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Microsoft_RPC)</cite>

## Related

* [Impacket](/XX-misc/08-impacket.md)

## Enumeration

```bash
nmap --script=msrpc-enum <ip>
```
