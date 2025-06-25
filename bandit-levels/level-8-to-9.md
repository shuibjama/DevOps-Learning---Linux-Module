# 🔐 **Bandit Level 8 → 9 Walkthrough**  
**OverTheWire: Linux Wargame**

---

## 🎯 **Goal**  
Find the password for **bandit9** by reading the contents of a file named `data.txt` in the current directory.

---

## 🧪 **What Happened**

Listing files showed this:


-rw-r----- 1 bandit9 bandit8 33033 Apr 10 14:23 data.txt
Using:
cat data.txt
I saw many lines of strings, with some repeating multiple times and some unique, but the password was not obvious by just looking.

🤔 My Thought Process
The instructions said the password is the string that only appears once in the file. Since the file was large and full of duplicates, I realized I needed a way to automatically find the unique string instead of scanning manually.

🔎 Research & Solution
After some quick research, I found the Linux command uniq which helps find unique lines when combined with sort.

I ran this:
sort data.txt | uniq -u
sort arranges all lines alphabetically, grouping duplicates together.

uniq -u filters and outputs only the lines that occur once.

This gave me the unique string that appeared only once in the file.

✅ Result
The output was:
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
This was the password for the bandit9 user.

🚀 Next Steps
I exited bandit8 and logged into bandit9 with:
ssh bandit9@bandit.labs.overthewire.org -p 2220
When prompted, I entered the password found above.

Summary
Use cat to view file contents.

When the file is large and repetitive, use sort and uniq -u to find unique lines.

Researching Linux commands online is a valuable skill—always explore your tools!

Precision and logic help solve problems faster than brute force.
