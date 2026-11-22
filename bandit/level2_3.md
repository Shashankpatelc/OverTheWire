# Bandit – Level 2 → Level 3

## Level Goal
> Log into the Bandit server as `bandit2` via SSH and retrieve the password for `bandit3` from a file named `--spaces in this filename--` located in the home directory.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the current working directory
* `cat ./'--spaces in this filename--'` – Reads a file with both leading dashes and spaces by combining a relative path (`./`) with quotes (`'...'`)

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit2@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 1 → Level 2.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals a file named `--spaces in this filename--`.

3. **Read the file:**
   ```bash
   cat ./'--spaces in this filename--'
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* The shell treats spaces as argument separators—wrapping a filename in quotes (`'...'` or `"..."`) or escaping spaces with backslashes (`\ `) ensures it is read as a single filename.
* Leading dashes (`--`) can be mistaken for command-line flags; prefixing the path with `./` forces `cat` to treat it strictly as a file in the current directory.