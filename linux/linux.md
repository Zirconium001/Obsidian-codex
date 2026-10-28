# Linux Fundamentals: Extended Guide

A detailed reference with syntax, useful flags, and examples for every command and operator, plus a few extra essentials.
---

## Table of Contents

1. [System Information](#1-system-information)
2. [Navigation](#2-navigation)
3. [File and Folder Management](#3-file-and-folder-management)
4. [Viewing File Contents](#4-viewing-file-contents)
5. [Searching](#5-searching)
6. [Process Management](#6-process-management)
7. [Networking and Downloads](#7-networking-and-downloads)
8. [Archives](#8-archives)
9. [Getting Help](#9-getting-help)
10. [Operators](#10-operators)
11. [Bonus Essentials](#11-bonus-essentials)
12. [Practice Combos](#12-practice-combos)

---

## 1. System Information

### `echo`: output any text
Prints text (or variable values) to the terminal.

```bash
echo "Hello World"        # prints: Hello World
echo $HOME                # prints your home path
echo "note" > notes.txt   # writes text into a file
```

| Flag | Meaning |
|------|---------|
| `-n` | Do not add a trailing newline |
| `-e` | Enable escape characters like `\n` and `\t` |

### `whoami`: current user
Shows which user you are logged in as.

```bash
whoami        # e.g. tryhackme
```
Related: `id` (shows user ID and groups), `who` (who is logged in).

### `uptime`: how long the system has been running
Shows current time, how long the machine has been up, number of users, and load averages (1, 5, 15 minutes).

```bash
uptime
uptime -p     # pretty format: "up 3 hours, 12 minutes"
uptime -s     # since when the system has been up
```

### `free`: memory usage
Shows total, used, free, and cached RAM and swap.

```bash
free          # in kilobytes
free -h       # human readable (MB / GB)
free -m       # in megabytes
```

### `du`: disk usage of a folder
Shows how much disk space files and folders consume.

```bash
du -h folder/          # sizes of everything inside, human readable
du -sh folder/         # one summary total for the folder
du -h --max-depth=1    # one level deep, great for finding space hogs
```

| Flag | Meaning |
|------|---------|
| `-h` | Human readable sizes |
| `-s` | Summary only |
| `-a` | Include files, not just folders |

Related: `df -h` shows free space on whole disks and partitions.

---

## 2. Navigation

### `pwd`: print working directory
Shows the full path of where you are right now.

```bash
pwd           # e.g. /home/user/projects
```

### `ls`: list directory contents

```bash
ls            # simple list
ls -l         # long format: permissions, owner, size, date
ls -a         # include hidden files (names starting with .)
ls -la        # long format plus hidden files
ls -lh        # long format with human-readable sizes
ls -lt        # sort by modification time, newest first
ls /var/log   # list a different folder
```

### `cd`: change directory

```bash
cd /var/log   # absolute path
cd projects   # relative path
cd ..         # up one level
cd ../..      # up two levels
cd ~          # home directory (same as just: cd)
cd -          # jump back to the previous directory
```

---

## 3. File and Folder Management

### `mkdir`: make a directory

```bash
mkdir photos
mkdir -p project/src/utils    # create nested folders in one go
mkdir a b c                   # create several at once
```

### `touch`: create a new empty file

```bash
touch notes.txt
touch a.txt b.txt c.txt       # several files
```
If the file already exists, `touch` only updates its timestamp.

### `cp`: copy

```bash
cp file.txt backup.txt         # copy a file
cp file.txt /tmp/              # copy into a folder
cp -r myfolder/ myfolder_bak/  # copy a whole folder (recursive)
cp -i a.txt b.txt              # ask before overwriting
```

### `mv`: move or rename

```bash
mv old.txt new.txt         # rename
mv file.txt ~/Documents/   # move
mv -i a.txt b.txt          # ask before overwriting
```

### `rm`: remove

There is no recycle bin. Deleted means gone.

```bash
rm file.txt
rm -i file.txt        # ask for confirmation
rm -r folder/         # delete a folder and its contents
rm -rf folder/        # force delete, no prompts (be very careful)
```

Safe habit: run `ls` first to check what you are about to delete.

---

## 4. Viewing File Contents

### `cat`: concatenate and print
Outputs the contents of files (not just text files).

```bash
cat file.txt
cat -n file.txt          # with line numbers
cat a.txt b.txt          # join and print two files
cat a.txt b.txt > all.txt
```

### `less`: page through large files

```bash
less /var/log/syslog
```

| Key | Action |
|-----|--------|
| `Space` / `f` | Next page |
| `b` | Previous page |
| `/word` | Search forward |
| `n` | Next search match |
| `g` / `G` | Top / bottom of file |
| `q` | Quit |

---

## 5. Searching

### `find`: locate files and folders by name or property

```bash
find / -name "file.txt"             # search whole system by name
find . -name "*.log"                # in current folder, all .log files
find /home -type d -name "photos"   # directories only
find . -type f -size +100M          # files larger than 100 MB
find . -mtime -7                    # modified in the last 7 days
find / -name "file.txt" 2>/dev/null # hide "permission denied" errors
```

| Flag | Meaning |
|------|---------|
| `-name` | Match by name (case sensitive); `-iname` ignores case |
| `-type f` / `-type d` | Files / directories |
| `-size` | Match by size |
| `-mtime` | Match by modification days |

### `grep`: search inside files

```bash
grep "error" log.txt            # lines containing "error"
grep -i "error" log.txt         # ignore case
grep -n "error" log.txt         # show line numbers
grep -c "error" log.txt         # count matching lines
grep -v "error" log.txt         # lines that do NOT match
grep -r "password" /etc/        # search a whole folder recursively
grep -E "fail|denied" log.txt   # match either word
```

### `wc`: word count

```bash
wc file.txt       # lines, words, bytes
wc -l file.txt    # number of lines (entries in a log)
wc -w file.txt    # number of words
wc -c file.txt    # number of bytes
```

---

## 6. Process Management

### `ps`: list running processes

```bash
ps            # processes in your current terminal
ps aux        # every process, with user and resource usage
ps -ef        # alternative full listing
ps aux | grep firefox   # find a specific process
```

Related: `top` or `htop` for a live, updating view.

### `kill`: stop a process

```bash
kill 1234         # polite stop (SIGTERM) for PID 1234
kill -9 1234      # force kill (SIGKILL)
kill -l           # list all signals
killall firefox   # kill by name
```

Workflow: `ps aux | grep name` to find the PID, then `kill PID`.

---

## 7. Networking and Downloads

### `ping`: check connectivity and latency

```bash
ping google.com
ping -c 4 google.com    # send only 4 packets, then stop
```
Without `-c`, ping runs until you press `Ctrl + C`.

### `wget`: download a file from the web

```bash
wget https://example.com/file.zip
wget -O newname.zip https://example.com/file.zip   # save under another name
wget -c https://example.com/big.iso                # resume an interrupted download
wget -b https://example.com/big.iso                # download in the background
```

---

## 8. Archives

### `zip`: compress into a .zip

```bash
zip archive.zip file1.txt file2.txt
zip -r archive.zip myfolder/         # include a whole folder
zip -e secure.zip file.txt           # password protect
```

### `unzip`: extract a .zip

```bash
unzip archive.zip
unzip archive.zip -d /tmp/output     # extract into a chosen folder
unzip -l archive.zip                 # list contents without extracting
```

---

## 9. Getting Help

### `man`: manual pages

```bash
man ls              # full manual for ls
man -k "copy"       # search manuals by keyword
ls --help           # quick built-in summary
```
Navigate with the same keys as `less`. Press `q` to quit.

---

## 10. Operators

### `&`: run in the background

```bash
sleep 60 &          # runs without blocking your terminal
jobs                # list background jobs
fg                  # bring the last one to the foreground
```

### `&&`: chain commands (run next only if previous succeeds)

```bash
mkdir demo && cd demo && touch hello.txt
```
If `mkdir` fails, nothing after it runs.

### `>`: redirect output (overwrites)

```bash
echo "first line" > file.txt     # creates or REPLACES file.txt
ls -la > listing.txt
```

### `>>`: redirect output (appends)

```bash
echo "second line" >> file.txt   # adds to the end, keeps old content
```

### Quick comparison

| Operator | Behavior | Example |
|----------|----------|---------|
| `&` | Run in background | `command &` |
| `&&` | Run next if the first succeeds | `cmd1 && cmd2` |
| `>` | Write output to file, replacing it | `cmd > out.txt` |
| `>>` | Append output to file | `cmd >> out.txt` |

---

## 11. Bonus Essentials

Extra commands worth knowing alongside the basics.

| Command | What it does | Example |
|---------|--------------|---------|
| `\|` (pipe) | Send one command's output into another | `ps aux \| grep ssh` |
| `head` | Show the first lines of a file | `head -n 5 file.txt` |
| `tail` | Show the last lines; `-f` follows live | `tail -f /var/log/syslog` |
| `sort` | Sort lines | `sort names.txt` |
| `uniq` | Remove adjacent duplicate lines | `sort a.txt \| uniq` |
| `chmod` | Change file permissions | `chmod +x script.sh` |
| `chown` | Change file owner | `sudo chown user file.txt` |
| `sudo` | Run a command as administrator | `sudo apt update` |
| `history` | Show previously used commands | `history \| grep ssh` |
| `clear` | Clear the terminal screen | `clear` |
| `df` | Show free disk space | `df -h` |
| `top` | Live view of running processes | `top` |
| `date` | Show current date and time | `date` |
| `tar` | Archive and compress (`.tar.gz`) | `tar -czf out.tar.gz folder/` |

### Handy keyboard shortcuts

| Shortcut | Action |
|----------|--------|
| `Tab` | Auto-complete names |
| `Ctrl + C` | Stop the running command |
| `Ctrl + L` | Clear the screen |
| `Ctrl + A` / `Ctrl + E` | Jump to start / end of the line |
| `Up arrow` | Previous command |

---

## 12. Practice Combos

```bash
# 1. Set up a workspace and add a file
mkdir -p lab/logs && cd lab/logs && touch app.log

# 2. Append some entries
echo "INFO started" >> app.log
echo "ERROR disk full" >> app.log

# 3. Count and search
wc -l app.log
grep -i "error" app.log

# 4. Find the biggest space users in a folder
du -h --max-depth=1 ~ | sort -h

# 5. Find and stop a process
ps aux | grep firefox
kill PID

# 6. Back up and compress
cp -r lab lab_backup && zip -r lab_backup.zip lab_backup
```

---

Tip: when unsure about any command, run `man command` or `command --help`.
