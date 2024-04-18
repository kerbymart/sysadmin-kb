# Resize the Physical Volume

After expanding the VHDX in Hyper-V and ensuring that your Ubuntu system recognizes the new disk size, the next critical step is to resize the physical volume. This allows the LVM to use the additional space made available by the VHDX expansion.

1. **Identify the Physical Volume (PV)**: Before proceeding, ensure you know the identifier of the physical volume you intend to resize. In our example, the physical volume was identified as `/dev/sda3` based on the output of `sudo pvdisplay`.

2. **Use the `pvresize` command**: The `pvresize` command is used to resize a physical volume to its maximum available size (or to a size specified by the user). This step is necessary to make the additional space recognized by the LVM system.

Example command:
```bash
sudo pvresize /dev/sda3
```

In this example, `/dev/sda3` represents the physical volume that you're resizing. Replace `/dev/sda3` with the appropriate device identifier for your setup if it's different.

Example output:
```
  Physical volume "/dev/sda3" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized
```

**What to look for**: The output should indicate that the physical volume was successfully resized. There won't be detailed information about the new size in this output, so you'll need to use other commands to verify the size change.

### Verifying the Resize

After resizing the physical volume, it's a good practice to verify that the system recognizes the new size. You can do this using the `pvdisplay` command again.

Example command:
```bash
sudo pvdisplay /dev/sda3
```

Example output:
```
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               <120.00 GiB / not usable 4.00 MiB
  ...
```

**What to look for**: In the `PV Size` field, confirm that the size reflects the new, expanded size of the VHDX. In our example, the goal was to expand to 120GB, so you should see `PV Size` close to `<120.00 GiB`.

This process ensures that the physical volume within Ubuntu's LVM system is resized to utilize the full capacity of the expanded VHDX file. After this step, you can proceed with resizing the logical volume and the filesystem to make use of the newly available space.