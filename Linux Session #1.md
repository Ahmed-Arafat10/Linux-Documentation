# **📘 Linux Basics — Session #1**

---

## **1. Understanding the Kernel**

* **Kernel** is the **heart and core** of any operating system.
* It is responsible for **low-level operations** such as:

  * Disk management
  * Memory management
  * Task management

### **System Structure Overview**

```
  -----------------
     Application
  -----------------
        Kernel
-------------------------
 CPU | Memory | Devices
-------------------------
```

---

## **2. Why Linux?**

1. **FOSS** — Free and Open-Source Software
2. **Secure** — Strong permission and user system
3. **Stable and High Performance** — Efficient and reliable under heavy loads

---

## **3. Linux Distribution (Distro)**

> A **Linux Distribution** is an operating system built from a collection of software based on the **Linux kernel**.
> Examples: Ubuntu, Fedora, Debian, Arch Linux, Red Hat, etc.

---

## **4. Linux File Hierarchy**

```
                        /  (root)
         /bin     /proc     /boot     /etc     /home     /lib     /var
    System     Device Info  Booting   Config   User Dirs  Libs   Logs/Cache
   Binaries
```

* Everything starts from the root `/`
* Every **file and directory** in Linux is part of a single **tree structure**

---

## **5. Common Linux Commands**

### **Working with Directories**

| Task                   | Command     | Notes                              |
|------------------------|-------------|------------------------------------|
| Show current directory | `pwd`       | → `/home/arafat`                   |
| List contents          | `ls`        | Lists visible files                |
| List hidden files      | `ls -a`     | Files starting with `.` are hidden |
| Change directory       | `cd <path>` | Example: `cd /etc`                 |
| Go back one directory  | `cd ..`     | Example: `/home/ahmed → /home`     |
| Go to home directory   | `cd ~`      | Shortcut for `/home/user`          |

---

### **Full Path vs Relative Path**

* **Full (Absolute) Path:** Starts from root `/`
  → `cd /home/ahmed/music`
* **Relative Path:** From current directory
  → `cd ../../Downloads`

> `{..}` means parent directory, `.` means current directory.

---

### **Create Directories and Files**

| Task                      | Command                        | Description                      |
|---------------------------|--------------------------------|----------------------------------|
| Create directory          | `mkdir <DirName>`              | Creates folder in current path   |
| Create nested directories | `mkdir -p <Dir1>/<Dir2>`       | Creates parent dirs if not exist |
| Create file(s)            | `touch <FileName> [File2Name]` | Creates empty files              |
| Show file type            | `file <FileName>`              | Detects file content type        |

> **Note:** File extensions are not mandatory in Linux.
> Used only for clarity (e.g., `.txt`, `.png`, `.mp4`, `.gz`).

---

### **Copying and Moving Files**

| Task                     | Command                          | Example                   |
|--------------------------|----------------------------------|---------------------------|
| Copy file                | `cp <File> <Destination>`        | `cp test1.txt Documents/` |
| Copy multiple files      | `cp ./{file1,file2} ./Documents` | Copies several at once    |
| Copy directory           | `cp -r <FolderFrom> <FolderTo>`  | `-r` = Recursive          |
| Confirm before overwrite | `cp -i file.txt ./folder1`       | Interactive copy          |
| Move file                | `mv <File> <Destination>`        | Moves or renames file     |
| Rename file              | `mv old.txt new.txt`             | Simple rename             |

---

### **Deleting Files and Directories**

| Task                      | Command            | Notes                           |
|---------------------------|--------------------|---------------------------------|
| Remove file               | `rm <FileName>`    | Deletes file                    |
| Ask before deleting       | `rm -i <FileName>` | Interactive deletion            |
| Remove directory          | `rm -r <DirName>`  | Recursive delete                |
| Remove empty directory    | `rmdir <DirName>`  | Only if empty                   |
| Remove all files          | `rm *`             | Deletes all files only          |
| Remove all (files + dirs) | `rm * -r`          | Deletes everything in directory |

---

## **6. Viewing Files**

| Command       | Description                               | Keys                                |
|---------------|-------------------------------------------|-------------------------------------|
| `cat <File>`  | View complete file                        | —                                   |
| `more <File>` | View file page by page                    | `space`: next, `p`: prev, `q`: quit |
| `head <File>` | Show first 10 lines                       | `head -n 5 file.txt` = 5 lines      |
| `tail <File>` | Show last 10 lines                        | `tail -n 5 file.txt` = 5 lines      |
| `less <File>` | Paginated viewer (faster for large files) | Scroll easily                       |
| `nano <File>` | Open text editor inside terminal          | `Ctrl+O`: Save, `Ctrl+X`: Exit      |

---

## **7. File Globbing**

> Globbing = Pattern matching for filenames

| Pattern | Example         | Description                       |
|---------|-----------------|-----------------------------------|
| `*`     | `rm *.txt`      | Matches all ending with `.txt`    |
| `?`     | `rm ?oo`        | Matches `a00`, `boo`, `coo`, etc. |
| `{}`    | `rm file{1..3}` | Removes `file1`, `file2`, `file3` |
| `[]`    | `rm file[1-3]`  | Same as above                     |

---

## **8. System Info & Utilities**

| Task                      | Command             | Description          |
|---------------------------|---------------------|----------------------|
| Show date/time            | `date`              | Displays system date |
| Show calendar             | `cal`               | Current month        |
| Show full year calendar   | `cal 1990`          | For any year         |
| Clear terminal            | `clear` or `Ctrl+L` | Clears screen        |
| Manual (help) for command | `man <Command>`     | `q` to exit manual   |
| Short info                | `whatis <Command>`  | One-line description |

---

### **Example:**

```bash
man ls
whatis ls
```

---

## **9. Key Takeaways**

* Everything in Linux is treated as a **file** (even directories, devices, sockets).
* File extensions are **optional**, not required.
* Use **flags/options** (`-a`, `-r`, `-p`, `-i`, etc.) to extend command behavior.
* Learn **manual pages (`man`)** — your built-in documentation.

---

> 🧠 **Tip:**
> Practice these commands daily inside a Linux terminal or WSL.
> Combine commands using `&&` to chain actions:
>
> ```bash
> mkdir -p Projects && cd Projects && touch notes.txt
> ```