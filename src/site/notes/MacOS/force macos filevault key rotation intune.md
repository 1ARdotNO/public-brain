---
{"dg-publish":true,"permalink":"/mac-os/force-macos-filevault-key-rotation-intune/","tags":["public","macos","intune"],"noteIcon":"1"}
---

DPIn in tune you might encounter a device where filevault key is missing, this is typically becuase the device was already filvault encrypted before it was onboarded in intune.
To solve this you can trigger a rotation of the key locally on the device. (Using the rotate key button in intune does not work, because intune does not know what the old key was)

run the following command, and authenticate with a user that has filevault access.
```bash
fdesetup changerecovery -personal
```
Needs ```sudo``` if not running as root.


> [!NOTE] Configuration profile
> This also resolves it so that the configuration provfile for filevault will display as "green"
> It can take up to 8 hours before status updates
