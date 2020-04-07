[![Build Status](https://travis-ci.com/fabiomarinetti/fmarinetti.logicalvolume.svg?branch=master)](https://travis-ci.com/fabiomarinetti/fmarinetti.logicalvolume)

fmarinetti.logicalvolume
=========

This role creates a dedicated volume from a new partition to mount on a desired mountpoint

Requirements
------------

parted version 1.8. 3 and above.  
If the version of parted is below 3.1, it requires a Linux version running the sysfs file system /sys/

Role Variables
--------------

All these variable can be overridden in the playbook:

- part_end: the end size of the new partition (default: 100% --> to the end of disk)  
- partno: the partition sequential number (default: 1)
- device: the device to partition (default: /dev/sda)
- vgname: the volume group name (default: ansible_vg)
- lvname: the logical volume (default: ansible_lv)
- lvsize: the size of the logical volume (default: 100%VG)
- fstype: the filesystem type
- mountpoint: the mountpoint where to mount the lv to (default: /mnt), it is created if not existing

Dependencies
------------

None

Example Playbook
----------------

Create a partition on device sdb, make a volume group myvg with the associated physical volume, create the lv mylv, create the ext4 filesystem and mount it on /media. 
```
    - hosts: servers
      vars:
        device: /dev/sdb
        vgname: myvg
        lvname: mylv
        mountpoint: /media
      roles:
         - dedicated_volume
```
License
-------


Author Information
------------------

