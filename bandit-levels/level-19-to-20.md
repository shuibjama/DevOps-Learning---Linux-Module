
# OverTheWire Bandit Level 19 → 20 🚀

I started this challenge by exploring my home directory to see what files might help me move to the next level.

```bash
bandit19@bandit:~$ ls
bandit20-do
````

There was only one file named `bandit20-do`. I checked its details and permissions to understand what it is.

```bash
bandit19@bandit:~$ ls -la .
total 36
drwxr-xr-x  2 root     root      4096 Apr 10 14:23 .
drwxr-xr-x 70 root     root      4096 Apr 10 14:24 ..
-rwsr-x---  1 bandit20 bandit19 14884 Apr 10 14:23 bandit20-do
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root     root       807 Mar 31  2024 .profile
```

The file `bandit20-do` had the **setuid** bit set (`rws`), meaning it would execute with the permissions of `bandit20` user, not mine (`bandit19`). This was a big hint.

To confirm, I ran a simple command using it:

```bash
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
```

The effective user ID was indeed `bandit20`. So I realized I could run commands as that user by using this binary.

Next, I tried to read the password file for bandit20 by running:

```bash
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

Success! 🎉 The password for the next level was revealed.

I then tried to SSH into bandit20:

```bash
bandit19@bandit:~$ ssh bandit20@bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit19/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit19/.ssh/known_hosts).

                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

bandit20@bandit.labs.overthewire.org: Permission denied (publickey).
```

This error meant I was trying to SSH from within the bandit19 server itself (localhost), which is blocked to save resources.

So, I exited bandit19:

```bash
bandit19@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```

Finally, I connected directly from my own computer:

```bash
sjama@ShuibJama:~$ ssh bandit20@bandit.labs.overthewire.org -p 2220
```

I entered the password I found, and it worked perfectly.

---

**Summary:**

* Found a setuid binary `bandit20-do` owned by bandit20.
* Used it to run commands as bandit20, including reading the password file.
* Tried SSH from localhost but was blocked.
* Exited and SSH’d directly from my own machine using the retrieved password.

This was a great lesson on understanding permissions and carefully reading error messages! 👍
