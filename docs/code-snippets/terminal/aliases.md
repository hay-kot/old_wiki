# Helpful Aliases

## General

### Custom Apt Alises
Stolen from the Internet! 

```bash
# Custom Apt
alias app="sudo apt-get"
alias app-remove="sudo apt-get remove"
alias app-install="sudo apt-get install"
alias app-edit="sudo envedit /etc/apt/sources.list"
alias app-search="apt-cache --names-only search"
alias app-search-all="apt-cache search"
alias app-update="sudo apt-get update && sudo apt-get upgrade"
alias app-info="apt-cache showpkg"
```

### Speed Test

```bash
speedtest() {
    curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -
}
```

### IP Geo

```bash
# Find geo info from IP
ipgeo() {
    # Specify ip or your ip will be used
    if [ "$1" ]; then
        curl "http://api.db-ip.com/v2/free/$1"
    else
        curl "http://api.db-ip.com/v2/free/$(myip)"
    fi
}
```

## File System

### Make and CD 

```bash
mkcdir ()
{
    mkdir -p -- "$1" &&
      cd -P -- "$1"
}
```

### lfcd
Stolen from [Luke Smith](https://www.youtube.com/channel/UC2eYFnH61tmytImy1mTYvhA). This alises `lfcd` to cd into the directory you were last in, in lf. 
```bash
# Use lf to switch directories and bind it to ctrl-o
lfcd () {
    tmp="$(mktemp)"
    lf -last-dir-path="$tmp" "$@"
    if [ -f "$tmp" ]; then
        dir="$(cat "$tmp")"
        rm -f "$tmp"
        [ -d "$dir" ] && [ "$dir" != "$(pwd)" ] && cd "$dir"
    fi
}
bindkey -s '^o' 'lfcd\n'
```
### lfcode
A modified version of the above alias that will, instead of cd, will open vs code in the folder you last exited from. Super handy for wsl, or if you're a heavy terminal user. 

```bash
# Opens Last lf Directory in VSCode
lfcode () {
    tmp="$(mktemp)"
    lf -last-dir-path="$tmp" "$@"
    if [ -f "$tmp" ]; then
        dir="$(cat "$tmp")"
        rm -f "$tmp"
        [ -d "$dir" ] && [ "$dir" != "$(pwd)" ] && code "$dir"
    fi
}
bindkey -s '^[c' 'lfcode\n'
```