# Bandit Level 15 → Level 16: Using SSL/TLS to Send Password Over Network 🔐

---

## What I needed to do

The goal was to retrieve the password for the next level by submitting the **current password** to `localhost` on port **30001** — but the connection had to be secured with **SSL/TLS encryption**.

---

## Tools I considered 🛠️

- `nc` (netcat) and `telnet` — great for plain text TCP connections, but they don’t support SSL/TLS by default.
- `openssl s_client` — a powerful tool to open SSL/TLS connections from the command line.
- Others like `ncat`, `socat`, but I decided to start simple.

---

## My thought process & trial and error 🧠💡

1. **First attempt**: Tried the obvious plain-text way to send the password using `nc`:
   cat /etc/bandit_pass/bandit15 | nc localhost 30001
But this didn’t work because the server expects SSL-encrypted input, so it just hung or gave no useful response.

Next, I researched how to send SSL data from command line. I found that openssl s_client is designed exactly for this — it opens an SSL/TLS connection and can pipe data through it.

Experimenting with openssl s_client:

I tried to connect with:

openssl s_client -connect localhost:30001
This connected and showed a lot of SSL handshake info, but I needed a cleaner way to send just the password and get a response.

Adding quiet mode to suppress extra info:

cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -quiet
This worked! The server responded with "Correct!" and then printed the password for the next level.

What I learned ✅
nc and telnet are great for simple connections but don't handle SSL.

openssl s_client is a versatile tool to interact with SSL/TLS servers from the command line.

Trial and error combined with focused research helped me figure out the right tool and options.

Understanding these tools not only solved this level but also improved my command-line networking skills!

Final command that worked 🎉

cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -quiet
This challenge was a nice reminder that sometimes the simplest tools (nc, telnet) aren’t enough, and a bit of research can open doors to powerful utilities like openssl. It also showed me how important it is to understand protocols like SSL/TLS beyond just using them blindly.
