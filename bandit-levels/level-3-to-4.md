# 🔐 Level 3 → 4: Hiding in Plain Sight

---

### 🧪 What Happened

This level was sneaky — the password was hidden in a file with a very odd name. I had to dig into hidden files and directories to find it.

I started by listing all files, including hidden ones:

bandit3@bandit:~$ ls -a .
.  ..  .bash_logout  .bashrc  inhere  .profile
There was a suspicious-looking directory called inhere. I jumped into it:

bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
It looked empty. Out of curiosity, I tried:

bandit3@bandit:~/inhere$ cat inhere
cat: inhere: No such file or directory
Still nothing. Then I used ls -a to see everything, even files that try to hide:

bandit3@bandit:~/inhere$ ls -a .
.  ..  ...Hiding-From-You
Boom — found a file named ...Hiding-From-You. Weird name, but worth a shot:

bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
Got the password instantly 🎯

Then I instinctively typed cd out of habit and ended up back in the home directory before exiting:

bandit3@bandit:~/inhere$ cd
bandit3@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

😅 Mistakes I Made
🔸 Assumed the file might be named inhere, tried to cat it blindly.

🔸 Forgot that ls doesn’t show hidden files by default.

🔸 Nearly missed the hidden file ...Hiding-From-You due to how strange it looked.

🔸 Randomly typed cd after finishing, no real reason 😅

✅ What Worked
✔️ Used ls -a to reveal hidden content in the directory.

✔️ Trusted my instinct when the directory looked empty — and dug deeper.

✔️ Used cat on the oddly named file and successfully retrieved the password.

💡 What I Learned
Always use ls -a if something seems off — many files are hidden on purpose.

Linux doesn’t care how weird a filename looks — if it exists, you can read it.

Don’t make assumptions based on names — verify everything.

Be methodical and check everything, even if it “looks” empty.

✅ Onward to Level 4 → 5!
