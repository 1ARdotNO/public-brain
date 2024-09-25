---
{"dg-publish":true,"permalink":"/mac-os/hide-application-from-application-list-macos/","tags":["macos","public"],"noteIcon":"1","created":"2024-08-03T14:55:52.256+02:00","updated":"2024-04-29T16:15:17.000+02:00"}
---


Run the following command to hide a app from the "Applications" on macos
```bash
sudo chflags hidden /Applications/PowerShell.app
```

To show it again,
```bash
sudo chflags nohidden /Applications/PowerShell.app
```