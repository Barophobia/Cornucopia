+++
title = "Installing Arch Linux"
+++

Arch linux is a sort of 'build it yourself' OS allowing you to create the environment you desire, I use this to have a low resource requirement extending the life of 'old' hardware but it can be used for more than that.

### How to use the Arch automated installer

Download the Arch Linux ISO from the website.
[https://www.archlinux.org](https://www.archlinux.org)

Boot to the ISO file

Once you have booted to the ISO you should be presented with the command line

To use the Arch automated installer type:
```
archinstall
```
The guided installer will perform the following steps:

- configure the locale;
- select the mirrors;
- partition the disks;
- format the partitions;
- enable disk encryption (optional);
- set the hostname;
- set the root password;
- install a boot loader (limited to systemd-boot for UEFI and GRUB for BIOS)

Leaving the root password blank disables the root account.

