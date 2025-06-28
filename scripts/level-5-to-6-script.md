cd ~/inhere

# trial and error checking:
ls maybehere00
ls maybehere01
ls maybehere02
...
ls maybehere19

# finally:
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
