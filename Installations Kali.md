# Kali Installations

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
>sudo apt-get upgrade -y  
>sudo apt-get dist-upgrade -y

### Removing Software

To remove packages installed with APT:
>sudo apt-get remove name


## Common Installations

### Preload

>sudo apt-get install preload

### Bleachbit

>sudo apt-get install bleachbit

### Scrub

>sudo apt-get install scrub 

### Lolcat

>sudo apt-get install lolcat

### Figlet + More Figlet Fonts

>sudo apt-get install figlet

>cd /usr/share

>sudo git clone https://github.com/xero/figlet-fonts

>sudo mv figlet-fonts/* figlet && sudo rm -rf figlet-fonts

>showfigfonts

### Cmatrix

>sudo apt-get install cmatrix

### Tor

>sudo apt-get install tor

### Proxychains

>sudo apt-get install proxychains

>sudo updatedb

### Chkrootkit

>sudo apt-get install chkrootkit

### Metagoofil

> sudo apt-get install metagoofil

### Libre Office

>sudo apt-get install libreoffice





