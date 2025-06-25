# 🔐 Bandit Level 5 → Level 6

## 🧠 Challenge Summary
> The password for the next level is stored somewhere in the `inhere` directory. It's a human-readable file, exactly **1033 bytes** in size.

## 🧪 What Happened

This level was about precision. The inhere directory had 20 subfolders (maybehere00 → maybehere19), and inside each were several files — some hidden, some with weird names, some large or binary.

At first, I tried poking around manually, running `ls` and `cat` on a few files. But it quickly became clear: **manual searching wouldn't scale**.

So I relied on the `find` command to surgically locate the right file using the size:

find . -type f -size 1033c
Boom — it gave me exactly one match:
./maybehere07/.file2
I ran:
cat ./maybehere07/.file2
And got the password for the next level:
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
🎯 Level Complete.

😅 Mistakes I Made
❌ I started manually exploring files with cat, which was a huge waste of time.

✅ What Worked
find . -type f -size 1033c
Explanation:

. → search in current directory

-type f → look for files

-size 1033c → exact size in bytes (c = char)

Then simply:
cat ./maybehere07/.file2

💡 What I Learned
🔍 find is essential for real-world Linux work — use it to filter by file size, type, and more.

📏 Always use the c suffix when dealing with bytes in find -size.

🧼 Avoid noisy, manual work — think in filters and leverage shell tools.
