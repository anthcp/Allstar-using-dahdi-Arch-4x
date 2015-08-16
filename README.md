ArchLinux 4.x ARM package for Allstar (https://allstarlink.org) on the ARM6 or ARM7 processor

Need to load pre-requisite packages with pacman e.g pacman -S svn wget libusb-compat

Due to upgrades to pacman (4.2) you need to load .xz package using "pacman -U --force <package name> at the moment.

Must load the "dahdi-linux-allstar" package from the Dahdi-Arch-4.x-Linux-ARM-6and7-Allstar repository (under this same user, anthcp)  beforehand as it is a dependency for this package and this must be created first using the makepkg command

Asterisk should automatically start after the package install (and on reboot), this can be checked by running "asterisk -r

Anthony, VK2ACP
