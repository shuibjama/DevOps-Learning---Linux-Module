# 🚀 Bandit Level 16 → 17: Using a Private SSH Key to Login 🔐

This level was by far the toughest one I've faced so far. It really tested my patience and understanding of SSH keys and Linux permissions. Here's a step-by-step recount of how I approached it, including the many trial and errors along the way. 😅

---

### 🏁 Starting Point

At the beginning, I tried to create a working directory to keep things organized:

bandit16@bandit:~$ mkdir /tmp/level17
mkdir: cannot create directory ‘/tmp/level17’: File exists
bandit16@bandit:~$ mkdir /tmp/levels17
I realized /tmp/level17 already existed, so I created /tmp/levels17 instead, but then noticed I kept using the original /tmp/level17 directory anyway. 🤦‍♂️

🔍 Finding the Private Key
I listed files inside /tmp/level17:

bandit16@bandit:~$ ls /tmp/level17
private.key
There it was — private.key. 🗝️

📝 Opening the Private Key File
I tried opening it with nano, but I got an error:

bandit16@bandit:~$ nano private.key
Unable to create directory /home/bandit16/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.
So nano wasn’t working due to permission issues, but no worries — I just used cat to view the key:

bandit16@bandit:/tmp/level17$ cat private.key
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
...
-----END RSA PRIVATE KEY-----
🔒 Setting Permissions Correctly
Before using the key, I needed to restrict permissions or SSH would complain:

bandit16@bandit:/tmp/level17$ chmod 400 private.key
bandit16@bandit:/tmp/level17$ ls -l
total 4
-r-------- 1 bandit16 bandit16 1675 Jun 27 18:17 private.key
🛠️ Trying to SSH into the Next Level
I ran the SSH command with the private key:

bandit16@bandit:/tmp/level17$ ssh -i private.key bandit17@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit16/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).

😓 Challenges & Lessons
I faced permission errors trying to save the SSH host key because the .ssh directory didn't exist and I had no rights to create it. It was a bit frustrating but didn't stop me.

The warning about the host authenticity was expected and safe to accept by typing yes.

The crucial part was realizing I had the private key and was using it correctly, so the login worked despite the warnings.

🎉 Success!
After accepting the host key, I gained access to the next level.

📝 Summary
This level taught me:

How to handle and set permissions for private SSH keys (chmod 400).

That permission errors in the home directory don’t necessarily block SSH login when using a private key.

How to carefully read and understand SSH connection messages.

It was the toughest level yet, but also one of the most rewarding! 💪🔥

