# Linux Storage & Filesystem Notes

## Index

1. [Linux Filesystem Hierarchy](#1-linux-filesystem-hierarchy)
2. [Hard Disk vs Network Disk](#2-hard-disk-vs-network-disk)
3. [Adding an Extra Disk to a Linux Server](#3-adding-an-extra-disk-to-a-linux-server)
4. [Partitioning and Mounting a New Disk](#4-partitioning-and-mounting-a-new-disk)
5. [Persistent Mount Using UUID](#5-persistent-mount-using-uuid)
6. [Disk, Memory, and Storage Monitoring Commands](#6-disk-memory-and-storage-monitoring-commands)
7. [Resizing an Existing Disk](#7-resizing-an-existing-disk)
8. [Important Directories for Databases](#8-important-directories-for-databases)
9. [Quick Revision Notes](#9-quick-revision-notes)
10. [Topics for Next Class](#10-topics-for-next-class)

---

# 1. Linux Filesystem Hierarchy

Linux follows a standard directory structure where each directory has a specific purpose.

## /bin

Essential user commands and binaries.

Examples:

* ls
* cp
* mv
* cat

---

## /boot

Contains files required during the operating system boot process.

Examples:

* Kernel files
* Bootloader files (GRUB)

---

## /dev

Contains device files.

In Linux, everything is treated as a file, including:

* Hard disks
* USB drives
* Keyboard
* Mouse
* Network interfaces

Examples:

```bash
/dev/nvme0n1
/dev/sda
/dev/null
```

---

## /etc

Stores system-wide configuration files.

Examples:

```bash
/etc/fstab
/etc/passwd
/etc/ssh/sshd_config
```

---

## /home

Contains home directories of normal users.

Example:

```bash
/home/ec2-user
/home/ubuntu
/home/student
```

---

## /lib and /lib64

Stores shared libraries required by commands and applications.

Similar to DLL files in Windows.

---

## /media

Used for automatically mounted removable devices.

Examples:

* USB drives
* DVD/CD

---

## /mnt

Temporary mount location for additional storage devices.

Commonly used in Linux servers.

Example:

```bash
/mnt
```

---

## /opt

Used for manually installed third-party applications.

Examples:

```bash
/opt/tomcat
/opt/roboshop
/opt/jobs
```

---

## /proc

Virtual filesystem containing kernel and process information.

Examples:

```bash
/proc/cpuinfo
/proc/meminfo
```

---

## /root

Home directory of the root user.

Example:

```bash
/root
```

---

## /run

Stores runtime information of currently running processes.

---

## /sbin

Contains essential system administration commands.

Examples:

```bash
fdisk
mkfs
reboot
shutdown
```

---

## /srv

Contains service-related data.

Examples:

* Website files
* NFS shared directories

---

## /swap

Virtual memory used when RAM becomes insufficient.

High swap usage generally indicates memory pressure.

---

## /sys

Contains information about kernel subsystems and hardware.

---

## /tmp

Temporary storage location.

Files here may be deleted automatically after reboot.

---

## /usr

Contains user applications, binaries, and libraries.

Examples:

```bash
/usr/bin
/usr/lib
```

---

## /var

Stores variable and continuously growing files.

Examples:

```bash
/var/log
/var/cache
/var/lib/mysql
```

---

# 2. Hard Disk vs Network Disk

## Hard Disk (Local Storage)

Storage physically attached to the server.

Examples:

* SSD
* HDD
* EBS volume attached to EC2

### Advantages

* Low latency
* High performance
* Best for operating systems and databases

### Use Cases

* OS installation
* Database storage
* Critical application data

---

## Network Disk (Remote Storage)

Storage accessible over a network or internet.

Examples:

* Amazon S3
* Google Drive
* Microsoft OneDrive
* NFS Storage

### Advantages

* Accessible from multiple systems
* Easy sharing
* High scalability

### Use Cases

* Backups
* Images
* Videos
* Documents
* Object storage

---

## Comparison

| Feature             | Hard Disk          | Network Disk            |
| ------------------- | ------------------ | ----------------------- |
| Location            | Attached to server | Remote                  |
| Latency             | Low                | Higher                  |
| Performance         | Fast               | Slower                  |
| Multi-System Access | No                 | Yes                     |
| OS Storage          | Recommended        | Not Recommended         |
| Database Storage    | Recommended        | Usually Not Recommended |

### Important Note

* Operating Systems should always be installed on local disks.
* Databases should generally use local disks because latency is critical.
* Media files, backups, and objects can be stored in network storage.

---

# 3. Adding an Extra Disk to a Linux Server

Example: AWS EC2 + EBS Volume

## Step 1: Create an EBS Volume

Create a new EBS volume from AWS Console.

---

## Step 2: Attach Volume

Attach the volume to the EC2 instance.

Important:

* EBS Volume and EC2 instance must be in the same Availability Zone (AZ).

---

## Step 3: Verify Attached Disks

List block devices:

```bash
lsblk
```

Example:

```text
nvme0n1  -> Root Disk
nvme1n1  -> Newly Attached Disk
```

Where:

* nvme0n1 = Operating System Disk
* nvme1n1 = New Data Disk

---

# 4. Partitioning and Mounting a New Disk

## Create GPT Partition

```bash
sudo parted /dev/nvme1n1 --script mklabel gpt mkpart primary 0% 100%
```

Meaning:

* Create GPT partition table
* Create one primary partition
* Use entire disk

---

## Verify Partition

```bash
lsblk
```

Expected:

```text
nvme1n1
└── nvme1n1p1
```

---

## Create Filesystem

Example (XFS):

```bash
mkfs.xfs /dev/nvme1n1p1
```

---

## Create Mount Point

```bash
mkdir /data
```

---

## Mount Disk

```bash
mount /dev/nvme1n1p1 /data
```

---

## Verify Mount

```bash
df -hT
```

---

# 5. Persistent Mount Using UUID

If the server reboots, manual mounts are lost.

Use UUID in `/etc/fstab` for permanent mounting.

---

## Get UUID

```bash
blkid
```

Example:

```text
UUID="0683949b-ce15-4d77-b202-4d47ee2a863a"
```

---

## Add Entry to fstab

```text
UUID=0683949b-ce15-4d77-b202-4d47ee2a863a   /data   xfs   defaults,nofail   0   2
```

### Fields Explanation

| Field           | Meaning                |
| --------------- | ---------------------- |
| UUID            | Disk Identifier        |
| /data           | Mount Point            |
| xfs             | Filesystem Type        |
| defaults,nofail | Mount Options          |
| 0               | Dump                   |
| 2               | Filesystem Check Order |

---

## Verify fstab

```bash
mount -a
```

No output = Configuration is correct.

---

# 6. Disk, Memory, and Storage Monitoring Commands

## Disk Usage

```bash
df -hT
```

Shows:

* Mounted filesystems
* Filesystem type
* Total size
* Used space
* Free space

---

## RAM Usage

```bash
free -m
```

Shows:

* Total RAM
* Used RAM
* Free RAM
* Swap Usage

---

## Top Memory Consuming Processes

```bash
ps aux --sort -rss | head -10
```

Shows:

* Top processes using RAM

---

## Directory Size

```bash
du -sh *
```

Shows size occupied by files and folders.

Example:

```bash
du -sh /var/*
```

---

# 7. Resizing an Existing Disk

When EBS volume size is increased, Linux must also expand the partition and filesystem.

---

## Step 1: Extend Partition

```bash
growpart /dev/nvme1n1 1
```

Where:

* nvme1n1 = Disk
* 1 = Partition Number

---

## Step 2: Extend Filesystem

For XFS filesystem:

```bash
xfs_growfs /data
```

---

## Step 3: Verify

```bash
df -hT
```

New disk size should be visible.

---

# 8. Important Directories for Databases

## MySQL

```bash
/var/lib/mysql
```

MySQL stores database files here by default.

---

## Redis

Common custom location:

```bash
/data
```

Redis persistence files are often stored here.

---

# 9. Quick Revision Notes

### Important Commands

```bash
lsblk
blkid
df -hT
free -m
du -sh *
mount -a
```

### Create Partition

```bash
parted /dev/nvme1n1 --script mklabel gpt mkpart primary 0% 100%
```

### Create Filesystem

```bash
mkfs.xfs /dev/nvme1n1p1
```

### Mount Disk

```bash
mount /dev/nvme1n1p1 /data
```

### Resize Partition

```bash
growpart /dev/nvme1n1 1
```

### Resize XFS Filesystem

```bash
xfs_growfs /data
```

---

# 10. Topics for Next Class

## Inode

* What is an inode?
* Metadata stored in inode
* File ownership and permissions

## Hard Link

* Multiple filenames pointing to same inode
* Shares same data blocks

## Symbolic Link (Symlink)

* Shortcut to another file or directory
* Similar to Windows shortcut

## Shell Scripting

* Variables
* Conditions
* Loops
* Functions
* Automation scripts

---

# One-Line Summary

Linux storage management mainly involves understanding filesystem hierarchy, managing disks and partitions, mounting storage using UUIDs, monitoring disk/memory usage, and safely expanding storage when requirements grow.
