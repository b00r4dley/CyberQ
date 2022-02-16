# Red Flags

## Flag 1: How many TCP ports are open at `ip addr`?

`nmap -sS <ip addr>`

SYN scan; half-open scan. For a full connect() scan use -sT.
********************************

## Flag 2: What is the server flag in the Apache HTTP headers at `ip addr`?

`nmap --script=http-headers -p 80 10.10.1.101`

This command performs a HEAD request for the root folder of a web server and displays the HTTP headers returned. The answer can be found where the "Server : " version is normally found.
********************************

## Flag 3: What port is the Apache web server running at `ip addr`?

By default, Apache web server runs on port 80 but can always be configured to use a different port. Based on the output from the above scan, the answer should be obvious.
********************************

## Flag 4: What is the flag on the web server at `http://ip addr`?

Visit the web page by typing the http ip address into a web browser.

********************************
## Flag 5: How many TCP ports are open below 1024 at `ip addr`?

`nmap -p -1023 <ip addr>`

By default, nmap scans the top 1000 ports. To specify a range, use the -p switch. -p 1-1023 and -p -1023 specifies the same range.

********************************
********************************
# Blue Flags

## Flag 1: What is the cleartext password of sadmin at FRF?

Towards the bottom of the screen, there are three buttons; one is labeled FRF. Select FRF. On the left side of the screen there is a system heading with a down arrow. Expand this option. Credentials are listed in cleartext. 
********************************

## Flag 2: What is the flag in the file ftp_flag.txt at FBF?

Towards the bottom of the screen, there are three buttons; one is labeled FRF. Select FBF. Click the Ctl-Alt-Del text just right of the console. Use the credentials listed to the left of the screen under system. Once on the desktop of the system, open File Explorer (folder icon in the toolbar). In the search bar at the top right of the window, enter ftp_flag.txt. The file should be listed in the results. Double-click the result and you'll find the flag. 
********************************

## Flag 3: What is the cleartext password of Administrator at FBF?

Towards the bottom of the screen, there are three buttons; one is labeled FBF. Select FBF. On the left side of the screen there is a system heading with a down arrow. Expand this option. Credentials are listed in cleartext. 