🧪 Bandit Level 2 → 3
Objective:

The password for the next level is stored in a file with spaces in its filename located in the home directory.

🔐 Result
bandit2@bandit:~$ find . -name "spaces in this filename"
./spaces in this filename

bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

bandit2@bandit:~$ exit
logout
💡 What I Learned
How to search for files using the find command

How to handle filenames that contain spaces using quotes

Cleaned up my workflow and moved faster through this level than the last

🧠 How I Solved It
This level was a breeze compared to the last one. Here's how I approached it:

🔍 I suspected the file might be hidden or oddly named, so I used:
find . -name "spaces in this filename"
It quickly pointed me to:
./spaces in this filename
🧼 I remembered to wrap the filename in quotes when using it with cat:
cat "spaces in this filename"
✅ That gave me the password instantly!

🔐 I used the password to SSH into the next level:
ssh bandit3@bandit.labs.overthewire.org -p 2220
⚠️ Tips for Beginners
Filenames with spaces must be quoted or escaped. Use "filename with spaces" or filename\ with\ spaces.

Use find . -name "*something*" to locate files reliably in Bandit.

If you're confident the file is in the current directory, even a simple ls works — but find is the safer tool as levels get trickier.

✅ Next Step
Jumping into Level 3 → 4, where the password is hidden in a file that starts with a special character! Stay sharp! ⚔️
