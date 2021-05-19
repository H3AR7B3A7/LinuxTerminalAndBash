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

