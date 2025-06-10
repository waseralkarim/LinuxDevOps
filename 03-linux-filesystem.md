# Linux Filesystem and Hierarchy

![linuxfilesystemhier](https://github.com/user-attachments/assets/e468e5fa-74b1-4e4d-bc44-742b7d40d036)

| Directory | Purpose |
| --- | --- |
| `/` | The root directory. All filesystem structures begin here. |
| `/bin/` | Essential user command binaries (ex: `ls`, `cp`, `mv`) needed for system operation in single-user mode. |
| `/boot/` | Contains files needed to boot the system, including the Linux kernel and bootloader configurations (like GRUB). |
| `/dev/` | Device files representing hardware (ex: `/dev/sda`, `/dev/tty`). |
| `/etc/` | Host-specific configuration files (ex: network settings, services, users). |
| `/home/` | Home directories for regular users (ex: `/home/alice`, `/home/bob`). |
| `/lib/` | Essential shared libraries and kernel modules needed by binaries in `/bin/` and `/sbin/`. |
| `/media/` | Mount points for removable media (USB drives, CDs, etc.). |
| `/mnt/` | Temporary mount points for mounting filesystems manually. |
| `/opt/` | Optional software packages and add-on application software. |
| `/root/` | Home directory for the `root` (superuser). |
| `/sbin/` | Essential system binaries (ex: `fsck`, `reboot`) used mainly for system administration. |
| `/srv/` | Data for services provided by the system (ex: web server data, FTP data). |
| `/tmp/` | Temporary files created by applications; usually cleared on reboot. |
| `/usr/` | Secondary hierarchy for read-only user data; contains most user commands, libraries, documentation, and applications. |
| `/usr/bin/` | Non-essential user binaries (the majority of user commands). |
| `/usr/lib/` | Libraries for programs located in `/usr/bin/` and `/usr/sbin/`. |
| `/usr/include/` | Header files for development. |
| `/usr/sbin/` | Non-essential system administration binaries. |
| `/var/` | Variable files—content expected to change frequently (logs, spool files, caches). |
| `/var/log/` | System log files (ex: `/var/log/syslog`, `/var/log/auth.log`). |
| `/var/cache/` | Cached data from applications. |
| `/var/spool/` | Data awaiting processing (ex: print jobs, mail queue). |
