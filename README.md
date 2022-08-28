# SFManager

SFManager, Shima Floppy Manager is a Windows tool developed around 2004 to read and write some floppy disks used by Shima Seiki knitting machines. This tool was possible thanks to the great work done by the developers behind the now offline website: sds.utils.home.ro
This tool was developed without understanding how everything works, and mostly based on source code found on the internet. All the assumptions are based on what works or not and some testing.

## Features

- Read and Write files directly to 640KB DD floppy disks
- Read and Write 640KB DD floppy disks dump files
- Logical format floppy disks
- Works with disks formatted by the Shima Seiki TFD (Terminal Floppy Disk)
- Tested under Windows XP

## Requirements

- Floppy drive (NOT USB)
- Windows XP or older. It seems possible to make it work under newer versions of Windows.
- Custom floppy driver

Standard Windows floppy drivers cannot read floppy disks formatted with this 640KB capacity, apparently is a bit more complex than just reading bytes. To be able to read this format I found multiple options

- Use the floppy drivers that shipped with SDS One
- Use the Omniflop driver (OmniFlop (shlock.co.uk)

## About

Old, and not so old Shima Seiki machines uses a floppy disk to input pattern data. Today it seems we have some more simpler solutions, like USB to floppy converter, but back at that time, the only solution was to use a floppy disk.
The main problem was that the floppy disk was not readable in tradition pcs, because either they use a nonstandard format, or we needed a special drive. (1.2MB).
The 640KB capacity floppy disks use the RT-11 file system. There’s a lot of documentation online about how the RT-11 file system works, but I was not able to find any software to read this kind of disks, but it seems 100% compatible.

Apparently, nothing specific to Shima here, under the hood SFManager does the following:

- RT-11 file system reader/writer (implemented without knowing it was RT-11)
- Conversion between file system absolute offset to real floppy offset based on head/cylinder/etc (not sure how it works)
- Low level access to the floppy driver
