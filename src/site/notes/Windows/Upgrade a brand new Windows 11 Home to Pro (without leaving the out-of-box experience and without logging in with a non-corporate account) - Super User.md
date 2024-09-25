---
{"dg-publish":true,"permalink":"/windows/upgrade-a-brand-new-windows-11-home-to-pro-without-leaving-the-out-of-box-experience-and-without-logging-in-with-a-non-corporate-account-super-user/","tags":["public","windows"],"noteIcon":"1","created":"2024-08-04T21:16:22.113+02:00","updated":"2024-09-05T14:29:26.296+02:00"}
---

1. Choose language, keyboard layout, device name etc.
    
2. Once you hit the login screen, press shift + F10 to open CMD. Technically you can open CMD while it's installing Updates but I don't recommend this because it will restart without warning and might interrupt the following process.
    
3. Run `slui.exe /upk`. This is not always necessary but I suspect sometimes the Home license will be installed and needs to be removed first. Doesn't hurt to do anyway.
    
4. Run `changepk.exe /ProductKey <Your product Key>` It will say it failed but ignore it.
    
5. Restart
    
6. It's now Windows 11 Pro.


EX.
- Running `changepk.exe /ProductKey VK7JG-NPHTM-C97JM-9MPGT-3V66T` (Key for Windows 11 Pro) brought up the "Preparing for Upgrade" dialogue but then failed with Error Code `0x80070490`

[![Windows Upgrading](https://i.sstatic.net/YC7Ic.png)](https://i.sstatic.net/YC7Ic.png)

[![Failed to Upgrade Error Code 0x80070490](https://i.sstatic.net/Qknwa.png)](https://i.sstatic.net/Qknwa.png)

- I also tried `slmgr.vbs /ipk VK7JG-NPHTM-C97JM-9MPGT-3V66T`. This errored with 0xC004F069 and said to run SLUI to get full details. [![enter image description here](https://i.sstatic.net/8MocA.png)](https://i.sstatic.net/8MocA.png)
    
- I ran `slui.exe 0x2a 0xC004F069` and it said [![enter image description here](https://i.sstatic.net/i0PcH.png)](https://i.sstatic.net/i0PcH.png)
    
- However, I then ran `slui.exe /upk` to uninstall the Product Key, and then tried `changepk.exe` again, after rebooting the OOBE was now for Windows 11 Pro and I could create a local user and domain join. [![CMD showing windows version to be 11 Pro.](https://i.sstatic.net/HJdop.png)](https://i.sstatic.net/HJdop.png) [![Windows 11 Pro signup page.](https://i.sstatic.net/HZFKK.png)](https://i.sstatic.net/HZFKK.png)