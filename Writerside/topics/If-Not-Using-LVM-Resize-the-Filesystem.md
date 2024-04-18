# Resize the Filesystem

After adjusting the partition, the next step is to resize the filesystem. Assuming an `ext4` filesystem, use `resize2fs`.

1. **Use the `resize2fs` command**: Ensure you replace `/dev/sda1` with the identifier for your resized partition.
   ```bash
   sudo resize2fs /dev/sda1
   ```

#### Example Command and Output for `resize2fs`
- **Command**:
  ```bash
  sudo resize2fs /dev/sda1
  ```
- **Example Output**:
  ```
  resize2fs 1.45.5 (07-Jan-2020)
  Resizing the filesystem on /dev/sda1 to 31457280 (4k) blocks.
  The filesystem on /dev/sda1 is now 31457280 blocks long.
  ```

This output confirms the filesystem has been resized to fill the partition.

### Verifying the Changes

After resizing the filesystem, verify that the additional space is recognized and available.

- **Command**:
  ```bash
  df -h
  ```
- **Look for** your partition (e.g., `/dev/sda1`) in the output. The `Size` column should reflect the new, larger size of the partition and filesystem.

This example illustrates the process for systems not using LVM. It's crucial to back up data before proceeding with these steps, as resizing partitions and filesystems involves operations that could potentially lead to data loss if not done correctly.