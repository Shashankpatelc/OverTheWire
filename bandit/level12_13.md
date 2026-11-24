# Bandit – Level 12 → Level 13

## Level Goal
> Log into the Bandit server as `bandit12` via SSH and retrieve the password for `bandit13` from `data.txt`, which is a hexdump of a file that has been repeatedly compressed using `gzip`, `bzip2`, and `tar`.

## Commands / Concepts Used
* `ssh` – Connects securely to the remote server (`-p 2220` specifies the port)
* `mktemp -d` – Creates a unique temporary directory inside `/tmp` where you have write permissions
* `cp` / `cd` – Copies `data.txt` into the temporary workspace and navigates into it
* `xxd -r` – Reverses a hexdump back into its original binary form
* `file` – Inspects a file's magic bytes to identify its compression/archive format
* `mv` – Renames files with the appropriate extension (`.gz`, `.bz2`) required by decompression tools
* `gzip -d` – Decompresses `gzip` (`.gz`) files
* `bzip2 -d` – Decompresses `bzip2` (`.bz2`) files
* `tar -xvf` – Extracts files from a POSIX `tar` archive
* `cat` – Displays the final uncompressed ASCII text file

## Walkthrough

1. **Connect to the level:**
   ```bash
   ssh -p 2220 bandit12@bandit.labs.overthewire.org
   ```
   Enter the password obtained from Level 11 → Level 12.

2. **Set up a temporary workspace and copy `data.txt`:**
   ```bash
   mktemp -d
   cp data.txt /tmp/<temp_dir>/
   cd /tmp/<temp_dir>/
   ```

3. **Convert the hexdump back to binary:**
   ```bash
   xxd -r data.txt new
   ```

4. **Iteratively identify and decompress each layer:**
   ```bash
   # Layer 1: gzip
   file new
   mv new new.gz
   gzip -d new.gz

   # Layer 2: bzip2
   file new
   mv new new.bz2
   bzip2 -d new.bz2

   # Layer 3: gzip
   file new
   mv new new.gz
   gzip -d new.gz

   # Layer 4: POSIX tar archive (extracts data5.bin)
   file new
   tar -xvf new

   # Layer 5: POSIX tar archive (extracts data6.bin)
   file data5.bin
   tar -xvf data5.bin

   # Layer 6: bzip2
   file data6.bin
   mv data6.bin data6.bin.bz2
   bzip2 -d data6.bin.bz2

   # Layer 7: POSIX tar archive (extracts data8.bin)
   file data6.bin
   tar -xvf data6.bin

   # Layer 8: gzip
   file data8.bin
   mv data8.bin data8.bin.gz
   gzip -d data8.bin.gz
   ```

5. **Verify the final file is ASCII text and read the password:**
   ```bash
   file data8.bin
   cat data8.bin
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* Always work inside `/tmp` (using `mktemp -d`) when you need to create, rename, or extract files on a read-only home directory.
* Tools like `gzip` and `bzip2` expect specific file extensions (`.gz`, `.bz2`) before decompressing, whereas `file` inspects the actual file header regardless of the filename.
* `xxd -r` is the standard way to reverse a hex dump back into raw binary data.
