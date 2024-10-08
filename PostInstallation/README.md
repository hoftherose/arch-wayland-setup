# Setup your computer

Congratulations, you offically have a fully fledged arch installation. The problem is arch doesn't come with much, so now we are going to setup our environment so that we can work productively in the future.

General recommendations for setting up your system once installed. Based off of [arch guide](https://wiki.archlinux.org/title/General_recommendations).

## Getting internet (again)

Connect to the internet using nmcli (assuming you installed networkmanager). If not simply reboot and mount from the live-usb and install anything that you may have been missing. Follow the [guide](https://wiki.archlinux.org/title/NetworkManager#Usage) to know how to use nmcli to connect to the internet.

## Creating a User
To create a new user simply run `useradd -m -G wheel USER_NAME` to create user, and `passwd USER_NAME` to set password. The wheel group should give you access to the sudo command. The `-m` flag will create a home directory for this user. You can also use the `-s` flag to add which shell you want to use for that user, by default it uses bash.

If you are not able to use sudo commands, edit /etc/sudoers.d to allow group wheel to execute any command. Follow the [guide](https://wiki.archlinux.org/title/Users_and_groups#User_management) to see best practices on creating users.

## Grub Config
Although most of the config is going to be aesthetic, this part will only walk you through the fuctional configuration for the grub.

```
GRUB_CMDLINE_LINUX_DEFAULT="nvidia_drm.modeset=1" # This for nvidia systems, if value already has parameters, simply append to end.
```

## Pacman Config
There are multiple configuration settings in pacman that aren't by default which we should set. The following are examples but feel free to add more.

```
Colors # Adds color to pacman output for easier reading.
VerbosePkgLists # Cleaner pkg listing on updates.``
ParallelDownloads = 5 # Allows updates to go faster.
```

### Yay install
Although for the most part you can go through this setup without the AUR, it's still a good idea to have yay in case you need some package not supported. Simply make sure that the package is safe or review the package itself.

```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
