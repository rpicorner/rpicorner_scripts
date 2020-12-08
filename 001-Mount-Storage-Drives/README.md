# How to mount storage drives to the Raspberry Pi

Note: In this tutorial everything is made via command line, so it should work on Raspberry Pi OS with and without desktop encironment.

Mounting drives is an important skill to have when it comes to working with hard drives and file structures in Linux. Once you have a general understanding, it becomes a pretty easy task.

## Recommended

- [Raspberry PI](https://bit.ly/36T6lqL)
- [Micro SD Card](https://amzn.to/2JBK4Fd) 4GB+.
- [External Hard Drive](https://amzn.to/37JL1mS)

## Optional

- [Raspberry PI Case w/ Fan](https://amzn.to/2VSi16N) For cooling the board to prevent over temperatures and performance throttle

Note: The USB ports on the Raspberry Pi might not be enough to power an external drive so you might need to invest in a [powered USB hub](https://amzn.to/3ovA27h).

# Before start

To follow this tutorial you just need to have access to a terminal on the Raspberry Pi, it can be directly plug a keyboard, mouse and monitor or just access it remotly via SSH.
This tutorial was developed and tested on the Raspberry PI OS, but any linux distribution that runs on the Raspberry Pi should work.

# 

Each hard drive, USB disk has a label on Linux. Before any hard drive is accessible, we must find out the device label. This is easy, but very important. This is because external hard drives in Linux (unlike Windows and Mac) do not automatically start up so that users can access files. To find out the label of an external hard drive, open up a terminal, and use the following command.

```
sudo fdisk -l
```

Most peripherals (ex. hard drives, keyboards, CD/DVD drives) detected by linux have a reference to the special directory **/dev**. However, the system cannot access the devices directly
without specifying the way to interact with them. In case of storage devices (hard disks, Pen USB) this devices need to be mounted to be possible to access the files.

The naming have the following meaning:
- **/dev** – Special directory
- **sd** - Naming associated with storage devices
- **a** - Ordering of the connected devices. **a** is used for first **b** for second, etc.
- **1** - Partition of the disk. In this case the hard drive only have one partition.

# Temporary mount

It is possible to mount any hard drive temporarily, to any folder. To start off, we are going to create the mount folder in the home directory.

```
mkdir -p ~/extern-drive
```

With the folder created, we can mount the hard drive. In this example, we are going to mount **/dev/sda1** onto our newly created folder.

```
sudo mount /dev/sda1 ~/extern-drive
```

And there you go, now everytime you perform any operation into the folder **~/extern-drive** the changes will be saved in the external hard drive. When Linux reboots, it will disconnect.

# Permanent mount

Permanently mounting an external hard drive requires modifying the file system tab. The file system tab lets Linux know where every hard drive partition needs to go. To make external hard drives permanently mountable at boot, do the following:

First, create the folder where the hard drive will load to. This folder will be this hard drive’s home, so DO NOT delete it. If you do, Linux will fail to boot and everything will break.

```
mkdir -p ~/extern-drive
```

Then edit the file **/etc/fstab** and add the folowing line:

```
/dev/sda1 /home/<user>/share auto noatime 0 0
```

Note: In the fstab file you need to use absolute paths.

Now you can restart your Raspberry Pi and see if the external hard drive was mounted properly.

And there you go, now everytime you perform any operation into the folder **~/extern-drive** the changes will be saved in the external hard drive.

