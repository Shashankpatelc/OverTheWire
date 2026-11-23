# Bandit – Level 10 → Level 11

## Level Goal
> Log into the Bandit server as `bandit10` via SSH and retrieve the password for `bandit11` from `data.txt`, which contains base64-encoded data.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory
* `base64 -d data.txt` – Decodes (`-d`) base64-encoded text from `data.txt` back into readable plain text

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit10@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 9 → Level 10.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals `data.txt`.

3. **Decode the base64-encoded file:**
   ```bash
   base64 -d data.txt
   ```
   This decodes the file contents and prints the password for `bandit11`.

## Flag / Password
`[REDACTED]`

## Key Takeaways
* Base64 is an **encoding** scheme, not encryption—anyone can reverse it immediately without a key using `base64 -d` (or `base64 --decode`).
* Trailing `=` or `==` padding characters at the end of an alphanumeric string are a common visual clue that data is base64-encoded.
