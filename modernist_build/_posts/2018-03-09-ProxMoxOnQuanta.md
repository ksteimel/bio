---
title: Installing Proxmox on a Quanta Windmill v1 
layout: default
category: hpc
---

Every time I tried to install proxmox on a quanta opencompute windmill v1 with legacy bios, it failed. 
Typically there were errors after the install process with sudden freezing. 

The install went perfectly fine in my case but there were issues upon reboot. Twice, the countdown for the default option at the proxmox boot screen froze. Once, I selected proxmox as my boot option and a bizarre error cropped up during boot(I'm refering to the modified grub for proxmox where you have the option to do memory tests and other debian things). 


By switching to UEFI, I was able to install proxmox like normal. 

I'm leaving this up here in case someone else has similar troubles with a quanta windmill.

In addition, I had to install using a cd-drive from a spare computer connected to SATA2 as the proxmox install continually failed to recognize the cdrom when booting from a usb. 
