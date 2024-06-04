# Arch Vanilla Installation

Note: Make sure you go through the preparation section before making a new installation of Arch. This guide is more based on this following [video](https://www.youtube.com/watch?v=FxeriGuJKTM) than the [arch guide](https://wiki.archlinux.org/title/Installation_guide).

[TOC]

## Live Boot
Once you live boot, click the option that says `Arch Linux install medium`. This will open a `zsh` console. By now you have done the first 4 steps in the [Guide](https://wiki.archlinux.org/title/Installation_guide). We will not be following this in order, instead it will be in my own prefered order.

## Setting up wifi
Unless you have an ethernet connection, the first step should be setting up your wireless connection. In order to do this run `iwctl` which will open a new shell. Run the following, replacing `wlan0` with your device (can be viewed with `ip addr show` on zsh shell).

```
station wlan0 scan # Scan networks
station wlan0 get-networks # List available networks
station wlan0 connect SSID_FOUND # Connect to network through SSID, password needed.
exit
```

Once you are back on zsh, you can test your connection pinging a site like google.com. `ping google.com`
