# 🔐 **Bandit Level 11 → 12 Walkthrough**  
**OverTheWire: Linux Wargame**

---

## 🎯 **Goal**  
The password for the next level is stored in the file `data.txt`, but every letter has been rotated by 13 positions (a ROT13 cipher).  
We need to decode it.

---

## 🧪 **What Happened**

---

### 📁 1. Checked what was in the directory

bandit11@bandit:~$ ls
data.txt
📄 2. Read the contents of the file

bandit11@bandit:~$ cat data.txt
Guvf vf gur cnffjbeq: 5Gr8L4qeTPesPk8hqtjhRK8XSP6x2RHi
At first, this looked like total gibberish. But I noticed the structure kind of resembled real words — like maybe it was encoded English.

🤔 3. Thought about the level description
The challenge said:

"all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions."

That rang a bell — this sounded like a ROT13 cipher (a simple Caesar cipher with 13-letter rotation). I didn’t know the command off the top of my head, so I paused and did a quick Google search.

🔎 Research Break
I searched:

linux decode rot13 in terminal
and came across a few Linux posts that mentioned using the tr command like this:

tr 'A-Za-z' 'N-ZA-Mn-za-m'
That translates A→N, B→O, ... N→A, O→B, etc., both for lowercase and uppercase.

Then I realized I could pipe the contents of data.txt into this command.

🧪 4. Ran the correct decode command

bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
This is the password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
💥 And just like that — the gibberish became English, and the password was there.

✅ Password Found

5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
🚀 5. Logged into Bandit12
Exited the session:

bandit11@bandit:~$ exit
Then:

ssh bandit12@bandit.labs.overthewire.org -p 2220
Pasted the decoded password when prompted.

💡 What I Learned
🔁 ROT13 is a simple cipher, but still useful to know.

🧠 The tr command is great for character transformations.

💡 A single Google search can save time and help you learn faster.

🧵 Using pipes (|) lets you combine small Linux tools into powerful workflows.

🧰 Always read the challenge carefully — most hints are hidden in plain sight.


