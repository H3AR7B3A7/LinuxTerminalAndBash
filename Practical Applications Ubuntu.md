# Practical Examples

An arbitrary list of practical working examples on an Ubuntu system.

## Hosting a Website Using NGiNX

```
sudo mkdir -p /var/www/mysite.net
cd IdeaProjects/MySite
sudo cp -r * /var/www/mysite.net/
sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/mysite.net
sudo nano /etc/nginx/sites-available/mysite.net
sudo ln -s /etc/nginx/sites-available/mysite.net /etc/nginx/sites-enabled/
sudo rm /etc/nginx/sites-enabled/default
sudo ls /etc/nginx/sites-enabled/mysite.net
sudo service nginx restart
```

## Hosting a Website Using Python

```
py -m http.server
```

## Hosting a Website Using PhP

```
brew install php
php -S 127.0.0.1:8080
```

## Hosting a Website Using NPM

```
npx http-server -p 8080
```

## Hosting a Website Using Apache

```
sudo apt install apache2
systemctl start apache2
```

 Change the port:

```
sudo nano /etc/apache2/ports.conf
```


## Connecting to Server Using SSH Key

```
ssh-keygen -b 2048 -t rsa -C name@company.com
ls .ssh
cat .ssh/id_rsa.pub
ssh-copy-id -i .ssh/id_rsa.pub name@172.16.141.186
ssh name@172.16.141.186
```


## Securely Transferring Files to Server Using SSH and SCP

Remote:
```
nano /etc/nginx/sites-available/mysite.net
sudo chmod a+w /etc/nginx/sites-available/
sudo chmod a+x /etc/nginx/sites-available/
scp /home/name/mysite.net name@172.16.141.186:/etc/nginx/sites-available
```

Server:
```
ls -l /etc/nginx/sites-available/
sudo chown root /etc/nginx/sites-available/mysite.net
sudo ln /etc/nginx/sites-available/mysite.net /etc/nginx/sites-enabled/
sudo rm /etc/nginx/sites-enabled/default
sudo ls /etc/nginx/sites-enabled/
sudo service nginx restart
```

### Using SSH Config
Remote:
```
touch .ssh/config
nano .ssh/config
```

Nano:
```
Host myServer
    HostName        172.16.141.186
    User            name
    IdentityFile    ~/.ssh/id_rsa
```

Remote Server:
```
ssh myServer
sudo mkdir -p /var/www
sudo chmod a+w /var/www/
sudo chmod a+x /var/www/
```

Remote:
```
scp -r /var/www/mysite.net myServer:/var/www/mysite.net/
```

## SSH into Alpine Docker

### Create
docker run --name remote -dit -p 22:22 alpine:latest

### Stop
docker stop remote

### Start
docker start remote

### Enter
docker exec -it remote sh

### Move file to container
docker cp foo.txt remote:/some/path/foo.txt

### Move file to host
docker cp remote:/some/path/foo.txt /host/path


### Set up SSH

#### Install OpenSSH
apk add openssh --no-cache

#### Install OpenRC
apk add openrc --no-cache

#### Generate Keys
ssh-keygen -A

#### Turn Off Password Auth
vi /etc/ssh/sshd_config

```
PasswordAuthentication no
```

#### Add Public Key to Authorized Keys
cat /etc/ssh/ssh_host_ecdsa_key.pub > /root/.ssh/authorized_keys

#### Copu Private Key to Host
docker cp remote:/etc/ssh/ssh_host_ecdsa_key ~/.ssh

#### Touch Softlevel Because Init w/o OpenRC
touch /run/openrc/softlevel

#### Start SSHD on Remote
rc-service sshd start

#### Get IP
sudo docker inspect -f "{{ .NetworkSettings.IPAddress }}" remote

#### Connect
ssh root@172.17.0.2

#### Add to Hosts on Host
sudo nano /etc/hosts

```
172.17.0.2       remote
```

#### Connect
ssh root@remote