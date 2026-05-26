# 🐧 Linux Basics + Vim + User Management + Tar Command (Revision Notes)

---

# 📁 1. File & Directory Basics

### 📍 Path Types

* **Absolute path** → starts from root `/`

  * Example: `/home/user/file.txt`
* **Relative path** → depends on current directory

  * Example: `file.txt`, `./file.txt`, `../file.txt`

---

### 📍 Basic Commands

* `uname` → system information
* `ls -ltr` → long list sorted by time (old → new)
* `ls -la` → show hidden files + detailed info
* `touch file.txt` → create empty file
* `cat file.txt` → view file content
* `cat > file.txt` → create & write file (overwrite)
* `cat >> file.txt` → append content

---

### 📍 File/Directory Operations

* `rm file.txt` → delete file
* `rmdir folder` → delete empty directory
* `cp source dest` → copy file/folder
* `mv source dest` → move or rename
* `head file` → first 10 lines
* `tail file` → last 10 lines

---

# 🌐 2. Download & Search Tools

* `wget <url>` → download files
* `curl <url>` → fetch data from URL

---

### 🔍 Search & Text Processing

* `grep "text" file` → search text in file
* `cut` → extract columns
* `awk` → advanced text processing

#### Examples:

```bash
cut -d ":" -f1
```

→ split by `:` and print first field

```bash
awk -F ":" '{print $NF}'
```

→ print last field

```bash
awk -F ":" '$3>=1000 {print $1, $3}'
```

→ users with UID ≥ 1000

---

# ✍️ 3. Vim Editor (Important)

### 📌 Open file

```bash
vim filename
```

---

## 🔵 Colon Mode (Command Mode)

| Command   | Description               |
| --------- | ------------------------- |
| `:q`      | quit                      |
| `:wq`     | save & quit               |
| `:q!`     | force quit without saving |
| `:set nu` | show line numbers         |
| `:10`     | go to line 10             |
| `:/word`  | search top → bottom       |
| `:?word`  | search bottom → top       |
| `:10d`    | delete line 10            |
| `:%d`     | delete entire file        |
| `:noh`    | remove search highlight   |

### Replace

* Replace first occurrence in line:

```bash
:10s/old/new
```

* Replace all in line:

```bash
:10s/old/new/g
```

* Replace all lines:

```bash
:%s/old/new/g
```

---

## 🟢 Normal Mode (Esc Mode)

| Key        | Function       |
| ---------- | -------------- |
| `gg`       | top of file    |
| `G`        | bottom of file |
| `u`        | undo           |
| `Ctrl + r` | redo           |
| `dd`       | delete line    |
| `yy`       | copy line      |
| `p`        | paste below    |
| `P`        | paste above    |

---

# 👥 4. User Management (Linux)

## 📌 Concept

| Entity      | Meaning             |
| ----------- | ------------------- |
| User        | individual account  |
| Group       | collection of users |
| Roles       | job position        |
| Permissions | access rights       |

---

## 🔄 CRUD Operations

### ➕ Create User

```bash
useradd ramesh
```

### 🔍 Check user info

```bash
id ramesh
```

```bash
cat /etc/passwd
cat /etc/group
```

---

## 👥 Groups

* Each user has:

  * 1 primary group
  * multiple secondary groups

### Create group

```bash
groupadd devops
```

---

### Assign user to group

* Primary group:

```bash
usermod -g devops ramesh
```

* Secondary group:

```bash
usermod -aG testing ramesh
```

---

### Set password

```bash
passwd ramesh
```

---

## 🔐 SSH Configuration

* File:

```bash
/etc/ssh/sshd_config
```

* Validate config:

```bash
sshd -t
```

* Default auth: **key-based authentication**

---

## 🛡️ Sudo Access

* File:

```bash
/etc/sudoers
```

---

## ❌ Remove user from group

```bash
gpasswd -d ramesh devops
```

---

## 🧨 Delete user

```bash
userdel -r ramesh
```

* `-r` → removes home directory too

---

## 🚨 User removal best practice

1. Lock user immediately
2. Remove from all groups
3. Backup home directory
4. Delete user

---

# 📦 5. Tar Command (Archiving)

### 📌 What is tar?

* Used to combine multiple files into one archive
* Common in Linux backups and deployments

---

## 📦 Create archive

```bash
tar -cf file.tar folder/
```

---

## 📤 Extract archive

```bash
tar -xf file.tar
```

---

## 📌 tar.gz (compressed archive)

* `.tar.gz` = tar + gzip compression

### Create:

```bash
tar -czf file.tar.gz folder/
```

### Extract:

```bash
tar -xzf file.tar.gz
```

---

# ⚡ Quick Revision Summary

* Paths: absolute vs relative
* File ops: `cp, mv, rm, cat`
* Search: `grep, awk, cut`
* Vim: edit + navigate + replace + save
* Users: `useradd, usermod, groupadd, passwd`
* Permissions: groups + sudo
* Archive: `tar -cf`, `tar -xzf`
