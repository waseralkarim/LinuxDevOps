# Package Management Distribution

Package Management system allows us to simplify the process of installation, upgrading, and removal of software packages.

We know that in windows we can install software by double clicking the .exe file but in Linux we have to install software via packages.  

**Linux Package:**

A **Linux package** is a compressed file that contains software, libraries, and necessary configurations required for installation on a Linux system.

**Types of Linux Packages:**

- **Debian-based (.deb)** – Used in Ubuntu, Debian. It is managed by `apt/dpkg` (Advanced Package Tool).
- **Red Hat-based (.rpm)** – Used in CentOS, Fedora. It is managed by `yum/dnf/rpm` (Yellowdog Updater Modified).
- **Arch-based (.pkg.tar.zst)** – Used in Arch Linux and managed by `pacman`.

### **Package Management Commands:**

**Install a package:**
    1. Debian:
       ```
       sudo apt install package_name
       ```
    2. Red Hat:
       ```
       sudo dnf install package_name
       ```
    3. Arch:
       ```
       sudo pacman -S package_name
       ```
**Remove a package:**
    1. Debian:
       ```
       sudo apt remove package_name
       ```
    2. Red Hat:
       ```
       sudo dnf remove package_name
       ```
    3. Arch:
       ```
       sudo pacman -R package_name
       ```
**Update all packages:**
    1. Debian:
       ```
       sudo apt update && sudo apt upgrade
       ```
    2. Red Hat:
       ```
       sudo dnf update
       ```
    3. Arch:
       ```
       sudo pacman -Syu
       ```

# Difference between APT and APT GET

In Debian based system we have both apt and apt get package management tool is available. 

**APT GET:** For many years it was a standard tool for package management. Unfortunately, it has some limitations. For example, it lacks built-in progress indicators and parallel downloading capabilities.

**APT:** Apt is now the most used package tool for Debian based systems. It is built upon the apt-get functionalities but more refined and includes more functionality such as built-in progress indicators and parallel downloading capabilities.

# Difference between APT and **DPKG**

**DPKG:**

`dpkg` is the low-level tool used for installing, removing, and managing `.deb` packages on Debian-based systems. However, it has some limitations. For example, it does **not** automatically handle dependencies or fetch packages from online repositories.

**APT:**

`apt` is the most used package management tool for Debian-based systems. It is built on top of `dpkg` but offers more advanced features such as automatic dependency resolution, access to online repositories, built-in progress indicators, and parallel downloading capabilities.
