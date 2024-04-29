---
{"dg-publish":true,"permalink":"/mac-os/hide-application-from-application-list-macos/","tags":["macos","public"],"noteIcon":"1","created":"2024-04-29T16:12:19.998+02:00","updated":"2024-04-29T16:15:17.745+02:00"}
---


Run the following command to hide a app from the "Applications" on macos
```bash
sudo chflags hidden /Applications/PowerShell.app
```

To show it again,
```bash
sudo chflags nohidden /Applications/PowerShell.app
```