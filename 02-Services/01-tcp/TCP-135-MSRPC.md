# TCP 135: MSRPC

> Remote Procedure Call (RPC) port 135 is used in client_server applications (might be on a single machine) such as Exchange clients, the recently exploited messenger service, as well as other Windows NT/2K_XP software. If you have remote users who VPN into your network, you might need to open this port on the firewall to allow access to the Exchange server.  

## Related

[Impacket](bear://x-callback-url/open-note?id=8B82F3FA-7934-4517-98E9-ED74DD9C76EB-524-000018D307D11453)

## Enumeration

```bash
nmap --script=msrpc-enum <ip>
```
