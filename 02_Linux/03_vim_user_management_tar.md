# 📘 Linux + Vim + User Management + Tar — Revision Notes

---

# 📑 Index

* [File & Directory Basics](#file--directory-basics)
* [Download & Search Tools](#download--search-tools)
* [Vim Editor](#vim-editor-important)
* [User Management (Linux)](#user-management-linux)
* [Tar Command](#tar-command-archiving)
* [Quick Revision Summary](#quick-revision-summary)

---

# 📁 File & Directory Basics

### 📍 Path Types

* **Absolute path** → `/home/user/file.txt`
* **Relative path** → `file.txt`, `./file.txt`, `../file.txt`

### 📍 Basic Commands

* `uname` → system info
* `ls -ltr` → long list sorted by time
* `ls -la` → hidden files + details
* `touch file.txt` → create file
* `cat file.txt` → view file
* `cat > file.txt` → overwrite file
* `cat >> file.txt` → append file

### 📍 File Operations

* `rm file` → delete file
* `rmdir folder` → remove empty directory
* `cp source dest` → copy
* `mv source dest` → move/rename
* `head file` → first lines
* `tail file` → last lines

---

# 🌐 Download & Search Tools

* `wget url` → download files
* `curl url` → fetch data

### 🔍 Search Tools

* `grep "text" file` → search text
* `cut -d ":" -f1` → split by delimiter
* `awk` → advanced processing

#### Examples

```bash
awk -F ":" '{print $NF}'
awk -F ":" '$3>=1000 {print $1, $3}'
```

---

# ✍️ Vim Editor (Important)

### 📌 Open file

```bash
vim filename
```

---

## 🔵 Colon Mode Commands

* `:q` → quit
* `:wq` → save & quit
* `:q!` → force quit
* `:set nu` → show line numbers
* `:10` → go to line
* `:/word` → search top → bottom
* `:?word` → search bottom → top
* `:%d` → delete entire file
* `:noh` → remove highlight

### Replace

* `:10s/old/new`
* `:10s/old/new/g`
* `:%s/old/new/g`

---

## 🟢 Normal Mode (Esc)

* `gg` → top of file
* `G` → bottom of file
* `u` → undo
* `Ctrl + r` → redo
* `dd` → delete line
* `yy` → copy line
* `p` → paste below
* `P` → paste above

---

# 👥 User Management (Linux)

### 📌 Concepts

* **User** → individual account
* **Group** → collection of users
* **Permissions** → access control

---

### 🧾 User Commands

```bash
useradd ramesh
id ramesh
cat /etc/passwd
cat /etc/group
```

---

### 👥 Group Commands

```bash
groupadd devops
usermod -g devops ramesh
usermod -aG testing ramesh
```

---

### 🔐 Password

```bash
passwd ramesh
```

---

### ⚙️ SSH Config

* File: `/etc/ssh/sshd_config`
* Validate:

```bash
sshd -t
```

---

### 🛡️ Sudo Access

* File: `/etc/sudoers`

---

### ❌ Remove user from group

```bash
gpasswd -d ramesh devops
```

---

### 🧨 Delete user

```bash
userdel -r ramesh
```

---

### 🚨 Best Practice Steps

1. Lock user
2. Remove from all groups
3. Backup home directory
4. Delete user

---

# 📦 Tar Command (Archiving)

### 📁 Create archive

```bash
tar -cf file.tar folder/
```

### 📂 Extract archive

```bash
tar -xf file.tar
```

### 🗜️ gzip compressed archive

```bash
tar -czf file.tar.gz folder/
tar -xzf file.tar.gz
```

---

# ⚡ Quick Revision Summary

* File handling → `cp, mv, rm, cat`
* Search → `grep, cut, awk`
* Vim → editing + navigation + replace
* Users → `useradd, usermod, groupadd`
* Security → sudo + ssh config
* Archive → `tar -cf`, `tar -xzf`
