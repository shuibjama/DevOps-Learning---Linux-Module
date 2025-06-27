🚀 OverTheWire Bandit Level 19 → 20
What I did:
I listed the files in my home directory on bandit19:

ls
I spotted the setuid binary bandit20-do owned by bandit20:

ls -la .
# -rwsr-x--- 1 bandit20 bandit19 14884 Apr 10 14:23 bandit20-do
🔑 This means the binary runs with bandit20’s privileges.

I ran the binary to see what it does:

./bandit20-do id
Output:

uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
👀 It confirmed the binary runs as bandit20.

I used the binary to read bandit20’s password file:

./bandit20-do cat /etc/bandit_pass/bandit20
And got:

0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
🎉 Password acquired!

Tried SSH directly from inside bandit19 to bandit20:

ssh bandit20@bandit.labs.overthewire.org -p 2220
After accepting the host key and entering the password, I got this message:

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

bandit20@bandit.labs.overthewire.org: Permission denied (publickey).
❌ SSH from localhost inside the server is blocked!

I accidentally ran the password as a command:

0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Which gave:

command not found
🤦‍♂️ Of course — it’s a password, not a command!

Tried SSH again from inside the server — same error.

Realized the right approach:

Exit fully from the bandit server to my local machine:
exit

Then SSH into bandit20 from my own local terminal:
ssh bandit20@bandit.labs.overthewire.org -p 2220

Enter the password
✅ And I’m in!

Summary & Lessons
The bandit20-do binary lets me read the next level’s password because it runs as bandit20.

SSH connections from inside the server itself are blocked for password logins (to save resources).

Always exit back to your local machine before SSH-ing to the next level.

Don’t run passwords as commands! 😅
