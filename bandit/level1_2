# Bandit – Level 1 → Level 2

## Level Goal
> Log into the Bandit server as `bandit1` via SSH and retrieve the password for `bandit2` from a file named `-` located in the home directory.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the current working directory
* `cat ./-` – Reads a file named `-` by specifying its relative path (`./`) so the command treats it as a file instead of standard input

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit1@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 0 → Level 1.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals a single file named `-`.

3. **Read the dashed filename:**
   ```bash
   cat ./-
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* Many Linux utilities (including `cat`) interpret a standalone `-` as standard input (`stdin`) or the start of an option flag.
* Prefixing a tricky filename with `./` forces the command to treat it as a literal file in the current directory.