````markdown
# 🏴‍☠️ Bandit Level 18 → 19

## 🧩 **The Challenge:**
> *The password for the next level is stored in a file called `readme` in the home directory. Unfortunately, someone has modified `.bashrc` to log you out when you log in with SSH.*

**Commands that might help:** `ssh`, `ls`, `cat`

---

## ✏ **My approach:**
I realised logging in directly to `bandit18` wasn’t going to work because `.bashrc` logs me out instantly.  
So I had to think: *Is there a way to get the contents of the `readme` file without actually opening an interactive shell?*

Did some quick reading and found out you can run single remote commands via SSH like:
```bash
ssh user@host command
````

That way, you never get into the shell at all — so `.bashrc` can’t kick you out. Neat trick.

---

## ⚡ **What I tried & what worked:**

At first I tried logging in normally:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

But that logged me out immediately.

Then, instead, I ran:

```bash
ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```

It prompted me for the `bandit18` password (from the previous level), and then printed:

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

## 🔑 **Step 2 – Use it to log into bandit19:**

```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220
```

and when it asked for the password, I used:

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

## ✅ **What I learned:**

* Even if you can’t log in normally, SSH lets you execute a remote command directly.
* Files like `.bashrc` only run when you start an interactive shell, not when you run single commands.
* Always check for `readme` or password files first.
