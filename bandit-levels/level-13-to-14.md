# 🔐 Bandit Level 13 → 14

## 📚 Challenge Description

> The password for the next level is stored in `/etc/bandit_pass/bandit14`  
> and can **only be read** by user `bandit14`.  
>  
> Instead of a password, I was given a **private SSH key** to log in as the next user.  
>  
> This level was about learning how to **use SSH keys** to move between users — a real DevOps skill!

---

## 🧪 What Happened

When I logged into `bandit13`, I ran:

ls
And I saw a file named:

sshkey.private
I thought: “Wait, this looks like an actual SSH private key 🔐... Let’s try reading it.”

cat sshkey.private
Yup — it was a long RSA private key.

I mistakenly tried:

cd sshkey.private
That didn’t work because it’s not a directory 😅.
Classic typo. I reset, laughed it off, and moved forward.

🧠 Realization
Since I have a private key, I figured (after some research) I could SSH into the next user like this:

ssh -i sshkey.private bandit14@localhost -p 2220
Then it prompted me:

Are you sure you want to continue connecting (yes/no)?

I typed:

yes
I got a warning:

Could not create directory '/home/bandit13/.ssh' (Permission denied)

No problem though — the SSH still went through successfully! ✅

I was now inside the bandit14 shell!

🪄 Getting the Password
Once inside bandit14, I ran:

cat /etc/bandit_pass/bandit14
And got the password for the next level! 🎉

✅ What I Learned
How to use ssh -i with a private key

What happens when SSH can’t write to .ssh/known_hosts (it still works!)

You don’t always need a password — private keys are a big part of Linux auth

Even if you make a few command mistakes, it’s part of the learning

💬 Final Thoughts
I’m slowly becoming more confident with real-world Linux and DevOps-style tasks.

This level was especially satisfying because it mimicked a real use case: SSHing into a box with a private key.
