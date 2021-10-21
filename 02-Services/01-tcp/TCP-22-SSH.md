# TCP 22: SSH

> Secure Shell is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line, login, and remote command execution, but any network service can be secured with SSH.
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Secure_Shell)</cite>

## Basic commands

authenticate with key file
```bash
ssh -i keyfile <user>@<ip>
```

generate key (to file)
```bash
ssh-keygen -f <file>
chmod 600 <file>.pub
chmod 600 <file>
```

### Conventions

**Naming**
default key: `id_rsa`
user key: `<user>_key`

## SSH package version

```bash
nc -nv <ip> 22
```

```
(UNKNOWN) [10.11.1.71] 22 (ssh) open
SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
```

## SSH key fingerprint

 ```bash
 ssh root@<ip>
```

```
The authenticity of host '<ip> (<ip>)' can't be established.
ECDSA key fingerprint is SHA256:AibCWx1KvdJmNHd3KVsYksWtveJPdLZAsHMIChsTeHE.
Are you sure you want to continue connecting (yes/no)?
```

Now what happens if you see multiple SSH services on different ports which have the same key? What could it mean if they are different? Why would you see the same key on another box? All questions to think about... As this is not the case here, we will not answer that _(_**_cough_**_ but it is in the labs _**_cough_**_)_.
On this subject: A useful resource ~  [https://github.com/rapid7/ssh-badkeys](https://github.com/rapid7/ssh-badkeys) 

## SSH banner

```
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '<ip>' (ECDSA) to the list of known hosts.
root@<ip>'s password:^C
```

But we DO get a password prompt, so the machine may accept SOME users with a password, rather than keys (or both!).
 [Example of a banner](http://www.tecmint.com/wp-content/uploads/2012/11/SSH-Banner.png)  (able to get some information from it too - domain name!).


## Nmap Scripts

-> automate fingerprinting and banner grabbing

```bash
ls -lh /usr/share/nmap/scripts/*ssh*
```

```
-rw-r--r-- 1 root root 5.6K Mar 31 08:51 /usr/share/nmap/scripts/ssh2-enum-algos.nse
-rw-r--r-- 1 root root  16K Mar 31 08:51 /usr/share/nmap/scripts/ssh-hostkey.nse
-rw-r--r-- 1 root root 1.5K Mar 31 08:51 /usr/share/nmap/scripts/sshv1.nse
```


```bash
nmap <ip> -p 22 -sV --script=ssh-hostkey
```

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 6.6.1p1 Ubuntu 2ubuntu2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|_  1024 72:b5:55:80:1b:24:d6:f3:bf:a5:c5:98:1b:01:03:90 (DSA)
```

## SSH "Konami Code"

> The **Konami Code** is a cheat code that appears in many Konami video games, and some non-Konami games. In the original code, the player can press the following sequence of buttons on the game controller to enable a cheat or other effects: ↑↑↓↓←→←→BA  

[SANS Penetration Testing | Using the SSH "Konami Code" (SSH Control Sequences) | SANS Institute](https://www.sans.org/blog/using-the-ssh-konami-code-ssh-control-sequences/)
