# Red Flags

## Flag 1: What is the MySQL version running at `ip addr`?

`nmap -sV <ip address>`

Alternatively, you could use the -A switch which enables version detection among other things. I ran both to see if there was a difference in the time each scan took. For this machine with 3 ports open, the -A switch took less than two seconds longer. The answer is in the format 2.7.12 .
********************************

## Flag 2: What is the Apache version at `ip addr`? 

The previous scan format will allow you to answer this question. Be sure to check the IP address.
********************************

## Flag 3: What was the last CVE recorded for this MySQL version in 2020. 

For this question, I researched commands that would find this information for me. It appears that nmap has some options that will try to detect CVEs based on the version of the software running. However, I found this approach unfruitful. I finally found the answer by using [Mitre's CVE search engine](https://cve.mitre.org/cve/search_cve_list.html). Once on the site, I entered `mysql <version>`. I entered the first result to get the correct answer. 
********************************
********************************

# Blue Flags

## Flag 1: What TCP port is the MySQL server listening on at `ip addr`?

Honestly, you should know the answer (or have a very educated guess) without having to do any research or scans. But you will find the answer in the previous scans. 