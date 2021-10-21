# TFTP

> Trivial File Transfer Protocol is a simple lockstep File Transfer Protocol which allows a client to get a file from or put a file onto a remote host. One of its primary uses is in the early stages of nodes booting from a local area network.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol)</cite>

## Server

```bash
atftpd --daemon --port 69 <dir>
```

## Client

```bash
tftp -i <ip> GET <file>
```
