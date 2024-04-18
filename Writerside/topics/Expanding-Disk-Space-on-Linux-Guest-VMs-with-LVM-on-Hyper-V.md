# Expanding Disk Space on Linux Guest VMs with LVM on Hyper-V

This guide provides comprehensive instructions for expanding the disk space on Linux virtual machines (VMs) that use Logical Volume Manager (LVM) on Hyper-V. The process involves expanding the VHDX file in Hyper-V, resizing the physical volume, extending the logical volume, and finally resizing the filesystem within the Ubuntu system. This procedure is essential when your VM requires more storage than initially allocated. The guide assumes that you have administrative access to the Ubuntu system and Hyper-V Manager for resizing the VHDX file. Always remember to back up your data before performing these operations to prevent data loss.