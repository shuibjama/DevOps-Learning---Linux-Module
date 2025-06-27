# OverTheWire Bandit Level 19 → 20 🚀

Here’s how I tackled the challenge step-by-step, with some trial and error and important lessons along the way.

---

### Step 1: Checking the files in the home directory

I started by listing the files:

bandit19@bandit:~$ ls
bandit20-do
There’s a single executable file called bandit20-do.

Step 2: Inspecting file permissions and details
I wanted to see the permissions and ownership:

bandit19@bandit:~$ ls -la .
total 36
drwxr-xr-x  2 root     root      4096 Apr 10 14:23 .
drwxr-xr-x 70 root     root      4096 Apr 10 14:24 ..
-rwsr-x---  1 bandit20 bandit19 14884 Apr 10 14:23 bandit20-do
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root     root       807 Mar 31  2024 .profile
The important bit is that bandit20-do has the setuid bit set (-rwsr-x---).

It is owned by user bandit20 and group bandit19.

This means when I run this program, it executes with the permissions of bandit20 user — key to escalating privileges here! 🔑

Step 3: Running the program with a simple command
To understand what this program does, I tried running it with a common command like id to see the user context:

bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
✅ The effective user ID (euid=11020(bandit20)) shows it’s running as bandit20, confirming setuid is working.

Step 4: Using the program to read the password file
Next, I tested if I could use it to read the next level's password file, by passing the command to cat the password file:

bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Boom! 🎉 The program lets me run commands as bandit20, so I can read the password for the next level.

Step 5: Logging into the next level
With the password in hand, I attempted to SSH into bandit20:

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
🔍 The important message:
"You are trying to log into this SSH server with a password on port 2220 from localhost. Connecting from localhost is blocked."

This means I can’t SSH to the next level from within the same session on the server. I need to log out of bandit19 and SSH directly from my own machine.

Step 6: Exiting and logging in from my own machine
I exited bandit19:

bandit19@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
Then on my local machine terminal, I SSH’ed directly into bandit20 using the password I found:

sjama@ShuibJama:~$ ssh bandit20@bandit.labs.overthewire.org -p 2220
Summary & Lessons Learned 📚
The setuid bit lets you run executables with the permissions of another user — essential for privilege escalation.

Running ./bandit20-do with commands as arguments lets me act as bandit20.

Cannot SSH into bandit20 from the same server, need to SSH directly from my own machine.

Reading error messages carefully is crucial; they guide your next steps.

This was tricky but a great step toward understanding Linux permissions and privilege escalation!
