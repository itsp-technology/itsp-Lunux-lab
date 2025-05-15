# Linux Command Reference (Part 2)

## Text Processing Commands

### `awk`  
- **Description**: Pattern scanning and text processing language.  
- **Prerequisites**: Usually pre-installed (`gawk` package).  
- **Example** (Print 1st column of a file):  
  ```bash
  awk '{print $1}' sample.txt
  ```
- **Output**:  
  ```
  John
  Alice
  Bob
  ```

### `cut`  
- **Description**: Extract sections from files/input.  
- **Example** (Extract 1st field from CSV):  
  ```bash
  cut -d',' -f1 data.csv
  ```
- **Output**:  
  ```
  Name
  John
  Alice
  ```

### `diff`  
- **Description**: Compare files line by line.  
- **Example**:  
  ```bash
  diff file1.txt file2.txt
  ```
- **Output**:  
  ```
  3c3
  < Line3 in file1
  ---
  > Line3 in file2
  ```

### `ex`  
- **Description**: Line-editor mode of `vim`.  
- **Prerequisites**: Install `vim` (`sudo apt install vim`).  
- **Example** (Replace text in file):  
  ```bash
  ex -sc '%s/old/new/g|x' file.txt
  ```
- **Output**: *(Silent; modifies file in-place)*

### `head`  
- **Description**: Output first part of files.  
- **Example** (Show first 3 lines):  
  ```bash
  head -n 3 logfile.log
  ```
- **Output**:  
  ```
  [2023-01-01] System start
  [2023-01-01] Service loaded
  [2023-01-01] User login
  ```

### `iconv`  
- **Description**: Convert text encoding.  
- **Example** (Convert UTF-8 to ASCII):  
  ```bash
  iconv -f UTF-8 -t ASCII//TRANSLIT input.txt
  ```
- **Output**:  
  ```
  Special chars become '?'
  ```

### `join`  
- **Description**: Join lines from two files.  
- **Prerequisites**: Files must be sorted.  
- **Example**:  
  ```bash
  join <(sort file1) <(sort file2)
  ```
- **Output**:  
  ```
  common_field value1 value2
  ```

### `less`/`more`  
- **Description**: View file content page-by-page.  
- **Example**:  
  ```bash
  less large_file.log
  ```
- **Navigation**:  
  `Space`=next page, `q`=quit, `/`=search.

### `paste`  
- **Description**: Merge lines from files.  
- **Example**:  
  ```bash
  paste file1.txt file2.txt
  ```
- **Output**:  
  ```
  Line1_from_file1   Line1_from_file2
  Line2_from_file1   Line2_from_file2
  ```

### `sed`  
- **Description**: Stream editor for text substitution.  
- **Example** (Replace text):  
  ```bash
  sed 's/foo/bar/g' input.txt
  ```
- **Output**:  
  ```
  All 'foo' become 'bar'
  ```

### `sort`  
- **Description**: Sort lines in a file.  
- **Example**:  
  ```bash
  sort unsorted.txt
  ```
- **Output**:  
  ```
  Alice
  Bob
  John
  ```

### `tail`  
- **Description**: Output last part of files.  
- **Example** (Monitor logs in real-time):  
  ```bash
  tail -f /var/log/syslog
  ```
- **Output**: *(Continuously updates)*  
  ```
  May 15 11:00:01 host systemd: Started service
  ```

### `tr`  
- **Description**: Translate/delete characters.  
- **Example** (Convert lowercase to uppercase):  
  ```bash
  echo "hello" | tr 'a-z' 'A-Z'
  ```
- **Output**:  
  ```
  HELLO
  ```

### `uniq`  
- **Description**: Report/omit repeated lines.  
- **Prerequisites**: Input must be sorted first.  
- **Example**:  
  ```bash
  sort duplicates.txt | uniq
  ```
- **Output**:  
  ```
  Unique_line1
  Unique_line2
  ```

### `wc`  
- **Description**: Word/line/character count.  
- **Example**:  
  ```bash
  wc -l document.txt
  ```
- **Output**:  
  ```
  42 document.txt
  ```

### `xargs`  
- **Description**: Build commands from stdin.  
- **Example** (Delete all `.tmp` files):  
  ```bash
  find /tmp -name "*.tmp" | xargs rm
  ```
- **Output**: *(Silent if successful)*

---

## Printing Commands

### `lp`  
- **Description**: Print files.  
- **Prerequisites**: CUPS service running (`sudo systemctl start cups`).  
- **Example**:  
  ```bash
  lp -d HP_LaserJet document.pdf
  ```
- **Output**:  
  ```
  request id is HP_LaserJet-42 (1 file(s))
  ```

---

## Communication Commands

### `inetd`  
- **Description**: Internet super-server (deprecated).  
- **Modern Alternative**: Use `systemd` or `xinetd`.

### `netstat`  
- **Description**: Network statistics.  
- **Prerequisites**: Install `net-tools` (`sudo apt install net-tools`).  
- **Example** (Show listening ports):  
  ```bash
  netstat -tuln
  ```
- **Output**:  
  ```
  Proto Recv-Q Send-Q Local Address  Foreign Address  State
  tcp        0      0 0.0.0.0:22     0.0.0.0:*        LISTEN
  ```

### `ping`  
- **Description**: Test network connectivity.  
- **Example**:  
  ```bash
  ping -c 4 google.com
  ```
- **Output**:  
  ```
  PING google.com (142.250.190.46) 56(84) bytes of data.
  64 bytes from fra16s48-in-f14.1e100.net (142.250.190.46): icmp_seq=1 ttl=117 time=12.3 ms
  ```

### `rlogin`  
- **Description**: Remote login (insecure, use `ssh` instead).

### `traceroute`  
- **Description**: Trace network path.  
- **Prerequisites**: Install `traceroute` (`sudo apt install traceroute`).  
- **Example**:  
  ```bash
  traceroute example.com
  ```
- **Output**:  
  ```
  1  router.local (192.168.1.1)  1.234 ms
  2  isp-gateway (203.0.113.1)  5.678 ms
  ...
  ```

---

**Notes**:  
- For security-sensitive commands (`rlogin`), prefer modern alternatives (`ssh`).  
- Use `sudo` for system-wide operations (e.g., starting CUPS).  
- Install missing packages using your distro's package manager (`apt`, `yum`, etc.).  

### Verification Tips:  
1. For text processing commands, create test files:  
   ```bash
   echo -e "John,35\nAlice,28" > sample.csv
   ```  
2. For network commands, ensure internet access is available.  
3. For printing commands, verify your printer is configured in CUPS.  