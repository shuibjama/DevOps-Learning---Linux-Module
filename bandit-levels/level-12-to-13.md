# 🔐 OverTheWire Bandit Level 12 → 13 Walkthrough

---

## What a tough challenge! 😅

This level took me quite some time and I needed some help along the way to fully understand what was going on. The file was a hexdump of a repeatedly compressed archive, which meant I had to carefully **reverse the hex dump** and then **unpack layers of compression** including **gzip**, **bzip2**, and **tar archives**.

At first, all these file types and compression formats felt confusing, but now I feel much more confident handling these commands and recognizing file types. Here’s exactly what I did, step by step.

---

## Step-by-step process 🔎

### Step 1: Reverse the hex dump

xxd -r stage1 stage2
xxd -r converts the hex dump (stage1) back into binary data (stage2).

Step 2: Identify file type
file stage2
Output: gzip compressed data

Step 3: Decompress gzip file
mv stage2 stage2.gz
gunzip stage2.gz
Step 4: Check file type again

file stage2
Output: bzip2 compressed data

Step 5: Decompress bzip2 file

mv stage2 stage3.bz2
bunzip2 stage3.bz2
Step 6: Identify next file type

file stage3
Output: gzip compressed data

Step 7: Decompress gzip file again
mv stage3 stage4.gz
gunzip stage4.gz
Step 8: Identify file type
file stage4
Output: POSIX tar archive

Step 9: Extract tar archive
tar -xf stage4
ls -l
New file found: data5.bin

Step 10: Rename and identify data5.bin
mv data5.bin stage5
file stage5
Output: POSIX tar archive

Step 11: Extract second tar archive
tar -xf stage5
ls -l
New file found: data6.bin

Step 12: Rename and identify data6.bin
mv data6.bin stage5
file stage5
Output: bzip2 compressed data

Step 13: Decompress bzip2 file again

mv stage5 stage6.bz2
bunzip2 stage6.bz2
Step 14: Identify file type

file stage6
Output: POSIX tar archive

Step 15: Extract tar archive again

tar -xf stage6
ls -l
New file found: data8.bin

Step 16: Rename and identify data8.bin

mv data8.bin stage7
file stage7
Output: gzip compressed data

Step 17: Decompress gzip file

mv stage7 stage8.gz
gunzip stage8.gz
Step 18: Check final file type

file stage8
Output: ASCII text

Step 19: Read the password!

cat stage8
The password is: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

Final thoughts 💡
This level was a real test of patience and understanding compression tools. It showed me the power of:

xxd to reverse hex dumps

gzip and gunzip for gzip files

bzip2 and bunzip2 for bzip2 files

tar for archives

file to check file types at every step

By breaking the problem into small steps and tackling one compression at a time, I learned to keep calm and keep pushing forward.

