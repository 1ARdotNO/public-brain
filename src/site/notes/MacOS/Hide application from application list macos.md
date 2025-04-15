---
{"dg-publish":true,"permalink":"/mac-os/hide-application-from-application-list-macos/","tags":["macos","public"],"noteIcon":"1"}
---


Run the following command to hide a app from the "Applications" on macos
```bash
sudo chflags hidden /Applications/PowerShell.app
```

To show it again,
```bash
sudo chflags nohidden /Applications/PowerShell.app
```