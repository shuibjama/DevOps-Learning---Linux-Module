# 🏴‍☠️ Bandit Level 17 → 18

**What happened:**

When I first logged in as `bandit17`, I saw two files:

* `passwords.new`
* `passwords.old`

It was obvious the password was hidden in whatever changed.

---

## 🔍 **Step 1 – Find the difference:**

I used:

```bash
diff passwords.new passwords.old
```

It showed me exactly what line had changed — revealing:

```
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y
```

The line starting with `<` is the **new** one, so:

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

---

## 🔑 **Step 2 – Got the password:**

I took that string as the password for `bandit18`.

---

## ⚡ **Step 3 – SSH into the next level:**

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

---

## ✅ **What I learned:**

* `diff` is super useful to spot changes.
* Usually the password is hidden in what’s new, not what’s old.
* Sometimes the simplest tools are enough.
  
---

### 🧰 **Tools used:**

* `ls`
* `id`
* `diff`
* `ssh`

---

> 📦 *Another level done, repo getting bigger, and each level feels more intuitive!*
