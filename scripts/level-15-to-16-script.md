bandit15@bandit:~$ openssl s_client -connect localhost:30001
...
(connected, got DONE/RENEGOTIATING etc.)

bandit15@bandit:~$ echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -connect localhost:30001
...
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
