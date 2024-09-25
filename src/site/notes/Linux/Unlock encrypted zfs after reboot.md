---
{"dg-publish":true,"permalink":"/linux/unlock-encrypted-zfs-after-reboot/","tags":["public","pve","zfs"],"noteIcon":"1","created":"2024-08-03T14:55:34.868+02:00","updated":"2024-02-02T15:14:51.000+01:00"}
---

When using encrypted zfs the volume must be unloacked upon boot, the manual way of doing this is to run this command and enter the passphrase when prompted

```bash
zfs load-key -a
```
