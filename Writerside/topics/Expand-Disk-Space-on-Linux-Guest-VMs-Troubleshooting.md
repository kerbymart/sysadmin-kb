# Troubleshooting

- **Filesystem Not Expanding:** Ensure that `pvresize` reflects the new size. If not, recheck the VHDX expansion steps.
- **Data Backup:** Always back up important data before performing disk operations.
- **Filesystem Types:** This guide assumes `ext4`. Adjustments may be needed for other filesystem types.

## Verification

Run `df -h` to check the new disk space allocation. The `Avail` column should reflect the increased space.

## Experience Tips

- **Monitoring Disk Usage:** Regularly monitor disk space to avoid running out unexpectedly.
- **LVM Flexibility:** LVM allows for easier disk expansion and management, as demonstrated.
- **Backup Importance:** Always back up data before making changes to disk configurations.

## Conclusion

Expanding disk space for Ubuntu VMs on Hyper-V using LVM involves expanding the VHDX file and then extending both the physical and logical volumes, followed by resizing the filesystem. This guide outlines the necessary steps to successfully increase the available disk space within the VM.