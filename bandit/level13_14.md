# Bandit – Level 13 → Level 14

## Level Goal
> Use the private SSH key (`sshkey.private`) located in `bandit13`'s home directory to log directly into `bandit14`, then retrieve the password for `bandit14` from `/etc/bandit_pass/bandit14`.

## Commands / Concepts Used
* `scp -P 2220` – Securely copies files over SSH from the remote server to the local machine (note the uppercase `-P` for port in `scp`)
* `chmod 600` – Sets file permissions to read/write for the owner only, which SSH requires for private key files
* `ssh -i sshkey.private` – Authenticates to a remote server using a specified private key (`-i` for identity file) instead of a password
* `cat /etc/bandit_pass/bandit14` – Reads the password file that is only accessible to the `bandit14` user

## Walkthrough

1. **Copy the private SSH key from `bandit13` to your local machine:**
   ```bash
   scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
   ```
   Enter the password obtained from Level 12 → Level 13 when prompted.

2. **Restrict permissions on the private key:**
   ```bash
   chmod 600 sshkey.private
   ```

3. **Connect to `bandit14` using the private key:**
   ```bash
   ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
   ```

4. **Read the password for `bandit14`:**
   ```bash
   cat /etc/bandit_pass/bandit14
   ```

## Flag / Password
`[REDACTED]`

## Key Takeaways
* `ssh` uses lowercase `-p` to specify a port, while `scp` uses uppercase `-P`.
* SSH will reject a private key with overly permissive access (`UNPROTECTED PRIVATE KEY FILE`); running `chmod 600` locks it down to the owner so SSH accepts it.
* Key-based authentication (`-i`) lets you log in without a password, and `/etc/bandit_pass/<user>` stores each level's password readable only by that user.
