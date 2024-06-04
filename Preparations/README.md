# Preparations

## Live-USB

> NOTE: This is also mostly covered in the [manual](https://wiki.archlinux.org/title/Installation_guide), but I've found it to be very verbose at times, and lacking explanation in others. I suppose just choose the guide that you have an easier time understanding.

Before we can install Arch we need to create a Live-Boot USB. For this we can use various tools and there are countless tutorials online. That is why for simplicity we will only show you how to do it on etcher. The following steps are a brief outline of what you will need.

-   USB
-   USB Installer
-   Live-Boot ISO

The ISO we will be downloading is a bit more than 1 GB, so any 4 GB USB will do. Like we said before we will be using etcher. We can install etcher easily though any linux package manager or from the following [link](https://www.balena.io/etcher/).

To get the Live-Boot ISO we can simply go to the [arch download page](https://archlinux.org/download/). From here scroll to the mirror that appears closest and download the latest version of the image. Make sure to also download the .sig file to check that the file you downloaded is untampered.

Arch linux won't have much out of the box, so there will be more work after installation vs other distros, but this also gives more freedom. Once you get this setup, simply run etcher and follow the instructions with your usb connected and ISO file available in your computer. Its straight forward but if for whatever reason you have trouble, you can follow this [short video](https://www.youtube.com/watch?v=kxt4uLJ53ro) from [DistroTube](https://www.youtube.com/channel/UCVls1GmFKf6WlTraIb_IaJg)

## Backup

When formating your computer or even if you want to partition it will be a good idea to create a backup for anything that will or may be erased should things go wrong. This is also why it can be better to keep a copy of important information in the cloud. Once you backed up all of your important work, make sure you also saved any configuration files you might need later. For more specifics you can look over the [Manjaro Guide](https://gitlab.com/hoftherose-config/manjaro-kde-setup/-/blob/master/Preparations/README.md?ref_type=heads&plain=0)


## Boot Order
