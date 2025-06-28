bandit17@bandit:~$ ls
passwords.new  passwords.old

bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y

bandit17@bandit:~$ exit
logout
Connection to localhost closed.

bandit16@bandit:/tmp/level17$ ssh -i private.key bandit18@localhost -p 2220
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit16/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).
