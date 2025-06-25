# OverTheWire Bandit - Levels 0 to 1 🔐

## 🎉 Level 0: Getting Started

At Level 0, the goal was simple: log in to the Bandit server using SSH and find the password for the next level.

### What I Did:

- Connected to the Bandit server using SSH on a custom port:
   ssh bandit0@bandit.labs.overthewire.org -p 2220
Listed files in the home directory using:
ls
Read the readme file to find instructions and the password:
cat readme
Found the password for Level 1:
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
💡 What I Learned:
How to connect to a remote Linux server via SSH

Using a custom port with SSH

Basic Linux commands: ls (list files), cat (display file contents)

Navigating and interacting with a remote Linux environment

🎉 Level 1: Next Level Access
Using the password from Level 0, I connected to Level 1 with:
ssh bandit1@bandit.labs.overthewire.org -p 2220
The server confirmed successful login, marking the start of the next challenge.

📝 Summary
These first steps in the Bandit game introduced me to:

Secure Shell (SSH) connections and authentication

Navigating a Linux terminal remotely

Reading files and understanding simple command-line output

Mastering these basics builds a foundation for more advanced Linux and DevOps skills. Excited to continue the journey!

📫 Connect with Me!
Feel free to reach out or follow my progress:

LinkedIn: linkedin.com/in/shuibjama

GitHub: github.com/shuibjama

