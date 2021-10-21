# TFTP
> Trivial File Transfer Protocol is a simple lockstep File Transfer Protocol which allows a client to get a file from or put a file onto a remote host. One of its primary uses is in the early stages of nodes booting from a local area network.   

- - - -
## Server
`atftpd --daemon --port 69 <dir>`

- - - -
## Client
`tftp -i <ip> GET <file>`

- - - -