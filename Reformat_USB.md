Here is the USB drive reformatting guide converted to Markdown:

# Guide for Reformatting USB Drives

This guide provides instructions for reformatting USB drives on Linux and Windows platforms.

## Table of Contents

- [Linux](#linux)
  - [Identify the USB Drive](#identify-the-usb-drive)
  - [Unmount the USB Drive](#unmount-the-usb-drive)
  - [Format the USB Drive](#format-the-usb-drive)
  - [Create a File System](#create-a-file-system)
  - [Mount the USB Drive](#mount-the-usb-drive)
- [Windows diskpart](#windows-diskpart)

## Linux

### Identify the USB Drive

First, you need to identify the drive you want to reformat. You can list all the storage devices in your computer with the following command:

```bash
lsblk
```

This will give you a list of devices along with their mount points. Your USB drive will usually be something like `/dev/sdb` or `/dev/sdc`.

### Unmount the USB Drive

Before reformatting, you should unmount the drive. This can be done with the following command: 

```bash
sudo umount /dev/sdX
```

### Format the USB Drive

Now you can start the process of reformatting. You can use `fdisk` to manage the partitions on your USB drive. Use the following command to start `fdisk` for your drive:

```bash
sudo fdisk /dev/sdX
```

Once you're in the `fdisk` utility, you can use the following commands:

- `p` - Display the partition table to confirm you're working with the correct drive.
- `d` - Delete a partition. If there are multiple partitions, it will ask you which one you want to delete. Repeat this step until all partitions are deleted.  
- `n` - Create a new partition. Follow the prompts to accept the defaults.
- `t` - Change the partition type. If asked for a code, use `b` for FAT32 or `83` for Linux.
- `w` - Write changes and exit.

### Create a File System

Now that you have a new partition, you can format it with a file system. If you want a FAT32 file system, you can use the following command:

```bash
sudo mkfs.vfat /dev/sdX1 
```

Or if you want an ext4 file system, use this command instead:

```bash
sudo mkfs.ext4 /dev/sdX1
```

### Mount the USB Drive 

Now you can mount the drive again:

```bash
sudo mount /dev/sdX1 /mnt
```

Now your USB drive is reformatted and ready to use! 

> **IMPORTANT:** Be very careful when using these commands, as choosing the wrong drive can result in data loss. Always double-check the drive name (`/dev/sdX`) before running these commands.

## Windows diskpart

1. Open Windows PowerShell as an administrator.

   ```powershell
   diskpart
   ```

2. List all the connected storage devices.

   ```powershell
   list disk
   ```

3. Identify your USB drive by its size and replace X with its disk number.

   ```powershell
   select disk X
   ```

4. Delete all data and partitions on the drive.

   ```powershell
   clean
   ```

5. Create a new primary partition. 

   ```powershell
   create partition primary
   ```

6. Select the newly created partition.

   ```powershell
   select partition 1
   ```

7. Format the partition to FAT32 or NTFS (replace "fs=fat32" with "fs=ntfs" if you want NTFS file system).

   ```powershell
   format fs=fat32 quick
   ```

8. Assign a drive letter to the partition (replace "Y" with your desired drive letter).

   ```powershell
   assign letter=Y  
   ```

9. Exit DiskPart.

   ```powershell
   exit
   ```

> This guide will completely erase all the data on your USB drive and prepare it for fresh use. Be sure to replace X with your disk number and Y with the desired letter for your drive.

Let me know if any changes need to be made!
