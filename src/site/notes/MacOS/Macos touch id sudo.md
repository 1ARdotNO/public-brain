---
{"dg-publish":true,"permalink":"/mac-os/macos-touch-id-sudo/"}
---

To use touchid for sudo on your mac

/etc/pam.d/sudo
Add the following to the top of the file
```
auth sufficient pam_tid.so
```