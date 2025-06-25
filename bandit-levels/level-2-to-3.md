🔐 Level 2 → 3: Quoted Filenames & find to the Rescue
🧪 What Happened
This level was smoother than the last — I was tasked with finding and reading a file that had spaces in its name. That’s the twist.

I tried checking what was in the current directory:

bash
Copy
Edit
bandit2@bandit:~$ ls
spaces in this filename
I knew right away this would cause trouble if I wasn’t careful. A filename like that needs to be quoted or escaped. But I wanted to play smart, so I used:

bash
Copy
Edit
bandit2@bandit:~$ find . -name "spaces in this filename"
That confirmed the file existed with the exact name. Then I used cat with quotes:

bash
Copy
Edit
bandit2@bandit:~$ cat "spaces in this filename"
And boom — the password popped out instantly:

MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

😅 Mistakes I Made
🔸 None this time! 🎉
I applied what I learned from the last level and avoided terminal confusion by quoting the filename immediately.

✅ What Worked
✔️ Used find . -name "filename" to safely search for exact names
✔️ Quoted the filename properly when using cat
✔️ Quickly exited and moved to the next level using:

bash
Copy
Edit
ssh bandit3@bandit.labs.overthewire.org -p 2220
💡 What I Learned
🔹 Files with spaces must be quoted when used in commands

🔹 find is a powerful way to locate files — especially when you’re unsure where exactly they are

🔹 Terminal precision is everything. One misquote or space can throw off a whole command

