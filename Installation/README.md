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
