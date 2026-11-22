# Bandit – Level 7 → Level 8

## Level Goal
> Log into the Bandit server as `bandit7` via SSH and retrieve the password for `bandit8` stored in `data.txt` next to the word `millionth`.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory
* `grep "millionth" data.txt` – Searches `data.txt` for lines containing the exact string `millionth`

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit7@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 6 → Level 7.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals a large file named `data.txt`.

3. **Search `data.txt` for the word `millionth`:**
   ```bash
   grep "millionth" data.txt
   ```
   This prints the matching line containing `millionth` followed by the password for `bandit8`.

## Flag / Password
`[REDACTED]`

## Key Takeaways
* `grep` is the go-to utility for quickly filtering large text files for specific strings or patterns instead of reading the entire file manually.
