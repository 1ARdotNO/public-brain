---
{"dg-publish":true,"permalink":"/linux/unlock-encrypted-zfs-after-reboot/","tags":["public","pve","zfs"],"noteIcon":"1","created":"2024-01-25T07:01:34.860+01:00","updated":"2024-01-25T07:03:08.025+01:00"}
---

When using encrypted zfs the volume must be unloacked upon boot, the manual way of doing this is to run this command and enter the passphrase when prompted

```bash
zfs load-key -a
```
