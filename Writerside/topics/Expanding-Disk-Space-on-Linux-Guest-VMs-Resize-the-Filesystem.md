# Resize the Filesystem

Once you have successfully extended the logical volume, the filesystem must be resized to utilize the newly allocated space. For Linux systems using an `ext4` filesystem, the `resize2fs` command is used.

1. **Identify the Filesystem**: Ensure you know the filesystem you intend to resize. For example, the filesystem to be resized is located on the logical volume `/dev/mapper/ubuntu--vg-ubuntu--lv`.

2. **Use the `resize2fs` command**: The `resize2fs` command is used to resize the `ext4` filesystems. It can be used without unmounting the filesystem if it is being enlarged.

Example command:
```bash
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

This command will resize the filesystem on the logical volume `/dev/mapper/ubuntu--vg-ubuntu--lv` to fill the entire logical volume, utilizing all available space.

Example output:
```
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/ubuntu--vg-ubuntu--lv is mounted on /; on-line resizing required
old_desc_blocks = 4, new_desc_blocks = 8
The filesystem on /dev/mapper/ubuntu--vg-ubuntu--lv is now 16000000 (4k) blocks long.
```

**What to look for**: The output will indicate that the resizing operation is in progress and will confirm once the filesystem is resized. It details the new size of the filesystem in blocks.

### Verify the Changes

After resizing the filesystem, it's a good practice to verify that the system recognizes the new size and that it is available for use.

Example command to check the new filesystem size:
```bash
df -h
```

Look for the mount point `/` (or wherever your logical volume is mounted) in the output. The available space should reflect the increased size of your filesystem.

Example output snippet:
```
Filesystem                              Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv        59G   11G   45G  20% /
```

**What to look for**: The `Size` column should show the new size of your filesystem, confirming that the resizing operation was successful and the system is now utilizing the additional space.

By following these steps, you have completed the process of expanding your VHDX file, resizing the physical volume, extending the logical volume, and finally resizing the filesystem within Ubuntu on your Hyper-V virtual machine. This expanded space provides additional capacity for applications, data, and system updates.