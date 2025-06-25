# 🔐 Level 4 → 5: Files Starting With a Dash (-) & Hidden Characters

---

## 🧪 What Happened  
This level was all about dealing with files that start with a dash (`-`), which can confuse commands like `cat` because the dash is often interpreted as an option flag rather than a filename.

I started by listing the files inside the `inhere` directory:

bandit4@bandit:~$ ls -h
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls -h
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
I then tried to read the files normally:
bandit4@bandit:~/inhere$ cat ./file00
cat: ./file00: No such file or directory

Since the files start with a dash, I had to tell the shell explicitly that I meant a file and not an option. So I used ./ to prefix the filename and tried to cat them:
bandit4@bandit:~/inhere$ cat ./-file00
�ŉOT���S �plS]-EH�t�:-�Z�

Some files contained gibberish, but finally:
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
This was the password for the next level!

😅 Mistakes I Made
Tried cat -file00 without ./ and it failed or behaved unexpectedly.

Ignored the fact that - at the start is treated as a flag, so commands need a ./ prefix.

Tried to read normal file names without considering the dash prefix.

✅ What Worked
Using cat ./-file07 to read the file starting with a dash correctly.

Understanding the ./ prefix tells the terminal "this is a file in the current directory," not a flag.

💡 What I Learned
Files starting with a dash - can cause commands to think they’re options.

Prefixing with ./ avoids this confusion and ensures the command treats it as a filename.

The ls command with -a or -h shows hidden files or human-readable sizes but sometimes you just need to experiment with options.

Bonus: My Random cd Move
After finding the password, I randomly cded back to the home directory before exiting the session:
bandit4@bandit:~/inhere$ cd
bandit4@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

Next Step: Connected to Level 5 using the new password with:

ssh bandit5@bandit.labs.overthewire.org -p 2220

