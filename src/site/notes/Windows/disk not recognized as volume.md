---
{"dg-publish":true,"permalink":"/windows/disk-not-recognized-as-volume/","tags":["public","windows"],"noteIcon":"1"}
---


After using third party utilities such as clonezilla, gparted or ntfsclone it is possible to get into this situation, where the disk is not bootable and not reconized as a volume meeaning further fixes with bcdboot etc is not possible. To solve this you must set the partition type id

Find out which partition X you need to associate with an letter:

```
diskpart> list partition
diskpart> select partition X
diskpart> detail partiton  # I found that partition was hidden
```

If your disk has GPT table, set [partition type GUID](https://en.wikipedia.org/wiki/GUID_Partition_Table#Partition_type_GUIDs) as _Microsoft basic data partition_ (corresponding _gdisk_ partition type is `0700`):

```
diskpart> set id=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
```

If your disk in MBR (`07` = Windows NT NTFS; `17` = Hidden; `27` = OEM Recovery):

```
diskpart> set id=07 override
```

Now you can try `diskpart> list partition` again. `bcdboot c:\Windows`

ref:
[hard drive - Diskpart assign letter to partition that is not associated with a volume (windows 10) - Super User](https://superuser.com/questions/978076/diskpart-assign-letter-to-partition-that-is-not-associated-with-a-volume-window)