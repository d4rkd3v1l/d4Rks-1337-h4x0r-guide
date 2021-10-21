# Process monitoring

## ps

[ps(1) - Linux manual page](http://man7.org/linux/man-pages/man1/ps.1.html) - Report a snapshot of the current processes.

```bash
ps aux
```

## top

[top(1) - Linux manual page](http://man7.org/linux/man-pages/man1/top.1.html) - Display Linux tasks

```bash
top
```

## pspy

[GitHub - DominicBreuker/pspy](https://github.com/DominicBreuker/pspy) - Monitor linux processes without root permissions

```bash
pspy64
```

## psmonitor.sh

Monitor process changes

```bash
#!/bin/bash
IFS=$'\n'
op=$(ps -eo command)
while true; do
    np=$(ps -eo command)
    diff <(echo "$op") <(echo "np")
    sleep 1
    op=$np
done
```
