# Linux Command Reference (Table Format)

---

## File and File System Management

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `cat`   | Display file content | `cat file.txt` | Contents of `file.txt` |
| `cd`    | Change directory | `cd /home/user` | (No output) |
| `chmod` | Change file permissions | `chmod 755 script.sh` | (No output) |
| `chown` | Change file owner | `chown user:group file.txt` | (No output) |
| `cp`    | Copy files | `cp file.txt backup/` | (No output) |
| `df`    | Show disk space usage | `df -h` | `Filesystem Size Used Avail Use% Mounted on` |
| `ls`    | List directory contents | `ls -l` | `-rw-r--r-- 1 user 4096 Jan 1 file.txt` |
| `mkdir` | Create directory | `mkdir new_folder` | (No output) |
| `mv`    | Move/rename files | `mv old.txt new.txt` | (No output) |
| `rm`    | Remove files | `rm file.txt` | (No output) |

---

## Process Management

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `ps`    | List processes | `ps aux` | `root 1 0.0 0.1 12345 6789 ? Ss ...` |
| `top`   | Interactive process viewer | `top` | Real-time process list |
| `kill`  | Terminate process | `kill -9 1234` | (No output if successful) |
| `crontab` | Schedule tasks | `crontab -e` | Opens cron job editor |
| `pgrep` | Find PID by name | `pgrep firefox` | `5678` |

---

## User Management/Environment

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `passwd` | Change password | `passwd` | `New password: [hidden]` |
| `sudo`   | Run as superuser | `sudo apt update` | `[sudo] password for user:` |
| `whoami` | Show current user | `whoami` | `user` |
| `id`     | User/group info | `id` | `uid=1000(user) gid=1000(user)` |

---

## Text Processing

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `grep`  | Search text patterns | `grep "error" log.txt` | `2023-01-01 ERROR: File not found` |
| `sed`   | Stream editor | `sed 's/foo/bar/g' file.txt` | Modified text with replacements |
| `awk`   | Text processing | `awk '{print $1}' data.csv` | First column of CSV |
| `sort`  | Sort lines | `sort names.txt` | Alphabetically sorted list |

---

## Printing

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `lp`    | Print file | `lp -d HP_Printer doc.pdf` | `request id is HP_Printer-123` |

---

## Communications

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `ping`  | Network connectivity test | `ping -c 4 google.com` | `64 bytes from 142.250.190.46: icmp_seq=1 ttl=117` |
| `netstat` | Network stats | `netstat -tuln` | `tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN` |

---

## Searching

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `find`  | Search files | `find /home -name "*.log"` | `/home/user/app.log` |
| `strings` | Extract text from binaries | `strings /bin/ls` | `libc.so.6` |

---

## Miscellaneous

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `cal`   | Display calendar | `cal 2024` | Calendar for 2024 |
| `bc`    | Calculator | `echo "5*3" | bc` | `15` |
| `banner` | ASCII art text | `banner "Hi"` | Large "Hi" in ASCII |
| `yes`   | Repeat string | `yes "y"` | Infinite `y` lines |

---

**Notes**:  
1. Replace placeholders (e.g., `user`, `1234`, `HP_Printer`) with actual values.  
2. Use `man [command]` for detailed documentation.  
3. For `banner`, install via `sudo apt install sysvbanner`.  