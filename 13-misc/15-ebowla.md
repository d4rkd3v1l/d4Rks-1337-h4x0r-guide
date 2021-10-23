# Ebowla

> Framework for Making Environmental Keyed Payloads (NO LONGER SUPPORTED)  
[GitHub - Genetic-Malware/Ebowla](https://github.com/Genetic-Malware/Ebowla)

## Usage

```bash
genetic.config
output_type = GO
payload_type = EXE
```
Configure stuff in `[[ENV_VAR]]`, e.g. computer_name

```bash
python ebowla.py <shell.exe> genetic.config
./build_x64_go.sh output/<generated-go-script> <output.exe>
```

## Use with LonelyPotato / RottenPotato / JuicyPotato

```cmd
lonelypotato.exe * <ebowla-output.exe>
```
