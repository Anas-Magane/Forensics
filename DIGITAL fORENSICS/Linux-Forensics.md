# Linux Forensics: Top 20 Locations to Find the Flag

**By Anas Education**

---

## 📌 Introduction

In Linux CTFs, flags are often hiding in plain sight, tucked into configuration files, or buried in the history of what users typed. This guide will walk you through the top 20 locations where flags are commonly hidden in Linux systems.

**Pro Tip:** Always start with shell history and logs!

---

## 🔍 Section 1: Essential Locations (1-10)

### 1. Shell History (Bash/Zsh)

This is the **absolute first place to look**. It records every command the user typed. You might find them downloading the flag, cat-ing the flag, or connecting to a remote server.

**📂 Locations:**
```
~/.bash_history
~/.zsh_history
~/.sh_history
```

**🔎 What to look for:**
- `wget` or `curl` commands (downloading malware/tools)
- `ssh user@IP` (connecting to other machines)
- `echo "flag{...}"` (sometimes users accidentally echo the flag)

**💡 Tip:** If the file is empty, check `.bash_logout` to see if they cleared it!

---

### 2. The User's Home Directory (Hidden Files)

In Linux, files starting with a dot (`.`) are hidden. Users often hide flags here thinking `ls` won't show them.

**📂 Location:**
```
~/ (The user's home folder, e.g., /home/ubuntu/)
```

**🔍 How to check:**

Run `ls -la` (List All)

Look for directories like `.ssh`, `.gnupg`, or suspicious ones like `...` (three dots)

---

### 3. Temporary Directories (/tmp & /var/tmp)

These folders are world-writable. Attackers and scripts use them to store payloads, exploits, or temporary flag files because they don't need root privileges to write here.

**📂 Locations:**
```
/tmp/
/var/tmp/
/dev/shm/ (Shared memory – acts like a ramdisk)
```

**🔎 What to look for:**
- Script files (`.sh`, `.py`)
- Binary files (ELF executables)
- Folders with random names

---

### 4. SSH Keys & Known Hosts

If you find a private key (`id_rsa`), you basically own the user's access. The flag might be on another server you can SSH into.

**📂 Location:**
```
~/.ssh/
```

**📄 Key Files:**
- **id_rsa** - Private Key (Jackpot!)
- **authorized_keys** - Who can login to this machine
- **known_hosts** - List of servers this machine has connected to

---

### 5. System Logs (Auth & Syslog)

Logs tell you who logged in, who used sudo, and what services are running.

**📂 Locations:**
```
/var/log/auth.log (Debian/Ubuntu)
/var/log/secure (RHEL/CentOS)
/var/log/syslog
```

**🔎 What to look for:**
- Successful logins (`Accepted password`)
- Sudo commands (`COMMAND=/bin/cat /etc/shadow`)
- Cron job executions

---

### 6. Web Server Directory

If the CTF involves a website, the flag is often hidden in the web root.

**📂 Locations:**
```
/var/www/html/
/srv/www/
```

**🔎 What to look for:**
- `robots.txt` (Often contains hints)
- Hidden `.htaccess` files
- Source code with comments containing the flag
- `config.php` (Database credentials)

---

### 7. Cron Jobs (Scheduled Tasks)

Malware often uses Cron to establish persistence (restart itself every minute). The flag might be inside the script that Cron runs.

**📂 Locations:**
```
/var/spool/cron/crontabs/
/etc/crontab
/etc/cron.d/
/etc/cron.daily/, /etc/cron.hourly/
```

**🔎 What to look for:**
- Scripts running strange commands
- Scripts connecting to external IPs

---

### 8. The /proc Filesystem (Memory & Processes)

This is a virtual filesystem that lets you see into the kernel and running processes. You can recover environment variables or deleted binaries here.

**📂 Location:**
```
/proc/
```

**📄 Key Files:**
- `/proc/self/environ` - Environment variables of the current process (often holds hidden keys)
- `/proc/[PID]/cmdline` - The command used to start a running process
- `/proc/[PID]/fd/` - File descriptors (can point to deleted files)

---

### 9. Vim History (.viminfo)

If the user edited a file using vim, the `.viminfo` file records their search history, command history, and file positions. This is a huge artifact!

