# 🔐 Bandit Level 5 → Level 6

## 🧠 Challenge Summary
> The password for the next level is hidden *somewhere* in the `inhere` directory.  
> It has **all** of these properties:
> - Human-readable  
> - Exactly **1033 bytes**  
> - **Not executable**

---

## 🧪 What Happened

- First, I `cd` into the `inhere` folder:
  ```bash
  cd inhere
Tried listing files and manually reading them with cat, but there were too many subfolders and files:

ls -l
Realized this was inefficient. Switched to using find to search for files that matched the exact byte size:

find . -type f -size 1033c
Only one match showed up:

./maybehere07/.file2
Finally, I read the contents:

cat ./maybehere07/.file2
✅ Found the password:

HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
😅 Mistakes I Made
❌ Started manually opening files — slow, messy

❌ Forgot the c suffix on the -size flag, which caused find to behave incorrectly

✅ What Worked
find . -type f -size 1033c
🔍 Narrowed down to a single file by filtering:

. = current directory

-type f = files only

-size 1033c = exactly 1033 bytes (c = characters/bytes)

Then:
cat ./maybehere07/.file2

💡 What I Learned
find is indispensable for targeted searches — don’t overlook it

File size filters must be precise, especially with suffixes (c = bytes)

Brute-force is tempting, but smart filters save time and sanity

Ready for Level 6 → 7 🚀
