# Software

Information about the software running on the Centauri Carbon.

State: Research

This page contains miscellaneous notes.

### OS

The Centauri Carbon runs on top of Tinalinux. The kernel has version 5.4.61. The installed version of glibc is 2.23.

### Is the Centauri Carbon running Klipper

The hotend and bed use a fairly standard Klipper setup, with bed-specific extensions (hx711s and dirctl) for the pressure sensors. The DSP (used as a Klipper MCU) runs Klipper MCU code that has been extended and modified for DSP use.

The mainboard host runs a monolithic app that exposes the web UI, camera, API, screen UI, machine configuration, and most importantly Klippy (transpiled to C++).

The version of Klipper used on the DSP is `v0.9.1-616-g28f60f7e-dirty-20220408_035823-fluiddpi`.

See the [Custom Gcode](custom-gcode.md) page for instructions on dumping the .cfg files.

!!! note
    Because Klippy is heavily modified, not everything is supported. Modifying the Klipper .cfg may lead to a bricked machine.

### Speed profiles

Speed setting | Speed multiplier
---|---
Silent|50%
Balanced|100%
Sport|130%
Ludicrous|160%

### Getting a coredump

Coredumps have their executable memory stripped, unfortunately.

They still contain useful information, especially readable strings from running programs.

1. Insert a USB drive into your PC.
1. Create a folder called `Crash` on your USB drive.
1. Copy [a corrupt .gcode file](../assets/ECC_0.4_dust%20cover%20lr_PLA0.2_2h52m.gcode) to this new `Crash` folder.
1. Eject the USB drive.
1. Insert it into the Centauri Carbon.
1. Navigate to your USB drive, then press the `Crash` folder.
    - Your Centauri Carbon will now crash.
1. After a restart, go to settings > `Export Logs`

You should now have a `coredumps.tar.gz` file containing a coredump on your USB drive.

Coredumps can be loaded in IDA, Ghidra, BinaryNinja, or any other analyser of your choice.