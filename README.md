ArchLinux ARM package for Allstar (https://allstarlink.org) on the ARM6 or ARM7 processor

Need to load packages with pacman e.g pacman -S svn wget libusb-compat

Due to upgrades to pacman (4.2) you need to load using "pacman -U --force <package name> at the moment.

Must load the "dahdi-linux-allstar" package (from this repository) beforehand as it is a dependency for this package and this must be created using the makepkg command

Asterisk should automatically start after the package install (and on reboot), this can be checked by running "asterisk -r

Anthony, VK2ACP
