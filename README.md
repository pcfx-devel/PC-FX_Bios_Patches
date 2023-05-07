# PC-FX_Bios_Patches

Useful patches for the PC-FX BIOS

## Overview

First, it is important to be aware that the PC-FX BIOS did NOT
remain consistent across the lifetime of the system; there are
at least two versions of the BIOS.

The more common version of the BIOS was found on most PC-FX consoles
built before late 1995, and is the likely version which people use
on emulators.

As such, you will need to check in the list below whether the patch
is intended for a specifc BIOS version.

## List of Patches

| Filename | Compatibility | Description |
|----------|---------------|-------------|
| fxbios_shortintro.ips | both | Disables startup splash screen and reduces boot time in half (for developers) |
| fxbios_english.ips | both | Partial translation - main menu only (roughly 20% of the full BIOS) |
| fxbios_autolaunch.ips | both | launches the CD right after the intro |

## Links for More Information

[Short Introduction Patch Technical Details](Short_intro_patch.md)
