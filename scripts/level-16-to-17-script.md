bandit16@bandit:~$ mkdir /tmp/level17
mkdir: cannot create directory ‘/tmp/level17’: File exists

bandit16@bandit:~$ mkdir /tmp/levels17

bandit16@bandit:~$ ls /tmp/level17
private.key

bandit16@bandit:~$ nano private.key
Unable to create directory /home/bandit16/.local/share/nano/: No such file or directory

bandit16@bandit:~$ cd /tmp/level17

bandit16@bandit:/tmp/level17$ cat private.key
-----BEGIN RSA PRIVATE KEY-----
... (key contents)
-----END RSA PRIVATE KEY-----

bandit16@bandit:/tmp/level17$ chmod 400 private.key

bandit16@bandit:/tmp/level17$ ls -l
total 4
-r-------- 1 bandit16 bandit16 1675 Jun 27 18:17 private.key

bandit16@bandit:/tmp/level17$ ssh -i private.key bandit17@localhost -p 2220
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit16/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).
