# Conky setup for wayland

Conky is a tool for setting up widgets on linux, it has somewhat support for wayland but from now and then shows bugs. Because of it's great integration with lua however, we will still use it for making some of our own widgets on the desktop background.

## Building for Wayland

At the time of writing this document, the latest version of conky has a bug where you can't set a widget to the desktop, meaning that it will instead open as a window (tiled) and will affect the users workflow. This bug was introduced in version 1.20.2 meaning that if we build the version 1.20.1 this will work perfectly. There is another bug on this earlier version where one of the c DLL's will not have the correct imports to properly compile.

Due to all of this, if the issue still exists on the latest version, my recommendation will be to revert back to 1.20.1 and add `import <algorithm>` to the beggining of the `x11.cc` file BEFORE building. For a guide as to how to project should be built, I simply reference the AUR official PKGBuild file.

## Allowing lua objects with cairo.

There is another bug present that doesn't allow for cairo to be used with lua, because this is used in one of my conky.conf files we will need to find a work around, but for now it's simlply an issue to keep in mind.
