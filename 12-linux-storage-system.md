# Linux Storage System

## LVM (Logical Volume Manager)

### What is LVM?

LVM is a Linux-based system for managing disk storage in a flexible way. Unlike standard disk partitions, LVM allows resizing, combining, and snapshotting storage dynamically.

### LVM Structure

Here's the 3-layer architecture:

1. **Physical Volume (PV)**: Actual disk or partition (ex: `/dev/sdb1`)
2. **Volume Group (VG)**: Pool of storage made by combining one or more PVs (ex: `vg_data`)
3. **Logical Volume (LV)**: Usable volume created from the VG (ex: `lv_home`, mounted to `/home`)

## Setup during first installation

### 1. During the installation we have to select Custom storage layout

![Lvm1](https://github.com/user-attachments/assets/f3485216-9b23-4aab-8855-f0b069899b35)

### 2. **Bootloader Partition:** It is recommended to place bootloader partition (/boot) separate from the LVM partitions. For bootloader files 2GB is enough most of the cases.

![LVM2](https://github.com/user-attachments/assets/0ebdc8dc-e798-4ae8-9520-c28948ca5529)

### 3. **LVM Partition:** 

Physical Volume part:

**In order to unlock the Create volume group (LVM) option first we need to create the partition with Leave unformatted option.**

![LVM3](https://github.com/user-attachments/assets/26daa88f-ee9d-450d-8a75-6457b6953b19)

Then the **Create volume group (LVM) will unlock. After selecting the volume group creation part starts.**

Volume Group part: We have to select the partition 3 and then create.

![LVM4](https://github.com/user-attachments/assets/3c77bf00-8489-48b9-860c-2c62762b078d)

Logical Volume part: Now from the free spaces we can slice down the storage based on our needs.

![LVM5](https://github.com/user-attachments/assets/99c3a7ff-7e1f-463d-9c21-7a28f72c6773)

After going through the partition creation process we can continue our rest of the installation process.

![LVM6](https://github.com/user-attachments/assets/f56b433b-db80-4dc7-a547-53aec15146b5)

### 4. Checking the storage after boot:

```bash
sudo lvdisplay
```
![lvdisplay](https://github.com/user-attachments/assets/5711a9ed-86b4-41c0-96c7-5476cc9cd605)

## Partitioning and Disk Structure

### MBR (Master Boot Record)

- Up to 4 primary partitions.
- Max size: 2 TB.
- Partition info in first 512 bytes.

### GPT (GUID Partition Table)

- Supports 128+ partitions.
- Max size: 9.4 ZB.
- Supports UEFI, more resilient.

---

## Adding a New Disk to an Existing LVM Setup

![storageadd](https://github.com/user-attachments/assets/43b99aa4-0626-49e7-9c7e-390105aa512b)

### Step-by-Step (Replace placeholders as needed):

```bash
# 1. View current block devices
sudo lsblk

# 2. Partition the new disk (ex: /dev/sdX)
sudo fdisk /dev/sdX

# 3. Verify partitions created
sudo fdisk -l /dev/sdX

# 4. Initialize new partition as a Physical Volume (ex: /dev/sdX1)
sudo pvcreate /dev/sdX1

# 5. Display Volume Groups
sudo vgdisplay

# 6. Display Physical Volumes
sudo pvdisplay

# 7. Extend Volume Group (ex: vg_name)
sudo vgextend vg_name /dev/sdX1

# 8. Display Logical Volumes
sudo lvdisplay

# 9. Check filesystem usage
sudo df -h

# 10. Extend Logical Volume (ex: lv_name)
sudo lvextend -l +100%FREE /dev/vg_name/lv_name

# 11. Resize filesystem (ext4)
sudo resize2fs /dev/vg_name/lv_name

# 12. Verify updated space
sudo df -h
```
![lvextend1](https://github.com/user-attachments/assets/14aa7ec4-65cf-4e8f-a6a9-2aaf07fefb11)

---

## Mounting a New Disk Without LVM

### Step-by-Step (Replace placeholders as needed):

```bash
# 1. List current block devices
sudo lsblk

# 2. Partition the disk (ex: /dev/sdX)
sudo fdisk /dev/sdX

# 3. Recheck partition layout
sudo lsblk

# 4. Format the new partition (ex: /dev/sdX1)
sudo mkfs.ext4 /dev/sdX1

# 5. Create a mount point
sudo mkdir /mnt/mount_point

# 6. Mount the partition
sudo mount /dev/sdX1 /mnt/mount_point

# 7. Verify the mount
df -h /mnt/mount_point

# 8. Get the UUID of the partition
sudo blkid /dev/sdX1
```

### Make Mount Persistent:

1. Open `/etc/fstab`:

```bash
sudo vim /etc/fstab
```

2. Add a line (replace UUID and mount point):

```bash
UUID=your-partition-uuid /mnt/mount_point ext4 defaults 0 0
```

3. Apply and verify:

```bash
sudo mount -a
df -h /mnt/mount_point
```








