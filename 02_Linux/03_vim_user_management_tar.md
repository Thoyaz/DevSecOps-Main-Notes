# 📘 Linux + Vim + User Management + Tar — Revision Notes

---

# 📑 Index

* [1. File & Directory Basics](#1-file--directory-basics)
* [2. Download & Search Tools](#2-download--search-tools)
* [3. Vim Editor](#3-vim-editor-important)
* [4. User Management](#4-user-management-linux)
* [5. Tar Command](#5-tar-command-archiving)
* [Quick Revision Summary](#quick-revision-summary)

---

# 📁 1. File & Directory Basics

### 📍 Path Types

* **Absolute path** → `/home/user/file.txt`
* **Relative path** → `file.txt`, `./file.txt`, `../file.txt`

### 📍 Basic Commands

* `uname` → system info
* `ls -ltr` → long list sorted by time
* `ls -la` → show hidden files
* `touch file.txt` → create file
* `cat file.txt` → view file
* `cat > file.txt` → write (overwrite)
* `cat >> file.txt` → append

### 📍 File Operations

* `rm file`
* `rmdir folder`
* `cp source dest`
* `mv source dest`
* `head file`
* `tail file`

---

# 🌐 2. Download & Search Tools

* `wget url` → download file
* `curl url` → fetch content

### 🔍 Search Tools

* `grep "text" file` → search text
* `cut -d ":" -f1` → split by delimiter
* `awk` → advanced processing

Examples:

```bash
awk -F ":" '{print $NF}'
awk -F ":" '$3>=1000 {print $1, $3}'
```

---

# ✍️ 3. Vim Editor (Important)

### 📌 Open file

```bash
vim filename
```

---

## 🔵 Colon Mode Commands

* `:q` → quit
* `:wq` → save & quit
* `:q!` → force quit
* `:set nu` → line numbers
* `:10` → go to line
* `:/word` → search down
* `:?word` → search up
* `:%d` → delete all
* `:noh` → remove highlight

### Replace

* `:10s/old/new`
* `:10s/old/new/g`
* `:%s/old/new/g`

---

## 🟢 Normal Mode (Esc)

* `gg` → top
* `G` → bottom
* `u` → undo
* `Ctrl+r` → redo
* `dd` → delete line
* `yy` → copy line
* `p` → paste below
* `P` → paste above

---

# 👥 4. User Management (Linux)

### Concepts

* User → person account
* Group → collection of users
* Permissions → access control

---

### CRUD Commands

```bash
useradd ramesh
id ramesh
cat /etc/passwd
cat /etc/group
```

---

### Groups

```bash
groupadd devops
usermod -g devops ramesh
usermod -aG testing ramesh
```

---

### Password

```bash
passwd ramesh
```

---

### SSH Config

* `/etc/ssh/sshd_config`
* `sshd -t` → test config

---

### Sudo Access

* `/etc/sudoers`

---

### Remove user from group

```bash
gpasswd -d ramesh devops
```

---

### Delete user

```bash
userdel -r ramesh
```

---

### Best practice steps

1. Lock user
2. Remove from groups
3. Backup home folder
4. Delete user

---

# 📦 5. Tar Command (Archiving)

### Create archive

```bash
tar -cf file.tar folder/
```

### Extract archive

```bash
tar -xf file.tar
```

### gzip format

```bash
tar -czf file.tar.gz folder/
tar -xzf file.tar.gz
```

---

# ⚡ Quick Revision Summary

* File handling: `cp, mv, rm, cat`
* Search: `grep, cut, awk`
* Vim: edit, navigate, replace
* Users: `useradd, usermod, groupadd`
* Security: sudo, ssh config
* Archive: `tar -cf`, `tar -xzf`
