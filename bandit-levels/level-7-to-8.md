# 🔐 Bandit Level 7 → Level 8  
**Challenge:** Find the password for the next level, hidden in a massive file.  
**Clue:** The password is next to the word `millionth`.

---

## 🧪 What Happened

This level looked simple at first: just one file called `data.txt`.  
So I did:

find -name data.txt
It returned:
./data.txt
Naturally, I opened it:

cat data.txt
Big mistake.
My terminal exploded with lines and lines of random words and passwords — no way I could scroll through it all manually.

I thought, “there’s no way I’m going through all that.”
Then I remembered something I learned in a previous level: grep is your friend.

So I searched for the keyword they gave:

grep millionth data.txt
Boom — it gave me just one clean match.
The password was sitting right next to the word millionth, exactly as the level hinted. 🎯

😅 Mistakes I Made
❌ I ran cat data.txt without thinking — flooded my terminal with useless noise
❌ I forgot how to search inside a file the smart way at first
❌ I wasted time before remembering to try grep

✅ What Worked
bash
Copy
Edit
grep millionth data.txt
This worked because:

grep scans the file line-by-line for the keyword

It shows just the matching line (no clutter)

The challenge told us the password is next to the word — and it was!

💡 What I Learned
🔍 Even when a problem looks overwhelming, think filters, not force
🧠 Use the right tool — grep saved me from hours of manual searching
📚 Don’t ignore the clues in the level — they often tell you exactly what to look for
