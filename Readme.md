
# Operation and configuration of radproc

**This is under development. Not yet operational**

**This is a public repository, don't put passwords and other private info in any file
here!**

**Will auto commit until there is more than one contributors.**

radproc is a computer for processing the broadband radiation data of LAP. Currently
not all processing is done by this machine.


## TODO

- [ ] add another HDD
- [ ] create btrfs mirrors
- [ ] install grub on both disks
- [ ] try to run BBand_LAP
    - [ ] install and describe dependencies



## Config

In `/etc/fstab` there are configured mounts to "sirena" and "radmon" in order to have
access to the data.

- /media/raddata/:             Access to raw data from the acquisition machine
- /media/raddata_cloud_flags/: Export cloud flags data to the acquisition machine for public use
- /media/sirena_lapdata_ro/:   Access to the repository of broadband data
- /media/tracker_CHP1_ro/:     Access to log data of the tracker



## Software

The source code for some of the data processing is in:
[github.com/thanasisn/BBand_LAP](https://github.com/thanasisn/BBand_LAP)


## Usage

All data and processes are under user 'athan'.

- ~/BBand_LAP:  Processing source code
- ~/DATA:       Main local data storage
- ~/LOGs:       Logs for the machine
- ~/PANDOC:     This git repository
- ~/ZHOST:      Helper folder for user data sync


## Other



