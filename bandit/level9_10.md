# Bandit – Level 9 → Level 10

## Level Goal
> Log into the Bandit server as `bandit9` via SSH and retrieve the password for `bandit10` from `data.txt`, stored in one of the few human-readable strings preceded by several `=` characters.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory
* `strings data.txt` – Extracts printable, human-readable text sequences from a binary or mixed-data file
* `grep "=="` – Filters the extracted strings to display only lines containing multiple `=` characters

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit9@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 8 → Level 9.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals `data.txt`.

3. **Extract human-readable strings and filter for `==`:**
   ```bash
   strings data.txt | grep "=="
   ```
   This strips out the binary noise and prints the few readable lines containing `==`, revealing the password for `bandit10`.

## Flag / Password
`[REDACTED]`

## Key Takeaways
* `cat` or `grep` alone can struggle with files containing binary data; `strings` cleanly extracts only sequences of printable characters.
* Piping `strings` into `grep` is a standard technique in CTF challenges and reverse engineering for pulling readable flags or clues out of binary files.
