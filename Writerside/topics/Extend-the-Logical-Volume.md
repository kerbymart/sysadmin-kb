# Extend the Logical Volume

Once you've resized the physical volume and confirmed that additional space is available in your volume group, the next step is to extend the logical volume to use this extra space. Extending the logical volume is necessary to increase the storage space available to the filesystem.

1. **Identify the Logical Volume (LV)**: Before proceeding, confirm the name of the logical volume you wish to extend. For example, the logical volume is named `/dev/mapper/ubuntu--vg-ubuntu--lv`.

2. **Use the `lvextend` command**: The `lvextend` command enlarges the size of a logical volume. By using `-l +100%FREE`, you specify that you want to extend the logical volume to use all of the remaining free space in the volume group.

Example command:
```bash
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```

In this command:
- `-l +100%FREE` tells `lvextend` to use all of the available free space in the volume group for the logical volume.
- `/dev/mapper/ubuntu--vg-ubuntu--lv` is the target logical volume to extend. This path may vary based on your LVM configuration and naming conventions.

Example output:
```
  Size of logical volume ubuntu-vg/ubuntu-lv changed from 31.00 GiB (7935 extents) to 61.00 GiB (15871 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
```

**What to look for**: The output will confirm the resizing of the logical volume and indicate the new size. Ensure the new size reflects the additional space you intended to add to the logical volume.

### Next Steps

After extending the logical volume, the final step is to resize the filesystem to make use of the enlarged logical volume. This step is crucial because it affects how much space the operating system sees as available for storage. For ext4 filesystems, this is typically done with the `resize2fs` command.

Example command for resizing the filesystem:
```bash
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

Remember, the logical volume and filesystem names may vary based on your specific LVM setup and the type of filesystem you are using. Always ensure to use the correct names for your environment.

By completing these steps, you will have successfully expanded the logical volume to utilize the newly available space, enabling the operating system to see and use this additional storage capacity.