# Linux Fundamentals: Quick Memory Sheet


---

## Commands

### System and Info

**`echo`**
Echo = Echo back. Whatever you say, the terminal repeats.
`echo "Hello"` prints Hello.

**`whoami`**
"Who am I?" Asks the system which user you are logged in as.
Handy before running anything powerful.

**`uptime`**
"How long has this machine been awake?" Shows time up, users, and load.
Think of it as the computer's stopwatch.

**`free`**
"How much memory is free?" Shows RAM used and available.
Add `-h` for human-friendly sizes.

**`du`**
**D**isk **U**sage. Shows how much space a folder eats.
Use `du -sh folder` to find the space hog.

### Processes

**`ps`**
**P**rocess **S**napshot. A photo of what is running right now.
`ps aux` shows everything.

**`kill`**
The off switch for a process. Find the PID with `ps`, then `kill PID`.
Stubborn process? `kill -9 PID`.

### Network

**`ping`**
Sonar for the internet. Sends a signal and times the echo back.
`ping google.com` checks if a site is reachable.

**`wget`**
**W**eb **get**. Grabs a file from a URL and saves it.
`wget URL` is download in one word.

### Navigation

**`pwd`**
**P**rint **W**orking **D**irectory. "Where am I?" in full path form.
Your GPS pin.

**`ls`**
**L**i**s**t. Shows what is in this folder.
`ls -la` shows everything, including hidden files, with details.

**`cd`**
**C**hange **D**irectory. Walk into another folder.
`cd ..` goes up, `cd ~` goes home.

### Files and Folders

**`mkdir`**
**M**a**k**e **dir**ectory. Creates a new folder.
`mkdir -p a/b/c` builds nested folders at once.

**`touch`**
Touch a file and it exists. Creates a new empty file.
Also updates the timestamp of an existing one.

**`cp`**
**C**o**p**y. Duplicates files or folders.
`cp -r` for folders (r = recursive).

**`mv`**
**M**o**v**e. Moves a file, or renames it.
Same command, two jobs: new place or new name.

**`rm`**
**R**e**m**ove. Deletes forever, with no recycle bin.
`rm -r` for folders. Think twice, press once.

### Viewing Content

**`cat`**
Short for con**cat**enate. Dumps a whole file onto the screen.
Best for small files.

**`less`**
Less is more. Reads big files one page at a time.
Space = next page, `q` = quit.

### Searching

**`find`**
Where is it? Hunts files and folders by name.
`find / -name "file.txt"`.

**`grep`**
Search inside files for a word or pattern.
`grep "error" log.txt` shows only the lines you want.

**`wc`**
**W**ord **C**ount. Counts lines, words, and characters.
`wc -l` counts lines (entries in a log).

### Archives

**`zip`**
Pack files into one compressed `.zip`.
`zip out.zip file1 file2`.

**`unzip`**
Unpack a `.zip`.
`unzip out.zip`.

### Help

**`man`**
**Man**ual. Every command's official handbook.
Stuck? `man command`, then `q` to leave.

---

## Operators

| Symbol | Name | Remember It As |
|--------|------|----------------|
| `&` | Background | "And go!" Runs the command in the background so your terminal stays free. |
| `&&` | AND chain | "And then." Runs the next command only if the first one succeeded. |
| `>` | Redirect (overwrite) | One arrow = one winner. Sends output to a file and replaces what was there. |
| `>>` | Redirect (append) | Two arrows = keep going. Adds output to the end of the file and keeps old content. |
