# Bash Scripts

Anything you can normally run on the command line can also be put into a script for repeated use.


## Running Scripts

A user will not have permission to run a saved script by default. We need to grant it first:

>chmod a+x script.sh

To run the script:
>./script.sh


## Scheduling Scripts

To schedule scripts with CRON:
>crontab -e

Edit the file to run a script every minute:
```
* * * * * ~/script.sh
```


## Example Scripts

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
