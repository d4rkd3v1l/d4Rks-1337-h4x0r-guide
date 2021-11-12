# Useful commands

## Related

[Process monitoring](/02-enumeration/06-process-monitoring.md)

## find

```bash
find / -maxdepth 5 -name *.php -type f -exec grep -Hn password {} \; 2>/dev/null
```

Writable files
```bash
find / -writable
```

## sudo

List commands, current user can run as root 
```bash
sudo -l
```
-> [GTFOBins](https://gtfobins.github.io/#)  
Run the command as a user other than the default target user (usually root).
```bash
sudo -u <user> <command>
```

-> Useful in scenarios like this:
```
User <user1> may run the following commands on bashed:
    (<user2> : <user2>) NOPASSWD: ALL
```

Asks the system to start a new login session for the specified user. The system will require the password for the user "username" (even if its the same as the current user).
```bash
su - <user>
```

## file

Get information about file
```bash
file <file>
```

## wc

Count chars
```bash
wc -c
```

Count lines
```bash
wc -l
```

## rlwrap

A 'readline wrapper', a small utility that uses the GNU readline library to allow the editing of keyboard input for any command.
```bash
rlwrap <cmd>
```

## Permissions

Define permissions new files get on creation, opposite (mask) to chmod permissions
```bash
umask
```

## authbind

bind sockets to privileged ports (<1024) without being root
```bash
authbind <command>
```

## base64

[Base64 Encode or Decode on the command line without installing extra tools on Linux, Windows or macOS    | Igor Kromin](https://www.igorkromin.net/index.php/2017/04/26/base64-encode-or-decode-on-the-command-line-without-installing-extra-tools-on-linux-windows-or-macos/)

### Linux

#### File

Encode `base64 -w 0 <file> > <base64file>`  
Decode `base64 -d <base64file> > <file>`  

#### String

Encode `echo -n <string> | base64`  
Decode `echo <base64string> | base64 -d`  

### Windows

#### File

Encode `certutil -encode <file> tmp.b64 && findstr /v /c:- tmp.b64 > <base64file>`  
Decode `certutil -decode <base64file> <file>`  

## grep

Print  x-lines **B**efore match  
Print  x-lines **A**fter match  
Ignore-case  
```bash
grep -i -A5 -B5 <string> <filename>
```

```bash
<cmd> | grep -A5 -B5 "text"
```

Recursive
```bash
grep -R "text" .
```

```bash
grep -oP '\d{1,5}/open' nmap_results.gnmap |  > ports
```

## watch
Run command every second
```bash
watch -n 1 '<command>'
```

## sed
Trim whitespaces
```bash
sed 's/ //g'
```

Remove newlines
```bash
sed -z 's/\n//g' <file>
```

## cut

Split string by delimiter, extract field 2
```bash
echo "some,strings" | cut -d "," -f 2 // outputs "strings"
```

Split file by colon
```bash
cut -d ":" -f 1 /etc/passwd
```

## cron

List user's crontab
```bash
crontab -l
```

## sort unique

```bash
sort -u
```

## File size

```bash
du -hs <file>
```

## ascii table

```bash
man ascii
```

## ltrace / strace

Trace library calls of a given program.
```bash
ltrace ./<programm>
```

Alternative
```bash
strace ./<programm>
```

## gcc

Use `-m32` or `-m64` to make the architecture explicit
```bash
gcc <file>.c -o <file>
```

Compile for old 32bit kernel (2.6.9)
```bash
gcc -o 1397 1397.c -m32 -Wl,--hash-style=both
```

## Specific files

### .tar.gz

```
-c		create
-x		extract
-f		file (must be last flag)
-v		verbose
-z		gzip
```

Create archive
```bash
tar -zcvf
```

Extract archive
```bash
tar -zxvf
```

### .7z

Extract
```bash
7z x <archive.7z>
```

```bash
7z l <file>
```

### .vhd

```bash
guestmount --add <vhd-file> --inspector --ro -v /mnt/vhd
```

### .scf

[https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/](https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/)  
Place scf file in windows share to gather hashes

### Images with hidden content

#### binwalk

Tool for searching binary images for embedded files and executable code
```bash
binwalk -Me <image-file>
```
