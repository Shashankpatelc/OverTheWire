# Bandit – Level 11 → Level 12

## Level Goal
> Log into the Bandit server as `bandit11` via SSH and retrieve the password for `bandit12` from `data.txt`, where all uppercase (`A-Z`) and lowercase (`a-z`) letters have been rotated by 13 positions (ROT13).

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory
* `cat data.txt` – Outputs the contents of `data.txt` to standard output
* `tr 'A-Za-z' 'N-ZA-Mn-za-m'` – Translates (substitutes) each letter by shifting it 13 places in the alphabet, decoding the ROT13 cipher

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit11@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 10 → Level 11.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals `data.txt`.

3. **Decode the ROT13-encrypted text using `tr`:**
   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```
   This shifts every letter by 13 positions and prints the readable password for `bandit12`.

## Flag / Password
`[REDACTED]`

## Key Takeaways
* ROT13 is a simple Caesar cipher that shifts letters halfway through the 26-letter alphabet, making it self-inverse (running the exact same `tr` command encodes or decodes it).
* The `tr` (translate) utility is a fast, built-in Linux tool for character-by-character substitution directly inside a command pipeline.
