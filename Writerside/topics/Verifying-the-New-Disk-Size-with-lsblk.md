# Verifying the New Disk Size with `lsblk`

1. **Use the `lsblk` command**: This command lists all block devices in a tree-like format, showing the relationship between devices and their partitions. It's a straightforward way to see if the system recognizes the new size of your expanded disk.

   Example command:
   ```bash
   lsblk
   ```

   Example output:
   ```
   NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
   sda                         8:0    0  120G  0 disk 
   ├─sda1                      8:1    0    1G  0 part /boot
   └─sda2                      8:2    0  119G  0 part 
     ├─ubuntu--vg-ubuntu--lv 253:0    0  119G  0 lvm  /
   ```

   **What to look for**: Notice the `SIZE` column for the disk (`sda` in this example) reflects the new size (120G). This indicates the system recognizes the new disk size post-expansion.

### Verifying with `sudo pvdisplay`

1. **Use the `pvdisplay` command**: This command displays detailed information about physical volumes (PV) for LVM. It's useful for verifying that LVM recognizes the new size of the expanded volume.

   Example command:
   ```bash
   sudo pvdisplay
   ```

   Example output:
   ```
   --- Physical volume ---
   PV Name               /dev/sda2
   VG Name               ubuntu-vg
   PV Size               <120.00 GiB / not usable 3.00 MiB
   Allocatable           yes (but full)
   PE Size               4.00 MiB
   Total PE              30719
   Free PE               0
   Allocated PE          30719
   PV UUID               Yr3CtT-jbfs-jD4Q-2nXd-22gh-Ujw5-eT0KXO
   ```

   **What to look for**: The `PV Size` field should show the new size of your disk (e.g., `<120.00 GiB`). This confirms that the physical volume has been successfully resized and LVM is aware of the new capacity.

### Next Steps

After confirming the disk and volume group recognize the new size, proceed with extending the logical volume and resizing the filesystem, as outlined in the guide. This process makes the additional space available for use by the operating system and applications.

Remember, these verification steps are essential for ensuring that your disk expansion process is on the right track and that the system is correctly recognizing the changes made to disk sizes.
