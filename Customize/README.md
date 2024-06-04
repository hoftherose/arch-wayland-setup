# Customization
Here we will customize our setup, meaning that this is probably the part that you should follow the least as it is purely opinionated.

## Setting Grub Theme
To create a theme for your grub you must first download the theme then set the grub configuration to use that theme. Below will be an example of how to set this up using [SiriusAhu/Persona_5_Royal_Grub_Themes](https://www.gnome-look.org/p/2122684).

First download and extract the tar.gz release file:
```
wget -c https://github.com/SiriusAhu/Persona_5_Royal_Grub_Themes/releases/download/v1.0/joker.tar.gz -P /boot/grub/themes
tar -xvzf /boot/grub/themes/joker.tar.gz -C /boot/grub/themes --no-same-owner
```
