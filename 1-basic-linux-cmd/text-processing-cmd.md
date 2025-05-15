# Linux Command Cheat Sheet

## Process Management

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `at` | Schedule one-time tasks | `echo "touch /tmp/file" \| at 15:00` | `job 5 at Wed May 15 15:00:00 2024` |
| `chroot` | Run command with different root | `sudo chroot /mnt/newroot /bin/bash` | *(No output, enters new environment)* |
| `crontab` | Schedule recurring jobs | `crontab -e` then `0 3 * * * /backup.sh` | *(Edits cron table)* |
| `kill` | Terminate process by PID | `kill -9 1234` | *(Silent if successful)* |
| `pgrep` | Find PIDs by name | `pgrep -u root nginx` | `1234\n5678` |
| `top` | Interactive process viewer | `top -o %MEM` | *(Dynamic process list)* |

## User Management

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `passwd` | Change password | `passwd` | `New password: \nRetype new password:` |
| `sudo` | Execute as superuser | `sudo apt update` | `[sudo] password for user:` |
| `whoami` | Show current user | `whoami` | `ubuntu` |
| `id` | Show user/group info | `id` | `uid=1000(user) gid=1000(user)` |

## Text Processing

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `awk` | Pattern scanning | `awk '{print $1}' file.txt` | `John\nAlice` |
| `sed` | Stream editor | `sed 's/foo/bar/g' file.txt` | *(Replaces all 'foo' with 'bar')* |
| `grep` | Pattern matching | `grep -i "error" log.txt` | `ERROR: File not found` |
| `sort` | Sort lines | `sort names.txt` | `Alice\nBob\nJohn` |
| `uniq` | Filter duplicates | `sort file.txt \| uniq` | *(Unique lines only)* |

## Printing

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `lp` | Print files | `lp -d Brother document.pdf` | `request id is Brother-42` |

## Network Commands

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `ping` | Test connectivity | `ping -c 4 google.com` | `64 bytes from 142.250.190.46` |
| `traceroute` | Trace network path | `traceroute example.com` | `1 router.local (192.168.1.1)` |
| `netstat` | Network stats | `netstat -tuln` | `tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN` |

## File Operations

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `find` | Search files | `find / -name "*.conf"` | `/etc/app.conf\n/home/user/config.conf` |
| `chmod` | Change permissions | `chmod 755 script.sh` | *(Silent if successful)* |
| `tar` | Archive files | `tar -czvf backup.tar.gz /data` | `data/file1\ndata/file2` |

## System Info

| Command | Description | Example | Output |
|---------|-------------|---------|--------|
| `uname` | System info | `uname -a` | `Linux server 5.4.0-135-generic` |
| `df` | Disk space | `df -h` | `/dev/sda1 50G 35G 15G 70% /` |
| `free` | Memory usage | `free -m` | `Mem: 7902 4523 3379` |

# Usage Notes

1. **Prerequisites**:
   ```bash
   sudo apt install net-tools traceroute # For network tools
   sudo systemctl start cups            # For printing services