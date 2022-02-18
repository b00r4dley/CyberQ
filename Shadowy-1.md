# Shadowy-1

Target : 10.10.1.6

Credentials : nicholls | Lysf%29*T&

Tags : Privilege Escalation | Linux Weak File Permissions | Writable Shadow File

I found this [resource](https://infinitelogins.com/2021/02/24/linux-privilege-escalation-weak-file-permissions-writable-etc-shadow/) helpful in this CTF.
***

## Flag 1: 

`cat /etc/passwd`
***

## Flag 2: What is the UID of the user Miller?

The result of the previous command answers this question.
***

## Flag 3: Can Nicholls write to the /etc/shadow file on the target machine?

`ls -la /etc/shadow`

Notice the read/write privileges.
***

## Flag 4: Enter the first 20 characters of the user johnson's password hash the target machine?

`cat /etc/shadow | grep "johnson" | cut -f2 -d: | cut -c 1-20` 

The first part displays the contents of the /etc/shadow file. The second part filters and displays on johson's password hash. The thrid part 'cuts' or displays on the second field using the colon as the delimeter. The last part filters it down even more by only displaying the first 20 characters.
***

## Flag 5: What is the value in the file flag.txt at the target?

Ran a similar command as above but for this time I grepped nicholls password hash and saved it to a file. Since copy and paste isn't working for me on this vm, I will have to copy it manually when I edit the shadow file.

`cat /etc/shadow | grep "nicholls" | cut -f2 -d: >> nichollsHash.txt`

`cat nicholls.txt`

From here I open a second terminal and ssh into the machine once more. I arrange the terminals so I can see nicholls password hash. I reused nicholls password hash because I already knew the password. 

In the new, second terminal I enter:

`nano /etc/shadow` 

and delete the root hash and replace it with nicholls' hash. Next I ran:

`sudo -` 

and entered nicholls password, thus gaining root privilege.