**📂 Location:**
```
~/.viminfo
```

**🔎 What to look for:**
- Strings they searched for (did they search for "password" or "flag"?)
- Files they opened (maybe they opened `/opt/flag.txt`)

---

### 10. Sudoers File (Privilege Escalation)

This file controls who can run commands as root. In CTFs, misconfigurations here are the key to getting the root flag.

**📂 Location:**
```
/etc/sudoers
```

**🔍 How to check:**
```
sudo -l (Lists what you can run as root)
```

**🔎 What to look for:**
- `(ALL) NOPASSWD: /usr/bin/python` - Means you can run Python as root without a password → instant root shell!

---

## 🔐 Section 2: Advanced Locations (11-20)

### 11. /etc/passwd & /etc/shadow

The passwd file lists all users. The shadow file contains their password hashes.

**📂 Locations:**
```
/etc/passwd (Readable by everyone)
/etc/shadow (Readable only by root)
```

**🔎 What to look for:**
- **passwd**: Look for users with ID 0 (root privileges) other than root. Look for strange users added recently.
- **shadow**: If you have read access, crack the hashes!

---

### 12. Bash Configuration (.bashrc / .profile)

Users (or attackers) put aliases and environment variables here that run every time a shell opens.

**📂 Locations:**
```
~/.bashrc
~/.profile
```

**🔎 What to look for:**
- `alias ls='ls -la'` (Harmless)
- `export FLAG=...` (The flag might be an environment variable!)

---

### 13. Mail Spools (/var/mail)

In older Linux systems or CTFs, "email" is just a text file stored in the mail spool.

**📂 Locations:**
```
/var/mail/[username]
/var/spool/mail/[username]
```

**🔎 What to look for:**
- Messages from "Root" or "Admin" containing passwords or instructions

---

### 14. Network Configuration (/etc/hosts)

Attackers might modify the hosts file to redirect traffic, or developers might leave internal IP addresses here.

**📂 Location:**
```
/etc/hosts
```

**🔎 What to look for:**
- Custom domain names mapped to IP addresses (e.g., `10.10.10.5 dev.flag-server.local`)

---

### 15. Opt and Mnt Directories

`/opt` is for optional software, and `/mnt` is for mounted drives. These are non-standard places often used to hide things because people forget to look there.

**📂 Locations:**
```
/opt/
/mnt/
/media/
```

**🔎 What to look for:**
- Custom applications
- Backups or mounted USB drives

---

### 16. Deleted Files (Recovering with Grep)

If a flag file was deleted but the disk space hasn't been overwritten, you can sometimes "grep the disk".

**🛠️ Command:**
```
grep -a -r "flag{" /path/to/search
```

**📝 Note:** This searches binary files as text (`-a`) recursively (`-r`). It can find flags in raw disk data if you point it at a partition (requires root).

---

### 17. Systemd Services

Persistence is often achieved by creating a new service that starts on boot.

**📂 Locations:**
```
/etc/systemd/system/
/lib/systemd/system/
```

**🔎 What to look for:**
- `.service` files that look out of place
- Services that reference scripts in `/tmp`

---

### 18. /usr/bin and /bin (SUID Binaries)

SUID binaries execute with the permissions of the file owner (usually root), not the user running them.

**🔍 How to find them:**
```
find / -perm -4000 2>/dev/null
```

**🔎 What to look for:**
- Standard binaries (like `nmap`, `vim`, `find`) that have SUID set
- You can use these to read the root flag (check **GTFOBins**)

---

### 19. /var/backups

Linux systems often keep automatic backups of critical files.

**📂 Location:**
```
/var/backups/
```

**🔎 What to look for:**
- `shadow.bak` (Backup of password hashes)
- `apt.extended_states` (History of installed packages)

---

### 20. Python/Perl/Ruby History

Just like Bash history, interactive coding shells have their own history files.

**📂 Locations:**
```
~/.python_history
~/.mysql_history (Database queries - Critical!)
~/.rediscli_history
```

**🔎 What to look for:**
- Database passwords
- SQL queries
- Logic used to generate the flag

---

---

*Created by Anas Education*

*Last Updated: 2026*