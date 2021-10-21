# Useful commands
- - - -
## Related
[process monitoring](bear://x-callback-url/open-note?id=61C0A322-548D-478E-8957-CA6438187AFC-13681-000027246D90369E)

- - - -
## find
`find / -maxdepth 5 -name *.php -type f -exec grep -Hn password {} \; 2>/dev/null`

writable files
`find / -writable`

- - - -
## sudo
list commands, current user can run as root 
`sudo -l`
-> [GTFOBins](https://gtfobins.github.io/#)

Run the command as a user other than the default target user (usually root).
`sudo -u <user> <command>`

-> Useful in scenarios like this:
```
User <user1> may run the following commands on bashed:    (<user2> : <user2>) NOPASSWD: ALL
```

Asks the system to start a new login session for the specified user. The system will require the password for the user "username" (even if its the same as the current user).
`su - <user>`

- - - -
## file
get information about file
`file <file>`

- - - -
## wc
count chars
`wc -c`

count lines
`wc -l`

- - - -
## rlwrap
A 'readline wrapper', a small utility that uses the GNU readline library to allow the editing of keyboard input for any command.
`rlwrap <cmd>`

- - - -
## Permissions
define permissions new files get on creation, opposite (mask) to chmod permissions
`umask` 

- - - -
## authbind
bind sockets to privileged ports (<1024) without being root
`authbind <command>`

- - - -
## base64
[Base64 Encode or Decode on the command line without installing extra tools on Linux, Windows or macOS    | Igor Kromin](https://www.igorkromin.net/index.php/2017/04/26/base64-encode-or-decode-on-the-command-line-without-installing-extra-tools-on-linux-windows-or-macos/)

### Linux
#### File
encode `base64 -w 0 <file> > <base64file>`
decode `base64 -d <base64file> > <file>`

#### String
encode `echo -n <string> | base64`
decode `echo <base64string> | base64 -d`

### Windows
#### File
encode `certutil -encode <file> tmp.b64 && findstr /v /c:- tmp.b64 > <base64file>`
decode `certutil -decode <base64file> <file>`

- - - -
## grep
print  x-lines **B**efore match
print  x-lines **A**fter match
ignore-case
`grep -i -A5 -B5 <string> <filename>`
`<cmd> | grep -A5 -B5 "text"`

Recursive
`grep -R 4.0.5 .`

`grep -oP '\d{1,5}/open' nmap_results.gnmap |  > ports`

- - - -
## watch
run command every second
`watch -n 1 '<command>'`

- - - -
## sed
trim whitespaces
`sed 's/ //g'`

remove newlines
`sed -z 's/\n//g' cmdasp.aspx`

- - - -
## cut
split string by delimiter, extract field 2
`echo "some,strings" | cut -d "," -f 2 // outputs "strings"`

split file by colon
`cut -d ":" -f 1 /etc/passwd`

- - - -
## cron
list user's crontab
`crontab -l`

- - - -
## sort unique
`sort -u`

- - - -
## file size
`du -hs <file>`

- - - -
## ascii table
`man ascii`

- - - -
## ltrace / strace
Trace library calls of a given program.
`ltrace ./<programm>`

alternative
`strace ./<programm>`

- - - -
## gcc
use `-m32` or `-m64` to make the architecture explicit
`gcc <file>.c -o <file>`

compile for old 32bit kernel (2.6.9)
`gcc -o 1397 1397.c -m32 -Wl,--hash-style=both`

- - - -
## specific files
### .tar.gz

```
-c		create
-x		extract
-f		file (must be last flag)
-v		verbose
-z		gzip
```

create archive
`tar -zcvf`

extract archive
`tar -zxvf`

### .7z
extract
`7z x <archive.7z>`

### .vhd
`7z l <file>`
`guestmount --add <vhd-file> --inspector --ro -v /mnt/vhd`

### .scf
[https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/](https://1337red.wordpress.com/using-a-scf-file-to-gather-hashes/)
place scf file in windows share to gather hashes

### images with hidden content
#### binwalk
tool for searching binary images for embedded files and executable code
`binwalk -Me <image-file>`

- - - -