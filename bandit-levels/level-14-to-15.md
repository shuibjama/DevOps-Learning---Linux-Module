# OverTheWire Bandit Level 14 → Level 15 🚀

---

## What I Did and Learned 🧑‍💻

At **level 14**, I was logged in as user `bandit14`. The goal was to get the password for the next level (bandit15). Unlike previous levels, this time the password is not just in a file I can read directly. Instead:

- The password is stored in `/etc/bandit_pass/bandit14`, but only the user `bandit14` can read it 🔐
- To get the next password, I needed to submit the current password to a service running on **localhost port 30000** 🖥️⚡
- Once I sent the correct password to this port, the service would respond with the next level’s password 🗝️

---

### Step 1: Confirm Who I Am 🕵️‍♂️

bandit14@bandit:~$ whoami
bandit14
I double-checked I was the correct user, bandit14, since the file permissions would only allow me to read /etc/bandit_pass/bandit14.

Step 2: Read the Current Password 📄

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
I read the password for this level from the file.

Step 3: Trying to Connect to Port 30000 🔌
First, I tried to connect manually with:

bandit14@bandit:~$ nc localhost 30000
But nothing happened (or it just hung). I had to exit with Ctrl+C ⏹️.

Step 4: Send Password to the Service on Port 30000 📤📥
Then, I remembered I can pipe the password directly into nc (netcat) like this:

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
The service responded with the string after "Correct!", which is the password for the next level 🔑.

Step 5: Exit Bandit14 Session 👋

bandit14@bandit:~$ exit
logout
Connection to localhost closed.
Step 6: Exit Bandit13 Session (Where I Initially SSHed In) 🔐

bandit13@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
Step 7: SSH Into Bandit15 🚪
At first, I made a mistake typing the SSH command:

sjama@ShuibJama:~$ bandit15@bandit.overthewire.org -p 2220
bandit15@bandit.overthewire.org: command not found
I forgot to type ssh before the command.

Then I tried:

sjama@ShuibJama:~$ ssh bandit15@bandit.overthewire.org -p 2220
ssh: Could not resolve hostname bandit.overthewire.org: Name or service not known
This was because the hostname was incorrect (bandit.overthewire.org does not exist) ❌.

Finally, I corrected the hostname:

sjama@ShuibJama:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
This connected me successfully to bandit15 🎉.

Summary 📝
I learned how to send data to a specific port on localhost using nc and pipe 🔄

I practiced troubleshooting SSH connection issues, specifically resolving hostnames 🛠️

This step taught me how services can require interaction over TCP ports to get secrets instead of just reading files 🔍

I improved command syntax and error handling by correcting typos and understanding DNS resolution 🧠

Commands I Used and Why:
whoami	Confirmed my current user
cat	Read the password file
nc (netcat)	Connected to localhost on port 30000 to send password and receive next password
exit	Logged out from current SSH sessions
ssh	Connected to next Bandit level using correct hostname and port

