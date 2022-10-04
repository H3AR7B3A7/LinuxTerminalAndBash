# Practical Examples

An arbitrary list of practical working examples on a Kali system.

## Add Command Line Banner

### Kali 2021.1 and earlier

> sudo chmod a+w /etc/bash.bashrc

> nano /etc/bash.bashrc

In nano append at bottom of file:

```
# Figlet banner
figlet -f slant "H3AR7B3A7" | lolcat
```

### Kali 2021.2

> nano .zshrc

In nano append at bottom of file:

```
# Figlet banner
figlet -f slant "H3AR7B3A7" | lolcat
```

## (Re-)Configure SSH

```
cd /etc/ssh
sudo mkdir old_ssh_keys
sudo mv ssh_host_* old_ssh_keys
sudo dpkg-reconfigure openssh-server
service ssh start
netstat -antp
service ssh stop
```

## Using Tor & Proxychains

```
nano /etc/proxychains.conf
```

In nano:

- Uncomment: dynamic_chain
- Comment-out: strict_chain
- Append at bottom: socks5 127.0.0.1 9050

```
service tor start
service tor status
proxychains firefox www.whatismyip.com
service tor stop
```

## Connecting to Windows via RDP

> xfreerdp /v:targetIp /u:htb-student /p:Password

