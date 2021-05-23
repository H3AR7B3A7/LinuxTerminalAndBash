# Example Practical Examples

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
