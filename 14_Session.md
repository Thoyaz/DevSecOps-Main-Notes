# 📚 Linux + Git + Shell Scripting Notes

## 📌 Index

* [Inode, Symlink, Hardlink](#inode-symlink-hardlink)
* [Version Control System (VCS)](#version-control-system-vcs)
* [Centralised vs Distributed VCS](#centralised-vs-distributed-vcs)
* [Git Basics & Commands](#git-basics--commands)
* [Shebang](#shebang)
* [Hello World Shell Script](#hello-world-shell-script)
* [Jenkins & Package Managers Note](#jenkins--package-managers-note)
* [Key Takeaways](#key-takeaways)
* [Tomorrow’s Topics](#tomorrows-topics)

---

## 📁 Inode, Symlink, Hardlink

### 🧠 Inode

* Inode stores **metadata of a file/directory**
* Does NOT store actual file content
* Stores:

  * File type (file / directory / link)
  * Owner & group
  * Permissions
  * Size
  * Timestamps (create, modify, etc.)
  * Pointers to actual data blocks (memory location)

---

### 🔗 Symlink (Soft Link)

* Also called **shortcut**
* Points to another file/folder
* Has a **different inode number**
* If original file is deleted → symlink breaks
* Can be created for:

  * Files ✔️
  * Directories ✔️
* Can work across different filesystems ✔️
* Used for:

  * Version switching
  * Rollback
  * Backward compatibility

---

### 🔗 Hard Link

* Same file with another name
* Shares the **same inode number**
* Points to same data blocks
* No extra memory usage
* Cannot cross filesystems ❌
* Cannot be created for directories ❌
* Used for backups
* File is deleted only when **all hard links are removed**

---

## 🧾 Version Control System (VCS)

* Stores code history and changes
* Tracks:

  * Who changed
  * When changed
  * What changed
* Helps in:

  * Code recovery
  * Collaboration
  * Review (Pull Requests)
  * Secure storage of code

---

## 🌐 Centralised vs Distributed VCS

### 📦 Centralised (e.g., SVN)

* Single central server
* All users connect to it

### 🌍 Distributed (e.g., Git)

* Every user has full copy (repo + history)
* Works offline
* Faster and more reliable

---

## ⚙️ Git Basics & Commands

### 📥 Clone (First step)

```bash
git clone <repo-url>
```

* Downloads repository for first time

---

### ➕ Add (Staging area)

```bash
git add <file-name>
```

* Moves changes to staging area

---

### 💾 Commit (Local repo)

```bash
git commit -m "message"
```

* Saves snapshot locally

---

### 🚀 Push (Remote repo)

```bash
git push origin main
```

* Sends code to GitHub/Git server

---

### 📥 Pull

```bash
git pull origin main
```

* Fetch + merge latest changes

---

### ⚙️ Git Config (First setup)

```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

---

## 🧾 Shebang

```bash
#!/bin/bash
```

* Tells system which interpreter to use
* Used in shell scripts
* Ensures script runs using Bash shell

---

## 🖥️ Hello World Shell Script

### Example:

```bash
#!/bin/bash

echo "Hello World"
```

### Run:

```bash
chmod +x script.sh
./script.sh
```

---

## 🧩 Jenkins & Package Managers Note

### Jenkins path idea:

```
/var/lib/jenkins -> jenkins-2.8
/var/lib/jenkins -> jenkins-2.9
```

* Symlink used to switch versions easily

---

### Package Managers

* **YUM** → Used in RHEL before version 8
* **DNF** → Used in RHEL 8 and later
