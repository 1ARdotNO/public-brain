---
{"dg-publish":true,"permalink":"/mac-os/macos-touch-id-sudo/","tags":["public","macos","sudo"]}
---

To use touchid for sudo on your mac

edit `/etc/pam.d/sudo`
Add the following to the top of the file
```
auth sufficient pam_tid.so
```
Script to have it set the setting automatically if it is not set. (useful for deployment in intune etc)
```bash
#!/bin/bash
if ! grep 'pam_tid.so' /etc/pam.d/sudo --silent; then
  sed -i -e '1s;^;auth       sufficient     pam_tid.so\n;' /etc/pam.d/sudo
fi
```