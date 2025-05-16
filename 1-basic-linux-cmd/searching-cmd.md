# Linux Command Reference (Searching & Miscellaneous)

---

## Searching Commands

### `find`
- **Description**: Search files/directories by name, type, size, etc.  
- **Syntax**:  
  ```bash
  find [path] [options] [expression]
  ```
- **Example** (Find `.txt` files in `/home`):  
  ```bash
  find /home -name "*.txt"
  find /root/vivek1/vivek2 -name "*.*"
  ```
- **Output**:  
  ```
  /home/user/file1.txt
  /home/user/docs/file2.txt
  ```

### `grep`
- **Description**: Search text patterns in files.  
- **Syntax**:  
  ```bash
  grep [options] "pattern" [file]
  ```
- **Example** (Search for "error" in a log file):  
  ```bash
  grep "error" /var/log/syslog
  ```
- **Output**:  
  ```
  May 15 10:30:01 host kernel: [ERROR] Disk full
  ```

### `strings`
- **Description**: Extract printable strings from binary files.  
- **Prerequisites**: Part of `binutils` (usually pre-installed).  
- **Example** (Extract strings from an executable):  
  ```bash
  strings /bin/ls
  ```
- **Output**:  
  ```
  /lib64/ld-linux-x86-64.so.2
  libselinux.so.1
  ...
  ```

---

## Miscellaneous Commands

### `banner`
- **Description**: Print text in large ASCII art letters.  
- **Prerequisites**: Install `sysvbanner` (Debian/Ubuntu: `sudo apt install sysvbanner`).  
- **Example**:  
  ```bash
  banner "HELLO"
  ```
- **Output**:  
  ```
   #    #  ######  #       #        ####  
  #    #  #       #       #       #    # 
  ######  #####   #       #       #    # 
  #    #  #       #       #       #    # 
  #    #  ######  ######  ######   ####  
  ```

### `bc`
- **Description**: Command-line calculator.  
- **Prerequisites**: Install `bc` if missing (`sudo apt install bc`).  
- **Example** (Calculate `5 * 3`):  
  ```bash
  echo "5 * 3" | bc
  ```
- **Output**:  
  ```
  15
  ```

### `cal`
- **Description**: Display a calendar.  
- **Syntax**:  
  ```bash
  cal [options]
  ```
- **Example** (Show 3-month calendar):  
  ```bash
  cal -3
  ```
- **Output**:  
  ```
      April 2023             May 2023              June 2023        
  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  
                    1      1  2  3  4  5  6               1  2  3  
   2  3  4  5  6  7  8   7  8  9 10 11 12 13   4  5  6  7  8  9 10  
  ...
  ```

### `man`
- **Description**: Display manual pages for commands.  
- **Example**:  
  ```bash
  man ls
  ```
- **Output**: *(Displays the manual for `ls`)*

### `size`
- **Description**: Show section sizes of a binary file.  
- **Prerequisites**: Part of `binutils` (usually pre-installed).  
- **Example**:  
  ```bash
  size /bin/ls
  ```
- **Output**:  
  ```
  text    data     bss     dec     hex filename  
  124042   4768    3360  130170   1fc7a /bin/ls
  ```

### `yes`
- **Description**: Repeatedly output a string (useful for automation).  
- **Example** (Repeat "confirm" indefinitely):  
  ```bash
  yes "confirm"
  ```
- **Output**:  
  ```
  confirm
  confirm
  confirm
  ... (press Ctrl+C to stop)
  ```

---

**Notes**:  
1. For `banner`, use `sysvbanner` on Debian/Ubuntu or `banner` on other distros.  
2. Use `Ctrl+C` to interrupt commands like `yes` or `tail -f`.  
3. Install missing packages using:  
   ```bash
   sudo apt install [package]   # Debian/Ubuntu
   sudo yum install [package]   # RHEL/CentOS
   ```

### Verification Tips:
1. Test `grep` with a sample log file:  
   ```bash
   echo "Test error message" > test.log
   grep "error" test.log
   ```
2. Test `bc` with arithmetic operations:  
   ```bash
   echo "scale=2; 10/3" | bc   # Output: 3.33
   ```
3. Test `cal` for specific years/months:  
   ```bash
   cal 2024          # Show entire 2024 calendar
   cal 12 2023       # Show December 2023
   ```