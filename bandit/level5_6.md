# Bandit – Level 5 → Level 6

## Level Goal
> Log into the Bandit server as `bandit5` via SSH and retrieve the password for `bandit6` from a file inside the `inhere` directory that is human-readable, exactly 1033 bytes in size, and not executable.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` / `cd` – Lists directory contents and navigates into `inhere/`
* `find . -type f` – Recursively searches for regular files starting from the current directory
* `-size 1033c` – Filters for files that are exactly 1033 bytes (`c` stands for bytes)
* `! -executable` – Excludes executable files from the results
* `-exec file {} +` – Checks the file type of matched results to verify human-readable text
* `cat` – Displays the contents of the located hidden file

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit5@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 4 → Level 5.

2. **Navigate into the `inhere` directory and inspect its contents:**
   ```bash
   ls
   cd inhere/
   ls
   ```
   This reveals multiple subdirectories (`maybehere00` through `maybehere19`).

3. **Search for the file matching all three criteria (1033 bytes, non-executable, human-readable):**
   ```bash
   find . -type f -size 1033c ! -executable -exec file {} +
   ```
   This pinpoints `./maybehere07/.file2` as ASCII text.

4. **Read the located file:**
   ```bash
   cat ./maybehere07/.file2
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* `find` allows chaining multiple filters (`-type`, `-size`, `! -executable`) to narrow down thousands of nested files in a single command.
* In `find`, the `c` suffix on `-size` specifies exact bytes (as opposed to `k` for kilobytes or `M` for megabytes).
