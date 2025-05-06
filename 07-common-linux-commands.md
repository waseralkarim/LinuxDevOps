## File & Directory Management

| Command | Description |
| --- | --- |
| `ls` | List files in current directory |
| `ls -l` | Long listing with details |
| `cd <dir>` | Change directory |
| `pwd` | Show current path |
| `mkdir <dir>` | Create new directory |
| `rm <file>` | Delete file |
| `rm -r <dir>` | Delete directory recursively |
| `cp <src> <dest>` | Copy file or directory |
| `mv <src> <dest>` | Move or rename file/directory |
| `touch <file>` | Create empty file |
| `tree` | Visual directory structure (recursive) |
| `find <dir> -name <pattern>` | Search for files/directories |
| `du -sh <dir>` | Show total directory size |

---

## File Viewing & Editing

| Command | Description |
| --- | --- |
| `cat <file>` | Show file content |
| `less <file>` | Scroll through file |
| `head <file>` | Show first 10 lines |
| `tail <file>` | Show last 10 lines |
| `tail -f <file>` | Live monitor file (e.g., logs) |
| `nano <file>` | Edit file (easy CLI editor) |
| `vim <file>` | Edit file (advanced CLI editor) |
| `grep '<pattern>' <file>` | Search pattern in file |

---

## User & Permission

| Command | Description |
| --- | --- |
| `whoami` | Show current user |
| `sudo <command>` | Run command as superuser |
| `chmod +x <file>` | Make file executable |
| `chmod +w <file>` | Make file writable |
| `chmod +r <file>` | Make file read-only |
| `chown user:group <file>` | Change file ownership |
| `id` | Show user and group info |
| `adduser <username>` | Add a new user |
| `passwd <username>` | Change user password |

---

## View Current Time & Date

| Command | Description |
| --- | --- |
| `date` | Show current system date/time |
| `timedatectl` | Show detailed time settings |
| `hwclock` | Show hardware (BIOS) clock |
| `timedatectl list-timezones` | List available time zones |
| `sudo timedatectl set-timezone <Region/City>` | Set system time zone |

---

## View System Info

| Command | Description |
| --- | --- |
| `uname -a` | Display system info (kernel, OS, arch) |
| `top` | View running processes (live) |
| `htop` | Enhanced interactive process viewer |
| `df -h` | Disk space usage (human-readable) |
| `free -h` | Memory usage (RAM and swap) |
| `uptime` | Show how long the system has been running |
