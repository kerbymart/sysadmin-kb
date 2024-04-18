# Identifying LVM Usage in Linux Systems for Disk Resizing

Determining whether your Linux or Ubuntu system is using Logical Volume Manager (LVM) can be crucial before proceeding with disk resizing tasks. Knowing if you're working within an LVM or a traditional partition setup helps you choose the correct method for expanding your disk space. Here are a few straightforward methods to check if your system is using LVM:

### Method 1: Use `lsblk`

The `lsblk` command lists information about all available or the specified block devices. It shows a tree-like view of the relationship between devices, partitions, and logical volumes.

1. **Command**:
   ```bash
   lsblk
   ```

2. **What to look for**:
    - If you see entries under `TYPE` as `lvm`, your system is using LVM.
    - The presence of `TYPE` as `part` without any `lvm` indicates a traditional partitioning scheme.

### Method 2: Check for Volume Groups with `vgs` or `vgdisplay`

LVM organizes physical volumes into volume groups (VGs). If there are active VGs, your system is using LVM.

1. **Using `vgs`**:
   ```bash
   vgs
   ```
    - If this command lists any volume groups, then LVM is in use.

2. **Using `vgdisplay`**:
   ```bash
   vgdisplay
   ```
    - This command provides detailed information about volume groups. If it outputs details about a volume group, LVM is being used.

### Method 3: Examine the `/etc/fstab` File

The file `/etc/fstab` contains information about where and how the partitions, including logical volumes, should be mounted on boot.

1. **Command**:
   ```bash
   cat /etc/fstab
   ```

2. **What to look for**:
    - Paths that include `/dev/mapper` or `/dev/<VG-Name>` are indicative of LVM usage. For example, `/dev/mapper/ubuntu--vg-ubuntu--lv` or `/dev/ubuntu-vg/ubuntu-lv` suggest an LVM setup.
    - Traditional partitions might be listed as `/dev/sda1`, `/dev/sda2`, etc., indicating non-LVM partitions.

### Method 4: Use the `df` Command

The `df` command shows the file system disk space usage. It can give clues about whether LVM is used based on the filesystem paths.

1. **Command**:
   ```bash
   df -h
   ```

2. **What to look for**:
    - Filesystem paths that begin with `/dev/mapper/` or include `-–vg-` (indicating volume groups) are typically managed by LVM.

These methods should help you determine whether your Ubuntu system is using LVM. Knowing this will guide you in choosing the correct procedure for expanding your filesystem, as outlined in the instructions provided.