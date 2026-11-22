# Bandit – Level 6 → Level 7

## Level Goal
> Log into the Bandit server as `bandit6` via SSH and locate the password for `bandit7` stored somewhere on the server in a file owned by user `bandit7`, owned by group `bandit6`, and exactly 33 bytes in size.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `ls` – Lists files in the home directory (empty in this level)
* `find / -type f` – Searches the entire root filesystem (`/`) for regular files
* `-size 33c` – Filters for files that are exactly 33 bytes in size
* `-group bandit6 -user bandit7` – Filters by file group ownership and user ownership
* `2>/dev/null` – Redirects standard error (`stderr`) to `/dev/null` to hide `Permission denied` messages
* `cat` – Displays the contents of the located password file

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit6@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 5 → Level 6.

2. **Check the home directory:**
   ```bash
   ls
   ```
   The home directory is empty, confirming the file is located elsewhere on the server.

3. **Search the entire filesystem for the matching file while suppressing permission errors:**
   ```bash
   find / -type f -size 33c -group bandit6 -user bandit7 2>/dev/null
   ```
   This returns `/var/lib/dpkg/info/bandit7.password`.

4. **Read the password file:**
   ```bash
   cat /var/lib/dpkg/info/bandit7.password
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* Searching from `/` as a non-root user generates heavy `Permission denied` noise; redirecting `stderr` with `2>/dev/null` keeps only the valid matches visible.
* Combining `-user`, `-group`, and `-size` in `find` lets you pinpoint a single file across an entire Linux filesystem.
