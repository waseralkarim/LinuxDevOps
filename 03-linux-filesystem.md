# Linux Filesystem and Hierarchy

![linuxfilesystemhyr](https://github.com/user-attachments/assets/580fd97c-a2ce-4273-ba15-546d7cac280b)


| Directory | Purpose |
| --- | --- |
| `/` | The root directory. All filesystem structures begin here. |
| `/bin/` | Essential user command binaries (e.g., `ls`, `cp`, `mv`) needed for system operation in single-user mode. |
| `/boot/` | Contains files needed to boot the system, including the Linux kernel and bootloader configurations (like GRUB). |
| `/dev/` | Device files representing hardware (e.g., `/dev/sda`, `/dev/tty`). |
| `/etc/` | Host-specific configuration files (e.g., network settings, services, users). |
| `/home/` | Home directories for regular users (e.g., `/home/alice`, `/home/bob`). |
| `/lib/` | Essential shared libraries and kernel modules needed by binaries in `/bin/` and `/sbin/`. |
| `/media/` | Mount points for removable media (USB drives, CDs, etc.). |
| `/mnt/` | Temporary mount points for mounting filesystems manually. |
| `/opt/` | Optional software packages and add-on application software. |
| `/root/` | Home directory for the `root` (superuser). |
| `/sbin/` | Essential system binaries (e.g., `fsck`, `reboot`) used mainly for system administration. |
| `/srv/` | Data for services provided by the system (e.g., web server data, FTP data). |
| `/tmp/` | Temporary files created by applications; usually cleared on reboot. |
| `/usr/` | Secondary hierarchy for read-only user data; contains most user commands, libraries, documentation, and applications. |
| `/usr/bin/` | Non-essential user binaries (the majority of user commands). |
| `/usr/lib/` | Libraries for programs located in `/usr/bin/` and `/usr/sbin/`. |
| `/usr/include/` | Header files for development. |
| `/usr/sbin/` | Non-essential system administration binaries. |
| `/var/` | Variable files—content expected to change frequently (logs, spool files, caches). |
| `/var/log/` | System log files (e.g., `/var/log/syslog`, `/var/log/auth.log`). |
| `/var/cache/` | Cached data from applications. |
| `/var/spool/` | Data awaiting processing (e.g., print jobs, mail queue). |
