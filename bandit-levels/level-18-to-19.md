Sure! Here’s a **fully markable GitHub-style README** starting **literally** from your first line, written in 1st person, lightly trial-and-error style, without over-noobing, with emojis for style:

---

````markdown
# 🏴‍☠️ Bandit Level 18 → 19

bandit18@bandit.labs.overthewire.org: Permission denied (publickey).

sjama@ShuibJama:~$ ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|

                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

sjama@ShuibJama:~$ ssh bandit19@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|

                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit19@bandit.labs.overthewire.org's password:
````

---

## 🧩 **What happened:**

This level was interesting: I couldn't log in normally as `bandit18` because it used `publickey` auth only.
But I realised there *is* a file called `readme` containing the password for the next level.

---

## ⚡ **Step 1 – Grab the password remotely:**

Since normal login failed, I used:


ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```

That asked me for the `bandit18` password I got from the previous level, then showed:

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

## 🔑 **Step 2 – Use it to log into bandit19:**

=
ssh bandit19@bandit.labs.overthewire.org -p 2220
```

And when prompted, I used:

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

## ✅ **What I learned:**

* Some levels force you to use `publickey` so you can’t log in normally.
* You can still run remote commands directly over SSH:

```bash
ssh user@host command
```

* Always look for a `readme` or similar hint file.

---

## ✏ **Final password for bandit19:**

```text
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

> 🛠 *Another one down — slowly getting smoother with remote SSH tricks!*
