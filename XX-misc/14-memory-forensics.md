# Memory forensics
## Volatility
An advanced memory forensics framework
[GitHub - volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)
`apt install volatility volatility-tools`

`volatility -f <memory-dump-file> imageinfo`
`volatility -f <memory-dump-file> --profile Win2020R2x64 clipboard`
`volatility -f <memory-dump-file> --profile Win2020R2x64 pstree`
`volatility -f <memory-dump-file> --profile Win2020R2x64 hashdump`

- - - -