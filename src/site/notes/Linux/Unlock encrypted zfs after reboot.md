---
{"dg-publish":true,"permalink":"/linux/unlock-encrypted-zfs-after-reboot/","tags":["public","pve","zfs"],"noteIcon":"1"}
---

When using encrypted zfs the volume must be unloacked upon boot, the manual way of doing this is to run this command and enter the passphrase when prompted

```bash
zfs load-key -a
```
