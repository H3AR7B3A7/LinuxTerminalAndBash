# Practical Examples

An arbitrary list of practical working examples on a Kali system.


## Add Command Line Banner

### Kali 2021.1 and earlier

>sudo chmod a+w /etc/bash.bashrc

>nano /etc/bash.bashrc

In nano append at bottom of file:
```
# Figlet banner
figlet -f slant "H3AR7B3A7" | lolcat
```

### Kali 2021.2

>nano .zshrc

In nano append at bottom of file:
```
# Figlet banner
figlet -f slant "H3AR7B3A7" | lolcat
```

