# Resize the Partition

First, you'll adjust the partition size to use the newly available space in the VHDX. Let's use `fdisk` for this example, although `gparted` (a GUI tool) is also a popular choice.

#### Using `fdisk`

1. **Start `fdisk` on the target drive**: Replace `/dev/sda` with your actual drive identifier.
   ```bash
   sudo fdisk /dev/sda
   ```
2. **Delete the existing partition**: Note that this doesn't delete data, but you should have backups just in case.
    - Command: `d`
    - Choose the partition number (e.g., `1` for `/dev/sda1`).
3. **Create a new partition**:
    - Command: `n`
    - Choose `p` for primary and then enter the partition number (same as the deleted one).
    - Enter the first sector (use the default provided by `fdisk` to use the same starting point).
    - For the last sector, either specify the size or press Enter to use the maximum available size.
4. **Write the changes**:
    - Command: `w`

This process effectively resizes the partition to fill the expanded VHDX.

#### Example Output for `fdisk`
The specific outputs from `fdisk` will vary based on your inputs and the state of your disk. Key points include confirmation messages for deleting and creating partitions and a final success message when writing the changes.