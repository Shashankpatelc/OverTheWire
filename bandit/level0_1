# Bandit – Level 0 → Level 1

## Level Goal
> Log into the Bandit server as `bandit0` via SSH and retrieve the password for `bandit1` from a file named `readme` in the home directory.

## Commands / Concepts Used
* `ssh` – Connects securely to a remote server (`-p 2220` specifies the non-default port)
* `ls` – Lists files and directories in the current working directory
* `cat` – Displays the contents of a file in the terminal

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit0@bandit.labs.overthewire.org
   ```
   Enter the starting password: `bandit0`

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals a file named `readme`.

3. **Read the `readme` file:**
   ```bash
   cat readme
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* OverTheWire Bandit uses port `2220` instead of the default SSH port `22`.
* Always start a level by listing the directory contents (`ls` or `ls -la`) to see what files are available.