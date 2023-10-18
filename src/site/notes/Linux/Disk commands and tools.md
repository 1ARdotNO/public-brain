---
{"dg-publish":true,"permalink":"/linux/disk-commands-and-tools/","tags":["public"],"noteIcon":"1","created":"2023-08-15T14:20:14.000+02:00","updated":"2022-12-23T10:22:06.000+01:00"}
---


#### Expand LVM when resizing virtual disks
```bash
#resize the LVM partition to expand to all available space
pvresize /dev/sdb
#expand the logical volume to desired size
lvextend /dev/elastic/elastiv-lv -L 195G 
#resize the file system to the new logical volumes size
resize2fs /dev/elastic/elastiv-lv
```