# RonR-RaspberryPi-image-utils

**NB** scruss is *not* the author or maintainer of thse files. No — and I mean **no** — issues will be accepted on this repo. Take it up in the [Image File Utilities](https://www.raspberrypi.org/forums/viewtopic.php?t=247568#p1511694) thread.

Tools to create a backup of a running Raspbian system to an SD card image file.

This is a copy of the files that [Raspberry Pi Forums](https://www.raspberrypi.org/forums/index.php) user [RonR](https://www.raspberrypi.org/forums/memberlist.php?mode=viewprofile&u=186692) posted to the topic [Image File Utilities](https://www.raspberrypi.org/forums/viewtopic.php?t=247568#p1511694) on 2019-08-01. File attachments to this forum don't seem to be persistent, so this repo was created to ensure a working snapshot is always available.

Copies of the original post/attachment are also available on the [Internet Archive](https://archive.org/):

* article: https://web.archive.org/web/20190824163430/https://www.raspberrypi.org/forums/viewtopic.php?t=247568

* attachment: https://web.archive.org/web/20190824162104/https://www.raspberrypi.org/forums/download/file.php?id=31366&sid=107ba04af18e19ad587c5bcf8ebacd38

**NB from repo creator**: This is not my code. I don't use it, but I saw that others do and were being frustrated by the forum download links expiring. I won't be responding to issues posted here.

Original README converted to markdown follows:

---------------------------------------------------------------------

## image-backup:

`image-backup` creates a backup of a running Raspbian system to a standard 'raw' image file that can be written to an SD card or a USB device card with Etcher, imageUSB, etc. It will also perform incremental updates to an existing backup image file.

Running image-backup with no parameters will create a full backup. To create the smallest possible image, specify an Image ROOT filesystem size of 0 to determine the minimum allowed size. If you plan to incrementally update the image file, specify a considerably larger size to allow for additional growth.

Running image-backup with a parameter of an existing image filename will incrementally update that image file.


## image-check:

`image-check` will check the integrity of a standard 'raw' image file.  Usage is:

    image-check imagefile [W95|Linux]

where *W95* checks the BOOT partition and *Linux* checks the ROOT partition.  If neither is specified, *Linux* is assumed.


## image-compare:

`image-compare` compares a running Raspbian system to an existing standard 'raw' image file and displays the incremental changes that image-backup would perform if run.  Usage is:

    image-compare [imagefile]


## image-mount:

`image-mount` mounts a standard 'raw' image file to allow it to be read or written as if it were a device.  Usage is:

    image-mount imagefile mountpoint [W95|Linux]

where *W95* mounts the BOOT partition and *Linux* mounts the ROOT partition.  If neither is specified, *Linux* is assumed.


## image-set-ptuuid:

`image-set-ptuuid` sets the Partition Table UUID value of a standard 'raw' image file.  Usage is:

    image-set-ptuuid imagefile ptuuid

where *ptuuid* is 8 hex digits


## image-shrink:

`image-shrink` shrinks a standard 'raw' image file to its smallest possible size (plus an optional additional amount of free space).  Usage is:

    image-shrink imagefile [Additional MB]

where *Additional MB* is an additional amount of free space to be added.
