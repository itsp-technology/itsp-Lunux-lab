# Linux Command Reference

## Process Management Commands

### `at`
- **Description**: Schedule a one-time task to run at a specific time.
- **Syntax**: `at [time]`
- **Example**:
  ```bash
  echo "rm -rf /tmp/*" | at 11:00 PM
  ```

### `chroot`
- **Description**: Run a command with a different root directory (isolated environment).
- **Syntax**: `sudo chroot /new/root command`
- **Example**:
  ```bash
  sudo chroot /mnt/isolated_env /bin/bash
  ```

### `crontab`
- **Description**: Schedule recurring tasks using cron jobs.
- **Syntax**: `crontab -e` (edit jobs)
- **Example** (cron job for daily backups):
  ```bash
  0 3 * * * /usr/bin/backup_script.sh
  ```

### `kill`
- **Description**: Terminate a process by PID.
- **Syntax**: `kill [signal] PID`
- **Example** (force kill):
  ```bash
  kill -9 1234
  ```

### `killall`
- **Description**: Kill all processes by name.
- **Syntax**: `killall [signal] process_name`
- **Example**:
  ```bash
  killall -15 firefox
  ```

### `nice`
- **Description**: Run a process with adjusted priority (default lowers priority).
- **Syntax**: `nice -n [priority] command`
- **Example** (low priority):
  ```bash
  nice -n 19 ./long_running_script.sh
  ```

### `pgrep`
- **Description**: Find PIDs by process name or user.
- **Syntax**: `pgrep [options] pattern`
- **Example** (find `nginx` PIDs):
  ```bash
  pgrep -u root nginx
  ```

### `pidof`
- **Description**: Get the PID of a running process.
- **Syntax**: `pidof process_name`
- **Example**:
  ```bash
  pidof sshd
  ```

### `pkill`
- **Description**: Send signals to processes by name.
- **Syntax**: `pkill [options] pattern`
- **Example** (reload `nginx`):
  ```bash
  pkill -HUP nginx
  ```

### `ps`
- **Description**: List active processes.
- **Syntax**: `ps [options]`
- **Example** (show all processes):
  ```bash
  ps aux
  ```

### `sleep`
- **Description**: Pause execution for a specified time.
- **Syntax**: `sleep [seconds]`
- **Example**:
  ```bash
  sleep 5 && echo "Done!"
  ```

### `time`
- **Description**: Measure command execution time.
- **Syntax**: `time command`
- **Example**:
  ```bash
  time ls -l
  ```

### `top`
- **Description**: Real-time process monitoring.
- **Syntax**: `top`
- **Example**:
  ```bash
  top -u apache
  ```

### `wait`
- **Description**: Wait for background processes to finish.
- **Syntax**: `wait [PID]`
- **Example** (in a script):
  ```bash
  ./job1.sh &
  ./job2.sh &
  wait
  ```

### `watch`
- **Description**: Repeat a command periodically (default: 2s).
- **Syntax**: `watch [options] command`
- **Example** (monitor disk usage):
  ```bash
  watch -n 1 df -h
  ```

---

## User Management/Environment Commands

### `env`
- **Description**: Display or set environment variables.
- **Syntax**: `env` or `env VAR=value command`
- **Example** (run with custom env):
  ```bash
  env DISPLAY=:0 xcalc
  ```

### `finger`
- **Description**: Show user information (may need installation).
- **Syntax**: `finger [user]`
- **Example**:
  ```bash
  finger alice
  ```

### `id`
- **Description**: Display user and group IDs.
- **Syntax**: `id [user]`
- **Example**:
  ```bash
  id -u bob
  ```

### `mesg`
- **Description**: Allow/deny terminal messages.
- **Syntax**: `mesg [y/n]`
- **Example** (block messages):
  ```bash
  mesg n
  ```

### `passwd`
- **Description**: Change user password.
- **Syntax**: `passwd [user]`
- **Example**:
  ```bash
  sudo passwd alice
  ```

### `su`
- **Description**: Switch user (use `-` for login shell).
- **Syntax**: `su - [user]`
- **Example** (switch to root):
  ```bash
  su - root
  ```

### `sudo`
- **Description**: Execute commands as superuser.
- **Syntax**: `sudo command`
- **Example**:
  ```bash
  sudo systemctl restart nginx
  ```

### `uname`
- **Description**: Display system information.
- **Syntax**: `uname [options]`
- **Example** (show kernel version):
  ```bash
  uname -r
  ```

### `uptime`
- **Description**: Show system uptime and load average.
- **Syntax**: `uptime`
- **Example**:
  ```bash
  uptime
  ```

### `w`
- **Description**: List logged-in users and their processes.
- **Syntax**: `w`
- **Example**:
  ```bash
  w -h
  ```

### `wall`
- **Description**: Broadcast a message to all users.
- **Syntax**: `wall "message"`
- **Example**:
  ```bash
  wall "Server reboot in 10 minutes!"
  ```

### `who`
- **Description**: List logged-in users.
- **Syntax**: `who`
- **Example**:
  ```bash
  who -b
  ```

### `whoami`
- **Description**: Print current username.
- **Syntax**: `whoami`
- **Example**:
  ```bash
  whoami
  ```

### `write`
- **Description**: Send a message to a specific user.
- **Syntax**: `write user [tty]`
- **Example**:
  ```bash
  write bob pts/1
  ```

---

**Notes**:  
- Use `sudo` for commands requiring root privileges (e.g., `chroot`, `passwd`).  
- Replace placeholders (e.g., `user`, `PID`) with actual values.  
- Commands like `finger` or `write` may require installation (e.g., `sudo apt install finger`).  