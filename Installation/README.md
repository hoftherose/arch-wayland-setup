# Arch Vanilla Installation

Note: Make sure you go through the preparation section before making a new installation of Arch. This guide is based on the [arch guide](https://wiki.archlinux.org/title/Installation_guide).

[TOC]

## Live Boot
Once you live boot, click the option that says `Arch Linux install medium`. This will open a `zsh` console. By now you have done the first 4 steps in the [Guide](https://wiki.archlinux.org/title/Installation_guide). We will not be following this in order, instead it will be in my own prefered order.

## Pre-partition
### Safety first
This step is to prepare for the partitioning. Make sure you have backed up or otherwise saved everything needed on the partitions, as this will be your last chance.

### Setting up wifi
Unless you have an ethernet connection, the first step should be setting up your wireless connection. In order to do this run `iwctl` which will open a new shell. Run the following, replacing `wlan0` with your device (can be viewed with `ip addr show` on zsh shell).

```
station wlan0 scan # Scan networks
station wlan0 get-networks # List available networks
station wlan0 connect SSID_FOUND # Connect to network through SSID, password needed.
exit
```

Once you are back on zsh, you can test your connection pinging a site like google.com. `ping google.com`

### Setup keyboard

Section 1.6 of the [guide](https://wiki.archlinux.org/title/Installation_guide) explains this quickly.

Although this will only set the installation keyboard settings, you should also be able to do the same process once you finished the installation to change keyboard on arch itself. But by that time you will have more friendly GUI options.

## Partition
You can list your current storage devices with `fdisk -l`. From now on we will refer to the storage device you will use as /dev/sda1, but you will need to change the commands to use your own. In order to open the fdisk console, run `fdisk /dev/sda1`. Below are various commands that will be needed

```
m # Opens help menu/manual
g # Creates new empty GPT partition table. (UEFI system)
o # Creates new empty DOS partition table. (Non-UEFI system)
n # Add a new partition
d # Deletes a partition
t # Changes a partition type
a # Toggles boot flag (in the case of Non-UEFI system)
w # Writes changes into disk
q # Exits without writing changes
```

The steps we need to take will vary on how we are trying to install arch, if we are trying to allow for dual boot it will be significantly more complicated, while clearing out a full disk and installing on the full disk is the simpler approach. If something is not clear, it is ALWAYS safer to double check your system or the documentation. Here is a [video](https://www.youtube.com/watch?v=LPYfoFSXB9A) which goes deep into the subject of fdisk.

### Using entire disk for installation.
Since we are using the entire disk we are going to use /dev/sda without a number associated. `fdisk /dev/sda`. 

#### Creating partition table

```
g # UEFI system, needs boot partititon
o # Non-UEFI system, does not need boot partition, instead uses boot flag
```

#### Creating boot

```
n # Create new partition. Don't create boot partition for non-UEFI.
(default) # Partition number as next number, remember which is which
First sector: (Default) # Since we are using the entire disk, leave default
Last sector: +2G # 2G for the boot, half if storage is limited.
t # We need to change the partition type to ensure that this is swap
L # Lists all partition types, you should look for "EFI system"
1 # Could be different, ensure number is correct
```

#### Creating swap

```
n # Create new partition. If non-UEFI choose primary partition
(default) # Partition number as next number, remember which is which
First sector: (Default) # Since we are using the entire disk, leave default
Last sector: +16G # 16G for the Swap, can be less (1G) if storage is issue.
t # We need to change the partition type to ensure that this is swap
L # Lists all partition types, you should look for "linux swap"
19 # Could be different, ensure number is correct
```

#### Creating root parititon
```
n # Create new partition. If non-UEFI choose primary partition
(default) # Partition number as next number, remember which is which
First sector: (Default) # Will default to right after partition 1.
Last sector: (Default) # Will consume rest of disk.
# Should be left as linux partition type
```

If using Non-UEFI set boot flag with the following

```
a # If using non-UEFI toggle this partitions boot flag with
```

#### Creating home parititon (Optional)
You can separate root and home into two different partitions, this although has it's advantages, I tend to format them both together anyways. Documentation about more partition schemas can be found [here](https://wiki.archlinux.org/title/Partitioning#Partition_scheme)

#### Confirm partition table
Once you are finished, you can use `p` to print the partition table and review your changes before writing them to disk. Once you finished confirming use `w` to write. Once again, if you want to quit without writing, leave using the `q` command.

> NOTE: DO NOT FORGET what partition is associated with which sub-disk. It will be used later. You can always reference by size using `fdisk -l`.

## Post partitioning
Once you have partitioned, there are a few commands we need to run to properly format our partitions.

### Format Boot
Do NOT format the boot if it already existed, in this case we assume it was just made in the previous steps, therefore we would want to run the following on the boot 

```
mkfs.fat -F 32 /dev/sda1
```

### Format Swap
Run the following commands so arch knows which partition is the swap partition. Make sure to correct if the partition here is not the same as yours.

```
mkswap /dev/sda2
```

### Format Root and Home
Root and home (or any other linux partition) can be formated in the same way, with the below command. If warning message occurs proceed since we, again, are formating the entire disk.

```
mkfs.ext4 /dev/sda3
```

### Mount partitions
Run the following commands when appropriate.

```
mount --mkdir /dev/sda3 /mnt # Mount Root partition to /mnt
mount --mkdir /dev/sda1 /mnt/boot # Mount EFI partition to /mnt/boot
swapon /dev/sda2 # set swap partition
```

## Install firmware and linux kernel into mount
Once mounted, you need to install the kernel into the partitions. This can be done with the following script. The second line is for setting the environment to the new partitions root.

```
pacstrap -K /mnt base linux linux-firmware
arch-chroot /mnt
```

## Grub Setup
Now that your are in the partition environment, we need to install a few things that will be used later. The first command will update pacman and refresh keys while the second installs tooling that will be needed soon.

```
pacman -Syu && pacman-key --refresh-keys
sudo pacman -S grub neovim efibootmgr
```

If there are issues with the keys, reset keys by following the [documentation](https://wiki.archlinux.org/title/Pacman/Package_signing#Resetting_all_the_keys).

Otherwise run the following to install the path on grub for bootloading. Everything should be found in /boot/grub.

```
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
```

## Final Configuration
These steps should be taken and are simple to follow from the [guide](https://wiki.archlinux.org/title/Installation_guide). This will be steps 3 and 4.
