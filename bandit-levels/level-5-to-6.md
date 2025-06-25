# 🔐 Level 5 → 6

---

## 🧪 What Happened

This level was a mental shift. The instructions told me:

> "The password is *stored somewhere* in the `inhere` directory and has *human-readable* content, is *1033 bytes in size*, and is *not executable*."

There were **20 subdirectories** (`maybehere00` to `maybehere19`), each filled with multiple hidden and oddly named files. At first, I tried manually `cat`-ing through each one — not scalable.

I had to refine my approach.

Eventually, I discovered the magic combo:

find . -type f -size 1033c ! -executable

This command surgically filtered out the noise and gave me exactly one match:
→ ./maybehere07/.file2

Then:
cat ./maybehere07/.file2
Boom — the password was in there 🎯

😅 Mistakes I Made
❌ I started grepping or manually cat-ting into individual files across folders, which quickly got tedious and error-prone.

❌ I forgot how specific the find command can be — I initially used 1033 instead of 1033c (bytes).

❌ I overlooked the ! -executable part, which is crucial since only non-executable files were candidates.

✅ What Worked
After trial and error, I settled on:
find . -type f -size 1033c ! -executable
Explanation:

. → start in current directory

-type f → look for files

-size 1033c → match size exactly in bytes (c = char)

! -executable → ignore binaries/scripts

Then simply:
cat ./maybehere07/.file2
💡 What I Learned
🔍 find is extremely powerful for narrowing down file searches based on properties like size, permissions, types, etc.

📏 When a file size is given in bytes, always use the c suffix in find -size.

⚙️ When instructions mention "not executable", use ! -executable to filter correctly.

🚫 It's inefficient to check everything manually — let the tools filter things for you.
