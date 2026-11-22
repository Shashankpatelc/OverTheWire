# Bandit – Level 8 → Level 9

## Level Goal
> Log into the Bandit server as `bandit8` via SSH and retrieve the password for `bandit9` from `data.txt`, which is the only line of text that occurs only once.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory
* `sort data.txt` – Sorts all lines in `data.txt` alphabetically so identical lines are grouped adjacent to each other
* `uniq -u` – Filters sorted input to display only lines that are completely unique (occurring exactly once)

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit8@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 7 → Level 8.

2. **List the files in the home directory:**
   ```bash
   ls
   ```
   This reveals `data.txt`.

3. **Sort the file and filter for the single unique line:**
   ```bash
   sort data.txt | uniq -u
   ```
   This outputs the one line in `data.txt` that does not repeat—the password for `bandit9`.

## Flag / Password
`[REDACTED]`

## Key Takeaways
* `uniq` only compares **adjacent** lines, so it will miss duplicates scattered throughout a file unless the input is sorted first (`sort file | uniq`).
* The `-u` flag tells `uniq` to print only lines that appear once, ignoring all duplicated lines entirely.
