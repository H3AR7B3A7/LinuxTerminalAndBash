# Bash Shell Cheatsheet

Bash commands with some of their arguments on the consecutive lines.

We can get a list of commands using help:

> help

We can also get more information on arguments using help as an argument:

> command --help

Or the version of the software providing a specific command, if any:

> command --version  
> command --v


## Shortcuts

**Arrow Up / Down** : Navigate command history  
**Tab** : Autocomplete  
**Ctrl + L** : Clear  
**Ctrl + C** : Kill current running task  
**Ctrl + D** : Exit shell  
**Ctrl + Z** : Current running task to background  
**Alt + F** : Move cursor forward one word  
**Alt + B** : Move cursor back one word  
**Esc + T** : Swap last two words before cursor  
**Ctrl + A** : Go to the beginning of the line  
**Ctrl + E** : Go to the end of the line  
**Ctrl + W** : Delete word before cursor  
**Ctrl + K** : Clear line behind cursor  


## Common Commands

### Information

#### Username:
>whoami

#### System name:
>hostname

#### Manual:
>sudo apt-get install man-db

>man  
> ls  
> ...

#### Network routing:
>ip rout show

#### Check for DHCP server in network:
>sudo dhclient

#### Lookup IP address:
>ip addr

#### Network interfaces and usage
>netstat -i

#### Open and listening ports
>netstat -l

>ss -i

#### Get DNS ip
>host google.com

#### Check if network address is live
>ping 8.8.8.8

#### Current DNS configurations
>systemd-resolve --status


### Navigate & Open

#### List content:
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

#### Locate file
>sudo apt-get install mlocate

>locate filename

#### Print files to screen
>cat

#### Print last X lines of file
>tail  
> file.txt  
> -n 1
> -f

#### Print file in pages
>less

#### List loaded modules
>lsmod

#### Load module
>modprobe name


### Create & Alter

#### Elevating to super user
>sudo su

To drop elevation:
>exit

#### Non-Interactive Download
>wget
> wordpress.org/latest.tar.gz

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

*More info: [Vim cheatsheet](https://vim.rtorr.com)

>nano  
> file.txt

#### Zip / Unzip file
Zip:
>zip name.zip filename filename ...

>unzip name.zip

Gzip:
>gzip filename

>gunzip filename

Tar:
>tar cvzf name.tar fileOrFoldername

>tar -xvf name.tar

>tar cvzf name.tar.gz fileOrFoldername

>tar -xvf name.tar.gz

>tar cvzf name.tgz fileOrFoldername

>tar -xvf name.tgz

*More info: [Zip Format Differences](https://upengareri.github.io/compression_and_archiving/)


## Command Insertion
List kernel module files for current kernel version.
>ls /lib/modules\`uname -r\`


## Command Chaining

Append contents of group filtering only lines with username to file.
>cat /etc/group | grep name >> file

Overwrite contents of group filtering only lines with username to file.
>cat /etc/group | grep name > file

Cut contents using colon as field delimiter keeping the 3d field and sorting them in natural order.
>cut -d: -f3 /etc/group | sort -n

Cut contents using colon as field delimiter keeping the 3d field and sorting them in descending order.
>cut -d: -f3 /etc/group | sort -rn

Find everything in /var/log starting with syslog of type file, print with null chars for new line and individually run each with an elevated command to grant read permission to all users.
>find /var/log/syslog* -type f -print0 | xargs -0 sudo chmod a+r

Find everything in /var/log starting with syslog and ending on .gz of type file, print with null chars for new line and individually run each with an elevated command to unzip.
>find /var/log/syslog*.gz -type f -print0 | xargs -0 sudo gunzip

Find everything in /var/log starting with syslog of type file, print with null chars for new line and individually run each to concatenate in one long string and look for matching lines for "NetworkManager" that are warnings.
>find /var/log/syslog* -type f -print0 | xargs -0 cat | grep "NetworkManager.*warn"

Get IP-addresses from network interfaces, in the first result merge spaces, cut in string parts on the spaces and give me the 3d string.
>ifconfig | grep "inet " | head -n 1 | tr -s ' ' | cut -d ' ' -f 3


## Standard Streams

- Standard Input (stdin): 1
- Standard Output (stdout): 1
- Standard Error (stderr): 2


## Running Scripts

Anything you can normally run on the command line can also be put into a script for repeated use.
A user will not have permission to run a saved script by default. We need to grant it first:

>chmod a+x script.sh

To run the script:
>./script.sh

To schedule scripts with CRON:
>crontab -e

Edit the file to run a script every minute:
```
* * * * * ~/script.sh
```

### Example Scripts

Print IP:
```
#!/bin/bash

originalAddress=$(   ifconfig | 
                    grep "inet " | 
                    head -n 1 | 
                    tr -s ' ' | 
                    cut -d ' ' -f 3)

echo $originalAddress >> ~/Desktop/ip.txt
```

Print date and IP in an endless loop:
```
#!/bin/bash

while [ : ]
do

	originalAddress=$(   ifconfig | 
		            grep "inet " | 
		            head -n 1 | 
		            tr -s ' ' | 
		            cut -d ' ' -f 3)

	echo "$(date) $originalAddress" >> ~/Desktop/ip.txt
	
	sleep 10
done
```
To watch the output updating every 10s:
>tail ip.txt -f

