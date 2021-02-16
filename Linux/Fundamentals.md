# Fundamentals
In 1991, Linus Torvalds rewrote the UNIX software and made it available to everyone by writing the Core, the Kernel. 

## BIOS
BIOS (basic input/output system): Software that lices on the motherboard and exists as firmware
- Allows recognizing, enabling, and disabling different pieces of hardware.
- Takes an action to begin the startup process.
- BIOS is used to view and configure the hardware operation. 

BIOS is used to enable/disable integrated peripherals. Integrated peripherals are peripherals that is connected to the motherboard examples are:
- Serial or RS232 ports
- Internal disk drives
- USB port operations
- System clock

In BIOS Setup user can view/edit disk drive availability, boot order, overall system security, boot password, configure systems without external peripherals. 

BIOS launches the operating system. Operating system need to load modules into kernel. `modprobe` is a command that load modules into the kernel. `insmod` only load the module which has been requested. `ls mod` to show the modules loaded for a particular kernel. 

### Hardware embedded devices
Hardware embedded devices are small computing devices that are never intended to be used as general computing devices. Raspberry Pi is an example. Raspberry Pi is run as a headless client. 

### Determine Hardware Resources
There are several utlities that show what is in the computer such as `ls utility` and `lsusb`. These are the steps to determine hardware resources:

1. Open the shell by using `Ctrl`+`Alt`+`T` 
2. Investigate USB devices using `lsusb`
3. Investigate PCI bus using `lspci`
4. Use `sudo` super user mode to run command `usbview` which requires certain privileges

### Virtual Filesystem
Linux uses everything is a file approach and present data as a collection of files. `Sysfs` is a virtual filesystem mounted at `/sys`. Use `/sys` and `/dev` to view devices.

Udev virtual filesystem creates a dummy device file to represent hotplug devices and it is mounted at `/dev`. 

Virtual filesystem `ls /proc` lists processes, hardware, and directory. 

### Hardware Abstraction Layer Daemon
A user space program the provides other user space programs info about hardware and it is a messaging API. HALD uses Desktop Bus, a message passing bus which allow user space programs to interact indirectly. 

## Boot Process
Boot loader determine what the next steps should be taken. **LILO** and **GRUB** are most common boot loader. 

**GRUB** configuration file can be found in `/boot/grub` and it can be displayed as either `grub.conf` or `grub.cfg`. Do not change these files, to edit **GRUB** files access `/etc/default/grub` and edit. Use `run update-grub` to update the **GRUB** configuration files. The reason for this methodology is because **GRUB** takes the configuration provided and pulls together all dependencies and create a **GRUB** configuration. **GRUB** is installed using `grub-install/dev/had`. 

Hold `Shift` key to during boot to show **GRUB** menu, in this editor it will show images available for boot. `initrd` show initial RAM disk. 

**GRUB** boot loader record entries when kernel is updates. It is like git version control. Boot loader lives in Master Boot Record. MBR is a place on primary partition on the disk drive that can be easily located and the primary action for the BIOS.

Kernel initializes the environment and runs `/sbin/init`. `/sbin/init` is a default program that launch. End of the boot process is indicated when kernel initialized the environment and ran the initial program, `sysvinit`. `sysvinit` is stored `sbin/init`. Run scripts are stored in `/etc/rc` or `/etc/rc.d`.

`systemd`, Linux system daemon defines the dependencies among startup procedures. It also support parallelism during the boot process.
- `journalId` to display boot messages

`upstart` used in Ubuntu that handles starting and stopping of programs asynchronously. 

Boot events are stored in `/var/log/messages`. `dmesg` command will dump event messages. 

## Runlevel
**Runlevel** determines which set of services should be active. 

| Runlevel | Description |
| --- | --- |
| 0 | Shut down the system |
| 1, s, S | Single-user mode used in system maintenance |
| 2 | Multi-user with GUI running |
| 3 | Multi-user in console mode |
| 4 | Normally undefined |
| 5 | Multi-user with GUI running |
| 6 | Reboot the system |