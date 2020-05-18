# embedded-admin-utility-fs

The aim of the third assignment is to create a design with:<br>

• separate „administrative” system (used for maintenance or as a rescue
system in real embedded systems), and the „utility” system (used for
normal operation). <br>

• the bootloader enabling the selection of the system to be started.
The „Admin” system must use initramfs compiled into kernel to allow modification
of the SD card. The „Utility” system should offer the permament storage, and
therefore it should use the root file system located in the second partition of
the emulated SD card.

The selection of the started system should be done with the GUI buttons as
described below. The given templates (Admin) and (Utility) may be used as a
starting point. Below are the detailed tasks:

1. Prepare the "administrative" Linux system similar to the „rescue” system
used in our normal lab. This system should be:
1. working in initramfs;
2. equipped with the tools necessary to manage the SD card (partition it,
format it, copy the new version of the system via a network, etc.).
2. Prepare a "utility" Linux operating system using the ext4 filesystem
located in the 2nd partition as its root file system. This system should
provide a file server controlled via WWW interface (suggested solution is
Python with certain web application framework – flask, Tornado etc..
However, you may chose another environment as well).
1. The server should serve files located in certain directory (displaying
the list of files and allowing selection of file to download).
2. The server should also allow the authenticated users to upload new
files to that directory.
3. Prepare a script for the bootloader, which allows to select which system
(the „administrative” or the „utility”) should be booted.
1. Unfortunately, the current emulation of the GUI-connected GPIO does not
correctly send the initial state of the inputs. Therefore the user must
have certain time to press the „reconnect” button in the GUI as soon as
the U-Boot starts.
2. Due to certain problems with current emulation of GPIO, the first
change of the state of the LED is ignored. Please clear all GPIOs
connected to the LEDs you are going to use, so the next operations will
work correctly.
3. After two seconds the LED 24 should signal, that the buttons will be
checked.
4. After the next second, the buttons should be read to select the system.
If the chosen button IS NOT pressed, the „utility” system should be 
loaded. If the chosen button IS pressed, the „administrative” system
should be loaded.
5. After selection of the system, the LED 24 should be switched off. The
LED 25 should be switched ON if the „utility” system was selected. The
LED 26 should be switched ON if the „administrative” system was
selected.
