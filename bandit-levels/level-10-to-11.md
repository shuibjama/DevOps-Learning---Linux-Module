# 🔐 **Bandit Level 10 → 11 Walkthrough**  
**OverTheWire: Linux Wargame**

---

## 🎯 **Goal**  
Extract the password for **bandit11** from a file named `data.txt`, which contains a **Base64-encoded string**.

---

## 🧪 **What Happened**

I started by listing the contents of the home directory:

bandit10@bandit:~$ ls
data.txt
Then I checked what was inside the file:

bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
This string looked like random letters — but I suspected it was encoded.

😅 Mistake I Made
I tried decoding it without fully understanding how base64 works:

cat data.txt base64 -d
But got an error:

cat: invalid option -- 'd'
Try 'cat --help' for more information.
At that point, I paused and did some quick research on what Base64 actually is, and how the base64 command works in Linux — especially the -d flag for decoding.

🔎 Research Break
I learned:

The string was Base64, a common encoding format for text and binary data.

The correct usage is to pipe data into base64 using |.

-d means decode.

✅ What Worked
After returning with better understanding, I ran:

cat data.txt | base64 -d
That decoded the string correctly and returned:


The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
💡 What I Learned
Don’t panic when something fails — pause, research, and adapt.

base64 -d is the correct syntax to decode Base64 strings in Linux.

Understanding encoding formats is critical for DevOps, CTFs, and security work.

The | (pipe) operator is essential for chaining Linux commands efficiently.

🚀 Next Step
I exited the session:

bandit10@bandit:~$ exit
Then logged into the next level:

ssh bandit11@bandit.labs.overthewire.org -p 2220
