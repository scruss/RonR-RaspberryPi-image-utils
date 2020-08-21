image-backup:

Usage: image-backup [options] [pathto/imagefile for incremental backup]
-h,--help       This usage description
-i,--initial    pathto/filename of image file [,inital size MB [,added space for incremental MB]]
-n,--noexpand   Do not expand filesystem on first run after restore
-o,--options    Additional rsync options (comma separated)
-x,--extract    Extract image from NOOBS (force BOOT partition to -01 / ROOT partition to -02)"

image-backup creates a backup of a running Raspbian system to a standard 'raw' image file that can be written to an SD card or a USB device with Etcher, imageUSB, etc. It will also perform incremental updates to an existing backup image file.

Running image-backup with no incremental backup file parameter will create an initial/full backup. If no -i/--initial option is included, image-backup will interactively prompt for an "Initial image file ROOT filesystem size (MB)", which can be any size as long as (1) it's large enough to hold the data contained on the device being backed up and (2) that amount of space is available on the destination device.  image-backup will also prompt for an "Added space for incremental updates after shrinking (MB)" which will be added to the image file size after the full backup completes and the image file has been shrunk to the smallest size possible.  The resulting image file will auto-expand the first time it's executed unless the -n/--noexpand option is included.

Running image-backup with a parameter of an existing image filename will incrementally update that image file.  The -i/--initial option is ignored on incremental backups.

The -o/--options option permits including additional rsync options (comma separated).

Examples:

image-backup

image-backup /media/backup.img

image-backup --initial /media/backup.img,,5000 --noexpand --options --exclude-from=/home/pi/exclude.txt,--delete-excluded


Image-check:

image-check will check the integrity of a standard 'raw' image file.  Usage is:

image-check imagefile [W95|Linux]

where W95 checks the BOOT partition and Linux checks the ROOT partition.  If neither is specified, Linux is assumed.


image-compare:

image-compare compares a running Raspbian system to an existing standard 'raw' image file and displays the incremental changes that image-backup would perform if run.  Usage is:

image-compare [imagefile]


image-info:

image-info displays information about a standard 'raw' image file.  Usage is:

image-info [imagefile]



image-mount:

image-mount mounts a standard 'raw' image file to allow it to be read or written as if it were a device.  Usage is:

image-mount imagefile mountpoint [W95|Linux]

where W95 mounts the BOOT partition and Linux mounts the ROOT partition.  If neither is specified, Linux is assumed.


image-set-partuuid:

image-set-partuuid sets the ROOT partition PARTUUID value of a standard 'raw' image file.  Usage is:

image-set-partuuid imagefile [ hhhhhhhh-02 | hhhhhhhh-hhhh-hhhh-hhhh-hhhhhhhhhhhh | random ]"

If no partuuid is specified, the current ROOT partuuid will be displayed.


image-shrink:

image-shrink shrinks a standard 'raw' image file to its smallest possible size (plus an optional additional amount of free space).  Usage is:

image-shrink imagefile [Additional MB]

where Additional MB is an optional additional amount of free space to be added.
