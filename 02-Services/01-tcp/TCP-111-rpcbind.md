# TCP 111: rpcbind
> The port mapper (rpc.portmap or just portmap, or rpcbind) is an Open Network Computing Remote Procedure Call (ONC RPC) service that runs on network nodes that provide other ONC RPC services.
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Portmap)</cite>

Get Info
```bash
rpcinfo -s <ip>
rpcinfo -p <ip>
```

Look for NFS shares
```bash
rpcbind -p <ip>
sudo showmount -e <ip>
```
