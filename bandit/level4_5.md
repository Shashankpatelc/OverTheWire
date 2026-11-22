# Bandit – Level 4 → Level 5

## Level Goal
> Log into the Bandit server as `bandit4` via SSH and retrieve the password for `bandit5` from the only human-readable file inside the `inhere` directory.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` / `cd` – Lists directory contents and navigates into `inhere/`
* `find . -type f ! -executable` – Searches the current directory for regular files that are not executable
* `-exec file {} +` – Runs the `file` utility on all matched files to determine their actual content type (ASCII text vs. binary data)
* `grep "text"` – Filters the `file` output to show only human-readable text files
* `cat ./-file07` – Reads the file starting with a dash (`-`) using its relative path (`./`)

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit4@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 3 → Level 4.

2. **Navigate into the `inhere` directory and list the files:**
   ```bash
   ls
   cd inhere/
   ls
   ```
   This shows several files named `-file00` through `-file09`.

3. **Identify the only human-readable text file:**
   ```bash
   find . -type f ! -executable -exec file {} + | grep "text"
   ```
   This reveals that `./-file07` is ASCII text, while the others are binary data.

4. **Read `./-file07`:**
   ```bash
   cat ./-file07
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* Don't rely on filenames or extensions to guess file types in Linux—the `file` command inspects the file's actual contents/headers.
* Piping `find ... -exec file {} +` into `grep "text"` is a fast, scalable way to locate readable files in a directory full of binary data.