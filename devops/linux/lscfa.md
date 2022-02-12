# LCFA Notes

## CH 2: Linux Philosophy and Concepts

**Objectives**
* Discuss the history/ philosophy of Linux
* Describe the Linux community
* Define the common terms associated with Linux
* Discuss the components of a Linux distro

**Terms/Concepts**
* UNIX
* root
* linux
  *  fully multitasking (parallel threads), multiuser OS, with built-in networking and service processes known as daemons in the Unix world
* linux patches/ release system
* GNU license
* kernel
* distribution
* boot loader
  * grub
* service
* filesystem
* X window system
* desktop environment
* command line

## Ch 3: Linux basics and startup

**Objectives**
* Identify Linux filesystems
* Identify the differences between partiitons and filesystems
* Describe the boot process
* Install Linux on a computer

**Notes**

* Linux boot process
  * Power ON, BIOS, Master Boot Record MBR (first sector of the hard drive), Boot Loader (GRUB), Kernel (Linux OS) Initial RAM disk (initramfs image), /sbin/init (parent process), command shell using getty, X Window system (GUI)
  * BIOS
    * Basic Input/Output system
    * Inits hardware (screen and keyboard) and tests main memory (POST - power on self test)
    * stored on ROM chip on motherboard
  * Boot loader
    * Stored on HDD in
      * EFI partition (UEFI)
    * CMOS Values gives info on date, time, etc
  * Systemd vs upstart
  * PArtition and filesystem
  * File SYstem hierachy
  * Questions to think about when choosing distro
    * Main function of system (Server or desktop)
    * Type of pacakges (web, word proecessing, etc)
    * memory
    * package updates
    * LTS
    * Kernel customization
    * Archeticture
