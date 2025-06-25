## 🔐 Level 2 → 3: Finding Files with Spaces in the Name

---

### 🧪 What Happened

This level was about finding and reading a file with **spaces in its filename** — a great little challenge in terminal navigation and quoting.

When I first connected:

bandit2@bandit:~$ ls
spaces in this filename
Okay, cool — there's a file literally called: spaces in this filename. I know that when filenames have spaces, I need to quote the string or escape the spaces. I wanted to be thorough, so I used the find command first to confirm its existence:

find . -name "spaces in this filename"
That gave me:

./spaces in this filename
Now I just needed to cat the file, so I used quotes:

cat "spaces in this filename"
And it worked! 🎉

The password for the next level was:

MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
😅 Mistakes I Made
🔸 At first, I didn’t quote the filename — which would have broken the cat command if spaces were unescaped.

🔸 I didn’t actually make major mistakes here, but I used find out of habit just to confirm the file exists — not necessary, but helpful.

✅ What Worked

cat "spaces in this filename"
✅ Quoting filenames with spaces
✅ Using find to be extra sure
✅ Smooth connection to the next level:

ssh bandit3@bandit.labs.overthewire.org -p 2220
💡 What I Learned
Quoting filenames with spaces is essential. Either "double quotes" or escaping with backslashes (\ ) works.

The find command is powerful for discovering files by name.

Sometimes the level is easier than expected — but it’s still worth approaching it methodically.
