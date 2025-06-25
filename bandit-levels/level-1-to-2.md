## 🔐 Level 1 → 2: Hidden Files, Strange Names & Terminal Fails

### 🧪 What Happened

This level taught me a LOT. I had to find a file named `-` and extract the password from it.

I started off by listing the directory:

bandit1@bandit:~$ ls
-
At first glance, it looked like there was a file literally named - (a dash). Suspicious! I tried to read it normally:
cat -
But that didn't work — it just waited for input forever and froze the terminal. I tried again with quotes:
cat "-"
Still didn’t work 😤

💡 My Aha! Moment
I figured it had something to do with how Linux interprets - as stdin. So I tried telling cat to treat - as a file in the current directory using ./:
cat ./-
Boom! It worked 🎉

The password for the next level was:
263JGJPfgU6LtdEvgfWU1XP5yac29mFx

😅 Mistakes I Made
🔸 Tried cat - which just opened stdin and did nothing useful.

🔸 Forgot Linux treats - as a special stdin indicator in many commands.

🔸 First attempted to SSH into Level 2 using the default port 22, which failed:

ssh bandit2@bandit.labs.overthewire.org
I got this warning:

!!! You are trying to log into this SSH server on port 22, which is not intended.
🔸 Then I accidentally pasted the password into terminal directly, like this:
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
… which of course returned command not found.

✅ What Worked
After figuring it out, I finally connected to Bandit Level 2 correctly:
ssh bandit2@bandit.labs.overthewire.org -p 2220

💡 What I Learned
How to handle files named with special characters (-)

Use ./filename to explicitly reference files in the current directory

Don’t assume the terminal always knows what file you mean — be precise
