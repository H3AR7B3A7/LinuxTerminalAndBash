# Ubuntu Installations

## Before Starting

When uncertain about a packet name we can use:
>apt search name

Installing files can only be done by a super user.
We can either elevate our command temporarily by using:
>sudo

Or by elevating ourselves to super user (not recommended):
>sudo su

### Update APT

Before installing anything we might want to update the *advanced packaging tool*:
>sudo apt-get update

## Common Installations

### Git
>sudo apt-get install git

### Java
[Download Oracle JDK for Debian](https://www.oracle.com/java/technologies/javase-downloads.html)

>sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-16.0.1/bin/java 1

>sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-16.0.1/bin/javac 1

Or just check your version and follow instructions for OpenJDK:
>java --version

### NodeJS & NPM
>sudo apt-get install nodejs

>sudo apt-get install npm

Updating:
>sudo npm install npm@latest -g

>sudo npm install nodejs@latest -g

### NGINX
>sudo apt-get install nginx

### OpenSSH
Server:
>sudo apt-get install openssh-server

Client:
>sudo apt-get install openssh-client
