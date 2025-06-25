# 🔐 **Bandit Level 9 → 10 Walkthrough**  
**OverTheWire: Linux Wargame**

---

## 🎯 **Goal**  
Find the password for **bandit10** by analyzing a file called `data.txt`.  
The password is **surrounded by `==` symbols** inside the file.

---

## 🧪 **What Happened**

I started by trying to search for the pattern directly using `grep`:

grep "===" data.txt
But I got:
grep: data.txt: binary file matches
This told me grep found a match, but didn’t want to display it because the file is a binary file.

I tried again just to be sure:
grep == data.txt
Same result.

Then I tried this (but made a small typo):

string == data.txt
and got a helpful system suggestion:
Command 'string' not found, did you mean: 'strings'

🤔 My Thought Process
I realized I needed to extract human-readable content from a binary file. I remembered from previous Linux research that the strings command is designed exactly for this: pulling readable text from non-text files.

🔎 Solution
I ran:

strings data.txt | grep "=="
And got:

========== the
========== password{k
=========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
I could now clearly see the password line!

✅ Result
The correct password is:

FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
🚀 Next Steps
I exited bandit9 and logged into bandit10 using:

ssh bandit10@bandit.labs.overthewire.org -p 2220
When prompted, I entered the password found above.

📘 What I Learned
Binary files need special handling — don’t assume everything is readable by cat or grep.

strings is a powerful tool for extracting readable content from binary or compiled files.

The DevOps mindset is about adapting and using the right tool for the right context.

