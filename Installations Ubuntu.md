# Ubuntu Installations

## Before Starting

When uncertain about a packet name we can use:
>apt search name

Installing files can only be done by a superuser.
We can either elevate our command temporarily by using:
>sudo

Or by elevating ourselves to superuser (not recommended):
>sudo su

### Updating

Before installing anything we might want to update the *advanced packaging tool*:
>sudo apt-get update  

Our packages:  
>sudo apt-get upgrade -y  

Our OS:
>sudo apt-get dist-upgrade -y


## Common Commands

### Installing Packages

> sudo apt-get install package-name package-name ...

### Installing DEB Packages

>sudo dpkg -i path_to_deb_file.deb

### Download Packages

> sudo apt-get install --download-only package-name package-name ...

### Removing Software

To remove packages installed with APT:
>sudo apt-get remove package-name package-name ...

### Clean Up Downloaded Packages

>sudo apt-get clean


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

### Terminator

>sudo apt-get install terminator

### ZSH + Oh My ZSH

>sudo apt-get install zsh

>chsh -s $(which zsh)

>sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

For more customization tips go [here](https://maxim-danilov.github.io/make-linux-terminal-great-again/).

### Powerline Fonts

>sudo apt-get install fonts-powerline

### RipGrep

>sudo apt install ripgrep

### Silver Searcher AG

>sudo apt install silversearcher-ag