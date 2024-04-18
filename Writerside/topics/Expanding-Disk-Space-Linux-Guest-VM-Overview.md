# Overview

This guide provides step-by-step instructions for expanding the disk space on Ubuntu virtual machines (VMs) that use Logical Volume Manager (LVM) on Hyper-V. This process is necessary when your VM needs more space than was initially allocated.

### Scenario
The root cause was a VM configured with a dynamically expanding VHDX file on Hyper-V, running out of space on the Ubuntu VM.

## Prerequisites
- A VM running Ubuntu on Hyper-V with LVM.
- Hyper-V Manager access for resizing VHDX.
- Administrative access to the Ubuntu system.