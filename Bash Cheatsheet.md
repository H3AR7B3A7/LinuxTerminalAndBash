# Bash Cheatsheet

Bash commands with some of their arguments on the consecutive lines.

We can get a list of commands using help:

> help

We can also get more information on arguments using help as an argument:

> command --help

Or the version of the software providing a specific command, if any:

> command --version  
> command --v

## Common Commands

### Information

#### User name:
>whoami

#### System name:
>hostname

#### Manual:
>man  
> ls  
> ...


### Navigation

List content:
>ls  
> /bin/p*  
> -l -G  
> -C -b  
> -R

>ll

>dir

#### Print working directory:
>pwd

#### Change directory
>cd

#### Print files to screen
>cat

#### Print last X lines of file
>tail  
> file.txt  
> -n 1

#### Print file in pages
>less

### Creation / Alteration

#### Elevating to super user
>sudo su

To drop elevation:
>exit

#### Changing file rights
>chmod  
> 777 file.txt

![Chmod](img/chmod.png)

#### Changing owner
>chown  
> username

#### Create file
>touch  
> file.txt

#### Edit file
>vi  
> file.txt

[Vim cheatsheet](https://vim.rtorr.com)

>nano  
> file.txt

### Installations

#### Installing Git
>sudo apt-get install git

### Command Chaining Examples
Find everything in /var/log starting with syslog of type file, print with null chars for new line and individually run each with an elevated command to grant read permission to all users.
>find /var/log/syslog* -type f -print0 | xargs -0 sudo chmod a+r

Find everything in /var/log starting with syslog and ending on .gz of type file, print with null chars for new line and individually run each with an elevated command to unzip.
>find /var/log/syslog*.gz -type f -print0 | xargs -0 sudo gunzip

Find everything in /var/log starting with syslog of type file, print with null chars for new line and individually run each to concatenate in one long string and look for matching lines for "NetworkManager" that are warnings.
>find /var/log/syslog* -type f -print0 | xargs -0 cat | grep "NetworkManager.*warn"

Get IP-addresses from network interfaces, in the first result merge spaces, cut in string parts on the spaces and give me the 3d string.
>ifconfig | grep "inet " | head -n 1 | tr -s ' ' | cut -d ' ' -f 3

### Scripts

Anything you can normally run on the command line can also be put into a script for repeated use.

#### Examples

```
#!/bin/bash

originalAddress=$(   ifconfig | 
                    grep "inet " | 
                    head -n 1 | 
                    tr -s ' ' | 
                    cut -d ' ' -f 3)
                    
echo $originalAddress

echo $originalAddress >> ~/ip.txt
```