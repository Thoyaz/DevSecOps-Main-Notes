# Linux Commands Notes

## 1. Paths in Linux

### Absolute Path

* Full path from the root directory `/`
* Starts with `/`

Example:

```bash
/c/devops/daws-88s/daws-88s
```

### Relative Path

* Path relative to the current directory
* Does not start with `/`

Example:

```bash
daws-88s/daws-88s
```

---

# 2. Basic Linux Navigation

## `cd` → Change Directory

### Go to a specific directory

```bash
cd /home/ec2-user
```

### Go to home directory

```bash
cd
```

---

## `clear` → Clear Terminal Screen

```bash
clear
```

---

# 3. Users in Linux

## Normal User

```bash
$
```

Example home directory:

```bash
/home/ec2-user
```

Format:

```bash
/home/<user-name>
```

---

## Root User / Super User

Switch to root:

```bash
sudo su
```

Root prompt:

```bash
#
```

Root home directory:

```bash
/root
```

---

# 4. Important Linux Concept

> Everything in Linux is treated as a file or text.

---

# 5. Command Syntax

General command format:

```bash
command-name <inputs> <options>
```

Example:

```bash
ls -l
```

* `command-name` → actual command
* `inputs` → files/directories
* `options` → modifiers like `-l`, `-a`

Some commands may require inputs/options while others are optional.

---

# 6. System Information Commands

## `uname` → Display OS/Kernel Information

```bash
uname
```

### Help options

```bash
uname --help
```

or

```bash
man uname
```

---

# 7. CRUD Operations

CRUD stands for:

* **C** → Create
* **R** → Read
* **U** → Update
* **D** → Delete

---

# 8. Listing Files & Directories

## `ls` → List files and directories

### Basic listing

```bash
ls
```

### Long format

```bash
ls -l
```

Shows:

* File permissions
* Owner
* Size
* Timestamp

### Reverse order

```bash
ls -lr
```

### Latest files on top

```bash
ls -lt
```

### Latest files at bottom

```bash
ls -ltr
```

---

## Hidden Files & Directories

Files/folders starting with `.` are hidden.

Example:

```bash
.git
```

### Show hidden files

```bash
ls -lart
```

Options:

* `-a` → all files
* `-r` → reverse
* `-t` → sort by time
* `-l` → long format

---

# 9. File Permissions

Example:

```bash
drwxr-xr-x
```

* `d` → directory
* `-` → file

Permission groups:

```text
owner | group | others
```

Permissions:

* `r` → read
* `w` → write
* `x` → execute

---

# 10. Creating & Reading Files

## Create a file using `cat`

```bash
cat > devops.txt
```

Type content and then press:

```text
Enter
Ctrl + D
```

---

## Read file content

```bash
cat devops.txt
```

---

# 11. Redirection Operators

## `>` → Override existing content

```bash
echo "Hello" > file.txt
```

---

## `>>` → Append content

```bash
echo "World" >> file.txt
```

---

# 12. Copy Files

## `cp` → Copy files/directories

Syntax:

```bash
cp <source> <destination>
```

Example:

```bash
cp file1.txt backup/
```

---

# 13. Move or Rename Files

## `mv`

### Rename file

```bash
mv old.txt new.txt
```

### Move file

```bash
mv file.txt /tmp/
```

---

# 14. Downloading Files

## `wget`

Used for downloading packages/files.

Example:

```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.113/bin/apache-tomcat-9.0.113.tar.gz
```

---

## `curl`

* Used for APIs
* Displays output on terminal by default
* Does not download automatically like `wget`

Example:

```bash
curl https://example.com
```

---

# 15. Searching Inside Files

## `grep`

Syntax:

```bash
grep <word-to-search> <file>
```

Example:

```bash
grep error logs.txt
```

---

## Common `grep` Options

### Case insensitive

```bash
grep -i error logs.txt
```

### Non-matching lines

```bash
grep -v error logs.txt
```

### Show line numbers

```bash
grep -n error logs.txt
```

### Count matching lines

```bash
grep -c error logs.txt
```

---

# 16. Special Characters in Search

## `$` → End of line

Example:

```bash
grep "architecture$" file.txt
```

Searches lines ending with:

```text
architecture
```

---

## `^` → Start of line

Example:

```bash
grep "^root" file.txt
```

Searches lines starting with:

```text
root
```

---

# 17. Command History Search

## `Ctrl + R`

Used to search previously executed commands.

Steps:

1. Press:

```text
Ctrl + R
```

2. Start typing command

3. Matching previous commands appear automatically

---

# 18. Monitoring Logs

## `tail -f`

Follow live logs continuously.

```bash
tail -f logfile.log
```

---

# 19. Viewing File Content

## `head`

Displays top 10 lines by default.

```bash
head file.txt
```

---

## `tail`

Displays bottom 10 lines by default.

```bash
tail file.txt
```

---

# 20. Text Processing Commands

## `cut`

Used to split text using delimiters.

Example:

```bash
cut -d "/" -f1 file.txt
```

Where:

* `-d` → delimiter
* `-f` → field number

---

## Example File

```bash
/etc/passwd
```

---

## `awk`

Powerful text-processing command.

Example:

```bash
awk -F "/" '{print $NF}'
```

Where:

* `-F` → delimiter
* `$NF` → last field

---

# 21. Useful Practice URL

Session notes:
[GitHub Notes Repository](https://raw.githubusercontent.com/daws-88s/notes/refs/heads/main/session-02.txt?utm_source=chatgpt.com)

---

# Quick Revision Table

| Command   | Purpose                   |
| --------- | ------------------------- |
| `cd`      | Change directory          |
| `ls`      | List files/directories    |
| `pwd`     | Present working directory |
| `cat`     | Create/read files         |
| `cp`      | Copy files                |
| `mv`      | Move/rename files         |
| `grep`    | Search text               |
| `wget`    | Download files            |
| `curl`    | Hit URLs/APIs             |
| `head`    | Top lines                 |
| `tail`    | Bottom lines              |
| `tail -f` | Live log monitoring       |
| `cut`     | Split text                |
| `awk`     | Text processing           |
| `uname`   | OS/kernel information     |
