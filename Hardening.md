# Hardening

- Update system
- Install Fail2ban
- Working only with SSH keys
- Reduce Idle timeout interval
- Disable passwords
- Disable x11 forwarding
- Use a different port
- Limit users' SSH access
- Disable root logins
- Use SSH proto 2
- Enable 2FA Authentication for SSH

## Update System

> sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y

> sudo sh -c "apt update -y && apt full-upgrade -y && apt autoremove -y && apt autoclean -y"

_We can add an update alias for these commands in `.bashrc` or `.zshrc`._

## Install Fail2Ban

> sudo apt install fail2ban -y

_We should make a backup of the configuration located at `/etc/fail2ban/jail.conf`._

```
# [sshd]
enabled = true
bantime = 4w
maxretry = 3
```

_This sets the ban time to four weeks, and allows a maximum of 3 attempts._

## Editing OpenSSH Config

_We should also make a backup of `/etc/ssh/sshd_config`._

```
LogLevel VERBOSE
PermitRootLogin no
MaxAuthTries 3
MaxSessions 5
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication yes
UsePAM yes
X11Forwarding no
PrintMotd no
ClientAliveInterval 600
ClientAliveCountMax 0
AllowUsers <username>
Protocol 2
AuthenticationMethods publickey,keyboard-interactive
PasswordAuthentication no
```

_Among other things these settings turn off the ability to log in using a password, limits the amount of connections,
allows only specific users._

## 2FA Authentication

> sudo apt install libpam-google-authenticator -y

> google-authenticator

_Follow the instructions to configure google authentication._

## 2FA PAM Configuration

_We should also make a backup of the 2FA PAM Configuration at `/etc/pam.d/sshd`._

```
#@include common-auth

...

auth required pam_google_authenticator.so
auth required pam_permit.so
```

_Comment out `@include common-auth`._

## Restart SSH Server

_We need to restart the ssh server for the new configurations to take effect._

> sudo service ssh restart