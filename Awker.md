# Awker

Target : 10.10.1.10

Credentials : morgan | KXnjT04$*B

Tags : Privilege Escalation | Sudo Shell Escaping | Awk Binary
***

## Flag 1: What is the UID of the user Morgan on the target machine?

`id -u` or `echo $UID`

The first command allows for options to get user id information. The second command grabs the environment variable UID. 

## Flag 2: What is the command to check sudo privileges of a user on the system?

`sudo -l`

I tried many different commands before I read the `sudo --help` page. I tried `su -u` and `sudo -i` with no luck. I honestly didn't think this was going to do anything but since you learn more by failing, I allowed myself to mess around and to see what would happen. The result from this command displayed information that was interesting -- I saw the word '(root)'. 

Always read the help or man pages for a better understanding of what you can do with a particular program. 

## Flag 3: Which binary command may Morgan run without a root password of the target machine?

The result from the previous command will provide you with the answer.

## Flag 4: What is the value in the file flag.txt at the target machine?

When I started this flag, I knew, more or less, what awk was but I didn't have a thorough understanding. So I started googling and read a number of stackoverflow posts with no luck. I was getting extremely frustrated. I got stuck multiple times and had to restart (reset my thinking) from the beginning. I even watched a YouTube video to help me understand awk but it was not very helpful. I went back to googling different things about awk. Then finally I had a break through. I googled "awk with root privileges". The first result had what I was looking for. [www.hacknos.com](https://www.hacknos.com/awk-privilege-escalation/) It's amazing how a carefully worded search in google can make all the difference. 

`awk 'BEGIN{system("</bin/bash>")}'`

Now that I have found the right command, it's time to research what this command does and understand why it worked. 