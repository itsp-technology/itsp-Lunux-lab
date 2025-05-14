# Linux Command Reference

## Process Management Commands

### `at`
- **Description**: Schedule a one-time task to run at a specific time.
- **Syntax**: `at [time]`
- **Example**:
  ```bash
  echo "touch /tmp/testfile" | at 15:30
  ```
- **Output**:
  ```
  warning: commands will be executed using /bin/sh
  job 5 at Wed May 15 15:30:00 2024
  ```

### `chroot`
- **Description**: Run a command with a different root directory.
- **Syntax**: `sudo chroot /new/root command`
- **Example**:
  ```bash
  sudo chroot /mnt/isolated /bin/bash
  ```
- **Output**: *(No output if successful; drops you into the new environment)*

### `crontab`
- **Description**: Schedule recurring tasks.
- **Syntax**: `crontab -e`
- **Example**:
  ```bash
  */5 * * * * /usr/bin/disk_check.sh
  ```
- **Output**: *(No output; edits your crontab file)*

### `kill`
- **Description**: Terminate a process by PID.
- **Syntax**: `kill [signal] PID`
- **Example**:
  ```bash
  kill -9 1234
  ```
- **Output**: *(No output if successful)*

### `killall`
- **Description**: Kill all processes by name.
- **Syntax**: `killall [signal] process_name`
- **Example**:
  ```bash
  killall -HUP nginx
  ```
- **Output**: *(No output if successful)*

### `nice`
- **Description**: Run a process with adjusted priority.
- **Syntax**: `nice -n [priority] command`
- **Example**:
  ```bash
  nice -n 19 ./script.sh
  ```
- **Output**: *(Runs silently; check priority with `top`)*

### `pgrep`
- **Description**: Find PIDs by process name.
- **Syntax**: `pgrep [options] pattern`
- **Example**:
  ```bash
  pgrep -u root sshd
  ```
- **Output**:
  ```
  123
  456
  ```

### `pidof`
- **Description**: Get PID of a running process.
- **Syntax**: `pidof process_name`
- **Example**:
  ```bash
  pidof bash
  ```
- **Output**:
  ```
  7890
  ```

### `pkill`
- **Description**: Send signals to processes by name.
- **Syntax**: `pkill [options] pattern`
- **Example**:
  ```bash
  pkill -f "python script.py"
  ```
- **Output**: *(No output if successful)*

### `ps`
- **Description**: List active processes.
- **Syntax**: `ps [options]`
- **Example**:
  ```bash
  ps aux | grep nginx
  ```
- **Output**:
  ```
  root      1234  0.0  0.5  12345  6789 ?        S    May14   0:10 nginx: master
  www-data  5678  0.0  0.3  12345  4321 ?        S    May14   0:05 nginx: worker
  ```

### `sleep`
- **Description**: Pause execution.
- **Syntax**: `sleep [seconds]`
- **Example**:
  ```bash
  sleep 3 && echo "Done"
  ```
- **Output**:
  ```
  Done  # (after 3 seconds)
  ```

### `time`
- **Description**: Measure command execution time.
- **Syntax**: `time command`
- **Example**:
  ```bash
  time ls -l
  ```
- **Output**:
  ```
  total 12
  -rw-r--r-- 1 user user  0 May 15 10:00 file1
  -rw-r--r-- 1 user user  0 May 15 10:00 file2

  real    0m0.003s
  user    0m0.001s
  sys     0m0.002s
  ```

### `top`
- **Description**: Real-time process monitor.
- **Syntax**: `top`
- **Output**:
  ```
  top - 10:30:45 up 2 days,  3:15,  2 users,  load average: 0.15, 0.10, 0.05
  Tasks: 120 total,   2 running, 118 sleeping,   0 stopped,   0 zombie
  %Cpu(s):  2.3 us,  0.5 sy,  0.0 ni, 97.0 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
  KiB Mem :  8000000 total,  2000000 free,  3000000 used,  3000000 buff/cache
  ```

### `wait`
- **Description**: Wait for background processes.
- **Syntax**: `wait [PID]`
- **Example**:
  ```bash
  sleep 10 &
  wait $!
  echo "Done"
  ```
- **Output**:
  ```
  Done  # (after 10 seconds)
  ```

### `watch`
- **Description**: Repeat command periodically.
- **Syntax**: `watch [options] command`
- **Example**:
  ```bash
  watch -n 1 free -h
  ```
- **Output** *(updates every second)*:
  ```
  Every 1.0s: free -h

                total   used    free
  Mem:           7.7G    3.2G    4.5G
  Swap:          2.0G    0.0G    2.0G
  ```

---

## User Management Commands

### `env`
- **Description**: Show/set environment variables.
- **Syntax**: `env`
- **Example**:
  ```bash
  env | grep PATH
  ```
- **Output**:
  ```
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
  ```

### `finger`
- **Description**: Show user info.
- **Syntax**: `finger [user]`
- **Example**:
  ```bash
  finger alice
  ```
- **Output**:
  ```
  Login: alice         Name: Alice Smith
  Directory: /home/alice      Shell: /bin/bash
  Last login Wed May 15 09:30 (EDT) on pts/0
  ```

### `id`
- **Description**: Show user/group IDs.
- **Syntax**: `id`
- **Example**:
  ```bash
  id
  ```
- **Output**:
  ```
  uid=1000(alice) gid=1000(alice) groups=1000(alice),27(sudo)
  ```

### `passwd`
- **Description**: Change password.
- **Syntax**: `passwd`
- **Example**:
  ```bash
  passwd
  ```
- **Output**:
  ```
  Changing password for alice.
  Current password: 
  New password: 
  Retype new password: 
  passwd: password updated successfully
  ```

### `sudo`
- **Description**: Run as superuser.
- **Syntax**: `sudo command`
- **Example**:
  ```bash
  sudo apt update
  ```
- **Output**:
  ```
  [sudo] password for alice: 
  Hit:1 http://archive.ubuntu.com focal InRelease
  Reading package lists... Done
  ```

### `uptime`
- **Description**: Show system uptime.
- **Syntax**: `uptime`
- **Output**:
  ```
  10:45:30 up 2 days,  3:30,  2 users,  load average: 0.10, 0.15, 0.20
  ```

### `whoami`
- **Description**: Show current user.
- **Syntax**: `whoami`
- **Output**:
  ```
  alice
  ```

---

**Notes**:
1. Outputs may vary slightly based on your system configuration.
2. Commands like `kill`/`killall` show no output when successful.
3. Time-based commands (`sleep`, `watch`) show dynamic outputs.
4. Some commands (`finger`) may require installation first (`sudo apt install finger`).