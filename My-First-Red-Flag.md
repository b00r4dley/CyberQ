## Flag 1: How many TCP ports are open at `ip addr`?

`nmap -sT <target>` 

The -sT switch uses the connect() method. This command uses the high level connect system call making it less efficient than the half-open reset that a SYN scan does (-sS). Consider using SYN scan when possible. The result from this scan will provide the answer.
***

## Flag 2: What port is the Apache web server running at `ip addr`?

By default, Apache web server runs on port 80 but can always be configured to use a different port. Based on the output from the above scan, the answer should be obvious.
***

## Flag 3: What is the server flag in the Apache HTTP headers at `ip addr`?

`nmap --script=http-headers <target>`

This command performs a HEAD request for the root folder of a web server and displays the HTTP headers returned. The answer can be found where the "Server : " version is normally found.
***

## Flag 4: What is the flag on the web server at `http://ip addr`?

Visit the web page by typing the http ip address into a web browser.