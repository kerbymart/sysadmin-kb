# Instructions

### Step 1: Expand the VHDX File in Hyper-V

#### Using Hyper-V Manager
1. Shut down the Ubuntu VM.
2. Open Hyper-V Manager and select the VM.
3. Go to Settings > Hard Drive, then click Edit.
4. Choose Expand and enter the new size.
5. Complete the wizard and boot the VM.

#### Using PowerShell
1. Execute `Resize-VHD -Path <PathToVHDX> -SizeBytes (<SizeInGB>GB)` as Administrator.

### Step 2: Extend the Filesystem Within Ubuntu

#### If Using LVM (Logical Volume Manager)
1. Verify the new disk size with `lsblk` or `sudo pvdisplay`.
2. Resize the physical volume: `sudo pvresize /dev/sdX`.
3. Extend the logical volume: `sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv`.
4. Resize the filesystem: `sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv`.

#### If Not Using LVM
1. Use `gparted` or `fdisk` to resize the partition.
2. Then, resize the filesystem with `sudo resize2fs /dev/sdX1`.