# 🧠 Day 1: Linux Basics & File System (DevOps Linux Mastery)

---

## ✅ 1.1 What is Linux?

### 🔸 What is Linux?
- **Linux** is a free, open-source **Unix-like operating system**.
- It is **kernel-based**, meaning the **Linux kernel controls all hardware**.
- Commonly used in:
  - Servers
  - Cloud platforms
  - DevOps tools
  - Embedded systems

---

### 🔸 Linux Kernel vs. Linux Distribution

| Component           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Linux Kernel**     | The **core of the OS**, written in C. Handles hardware, memory, processes. |
| **Linux Distribution** | A full OS: kernel + tools + software + package manager.                    |

> 🧩 **Analogy:**  
> Think of a **car**:  
> - **Kernel = Engine**  
> - **Distribution = Full car (with steering, seats, dashboard, etc.)**

---

### 🔸 Popular Linux Distributions

| Distro     | Usage Type           | Package Manager |
|------------|----------------------|------------------|
| Ubuntu     | User-friendly, cloud | `apt`            |
| CentOS     | Server-grade         | `yum` / `dnf`    |
| RHEL       | Enterprise-grade     | `yum` / `dnf`    |
| Debian     | Stable, foundational | `apt`            |
| Fedora     | Latest tech & tools  | `dnf`            |
| Alpine     | Minimal, container   | `apk`            |
| Arch       | Rolling release      | `pacman`         |

> 🧠 **Tip:** Start with **Ubuntu** or **CentOS Stream** if you're a beginner.

---

## ✅ 1.2 Linux Boot Process

1. **BIOS/UEFI**: Initializes hardware.
2. **MBR/GPT**: Loads the bootloader (like GRUB).
3. **GRUB**: Selects and loads the Linux kernel.
4. **Kernel**: Initializes hardware drivers.
5. **Initramfs**: Temporary root filesystem to load drivers and mount real `/`.
6. **`init` or `systemd`**: Starts background services.
7. **Login prompt** appears.

> 🧠 Use `journalctl -b` to view full boot logs.

---

## ✅ 1.3 Runlevels vs. Systemd Boot Targets

### 🔸 Traditional Runlevels

| Runlevel | Meaning             |
|----------|---------------------|
| 0        | Halt (Shutdown)     |
| 1        | Single user         |
| 3        | Multi-user (CLI)    |
| 5        | Multi-user + GUI    |
| 6        | Reboot              |

---

### 🔸 Systemd Boot Targets (Modern)

| Target Name         | Old Runlevel | Description             |
|---------------------|--------------|-------------------------|
| `graphical.target`  | 5            | GUI                     |
| `multi-user.target` | 3            | CLI-only multi-user     |
| `rescue.target`     | 1            | Emergency mode          |
| `reboot.target`     | 6            | Reboot                  |
| `poweroff.target`   | 0            | Shutdown                |

> 🔧 Check/set default target:  
```bash
systemctl get-default  
systemctl set-default multi-user.target
````

---

## ✅ 1.4 Linux Directory Structure

Linux uses a **hierarchical tree structure** rooted at `/`.

| Directory | Description                            |
|-----------|----------------------------------------|
| `/`       | Root of the filesystem                 |
| `/`       | Root of the filesystem                 |
| `/bin`    | Essential system binaries (`ls`, `cp`) |
| `/sbin`   | System management binaries             |
| `/etc`    | System-wide configuration files        |
| `/home`   | Users’ personal data                   |
| `/var`    | Logs, mail, spools, changing files     |
| `/usr`    | User utilities and applications        |
| `/opt`    | Optional/additional software           |
| `/tmp`    | Temporary files                        |
| `/boot`   | Kernel and bootloader files            |
| `/dev`    | Device files (USB, HDD, etc.)          |
| `/proc`   | Kernel and process info (virtual FS)   |
| `/sys`    | System and hardware info               |
| `/mnt`    | Temporary mount points                 |
| `/media`  | Mount points for external media        |
| `/srv`    | Services’ data                         |

> 🧪 Try:

```bash
ls -l /
tree /
```

---

## ✅ 1.5 Linux File Types

Every file in Linux is classified by **type**, not just content.

| Symbol | Type              | Description                       |
| ------ | ----------------- | --------------------------------- |
| `-`    | Regular File      | Text, binary, etc.                |
| `d`    | Directory         | Folder                            |
| `l`    | Symlink           | Shortcut or soft link             |
| `b`    | Block Device      | Disk devices (e.g., `/dev/sda`)   |
| `c`    | Character Device  | Input devices (e.g., keyboard)    |
| `s`    | Socket            | Inter-process communication       |
| `p`    | Named Pipe (FIFO) | Inter-process communication       |
| `h`    | Hard Link         | Alternate name for existing inode |

> 📌 Commands to identify:

```bash
ls -l
file filename
stat filename
```

### 🔸 Examples:

```bash
file /bin/bash
readlink /bin/sh
ln file1 file2     # hard link
mkfifo mypipe      # named pipe
```

---

## ✅ 1.6 Filesystem Navigation

| Command    | Description                                 |
| ---------- | ------------------------------------------- |
| `pwd`      | Show current directory                      |
| `ls`       | List directory contents                     |
| `cd`       | Change directory                            |
| `tree`     | Show folder structure (install via apt/yum) |
| `file`     | Show file type                              |
| `ls -l`    | Long format list with permissions           |
| `ls -a`    | Show hidden files                           |
| `cd ~`     | Go to home directory                        |
| `cd -`     | Go to previous directory                    |
| `readlink` | Show where a symlink points                 |

---

## ✅ 1.7 Environment Variables

Environment variables are global settings available to all processes.

| Command                       | Description                    |
| ----------------------------- | ------------------------------ |
| `printenv`                    | Show all environment variables |
| `env`                         | Display environment            |
| `export VAR=value`            | Set a new variable             |
| `echo $VAR`                   | Access a variable              |
| `echo $PATH`                  | View PATH variable             |
| `export PATH=$PATH:/new/path` | Add to PATH                    |

---

## 🧪 Mini Practice Tasks (Hands-On)

Try these in your Linux terminal:

```bash
pwd                         # Show current dir
cd /etc && ls -l            # Go to /etc and list
file /bin/bash              # Check file type
tree /home                  # View folder tree (install tree first)
cd ~                        # Go to home
readlink /bin/sh            # See symlink target
printenv | less             # View environment vars
echo $PATH                  # Show PATH
```

---

## ✅ Day 1 Summary

You now understand:

* ✅ What Linux is and key distributions
* ✅ Kernel vs distribution (core vs full OS)
* ✅ Linux boot process (BIOS to login)
* ✅ Runlevels and systemd targets
* ✅ Filesystem layout and directory purpose
* ✅ File types including symlinks, pipes, sockets, etc.
* ✅ Navigation commands and environment variables

---