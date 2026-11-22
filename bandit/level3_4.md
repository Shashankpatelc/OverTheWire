# Bandit – Level 3 → Level 4

## Level Goal
> Log into the Bandit server as `bandit3` via SSH and retrieve the password for `bandit4` from a hidden file located inside the `inhere` directory.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists visible files and directories in the current working directory
* `cd` – Changes into a specified directory
* `ls -a` – Lists all files, including hidden files that start with a dot (`.`)
* `cat` – Displays the contents of a file in the terminal

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit3@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 2 → Level 3.

2. **Check the home directory and enter `inhere`:**
   ```bash
   ls
   cd inhere
   ```

3. **List all files, including hidden ones:**
   ```bash
   ls -a
   ```
   This reveals a hidden file named `...Hiding-From-You`.

4. **Read the hidden file:**
   ```bash
   cat ./...Hiding-From-You
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* In Linux, any file or directory whose name starts with a dot (`.`) is hidden from a standard `ls` output.
* Running `ls -a` (or `ls -la` for full details) is a standard first step when a directory appears empty.