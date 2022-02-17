# Schedule 1

Target : 10.10.1.11

Credentials : thomas | PnG1E59&%P

Tags : Privilege Escalation | Linux Cron Jobs | Writable Cron Job File
***

## Flag 1: What is the UID of the user Thomas on the target machine?

`id -u` or `echo $UID`

The first command allows for options to get user id information. The second command grabs the environment variable UID.

## Flag 2: What is the name of the file that contain system-wide crontab on the target machine?

`cat /etc/crontab`

Personally, I'm converting this to memory. I believe I should know where the crontab file is usually kept on Linux systems.

## Flag 3: Who is the owner of the backup.sh script file on the target machine?

First thing I needed to figure out is where this file would be kept. 

`ls -la`

After running this command I found a folder named "scripts". Looks promising... After moving into the directory I run the same command to find the answer.

## Flag 4: What is the value in the file flag.txt at the target?

When I "cat /etc/crontab", I noticed the last listing what the backup.sh file that Thomas has access to and that this ran as root. Check mate... I knew I needed to edit the backup.sh file. However, I didn't have the addition memorized so I googled it. I have worked with Linux for many years and knew the snippet I was looking for. 

`echo "thomas ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers`

Now that I have modified the file I need to execute crontab so I can gain my new privileges.

`sh /home/thomas/scripts/backup.sh`

`sudo -i`

I now have gained root access. I have found that most flags are in the /root folder. 