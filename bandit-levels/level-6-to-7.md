# 🔐 Bandit Level 6 → Level 7 (OverTheWire Linux Wargame)

---

## 🧠 Challenge Summary

The password for the next level is hidden somewhere on the server and has all of the following properties:

- Owned by user: `bandit7`
- Owned by group: `bandit6`
- Exactly **33 bytes** in size

Commands allowed and useful for this challenge include: `ls`, `cd`, `cat`, `file`, `du`, `find`, and `grep`.

---

## 🧪 What Happened

This level was about combining file ownership and size filters to locate a very specific file across the server.  

I started in my home directory (`cd ~`) but since the password file could be anywhere, I decided to search from the root directory `/` to cover all bases.

The key was to use the `find` command with multiple filters:

find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
Breaking down the command:

/ → Start searching from the root directory

-user bandit7 → Only files owned by user bandit7

-group bandit6 → Only files owned by group bandit6

-size 33c → Files exactly 33 bytes in size (c stands for bytes)

2>/dev/null → Suppress permission denied errors for cleaner output

After a brief wait, the command returned exactly one file path.

Then I used:

cat /path/to/found/file
To display the file contents and retrieve the password.

😅 Mistakes I Made
❌ Initially tried searching manually with ls and cat in common directories — too slow and inefficient.

❌ Forgot to suppress permission errors at first, which cluttered the output.

❌ Almost overlooked combining both user and group ownership filters in the find command.

✅ What Worked
The winning command was:

find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
This efficiently filtered the entire filesystem to just one file matching all criteria.

Following it up with:

cat /path/to/found/file
Allowed me to read the password and move on to the next level.

💡 What I Learned
🔍 Combining multiple filters in find makes it extremely powerful for pinpointing files.

📏 Always use the c suffix in -size to specify size in bytes exactly.

🧼 Redirecting error output (2>/dev/null) keeps output clean and focused, especially when searching system directories without root access.

🌍 Starting from / ensures you don’t miss files buried deep outside your home directory.
