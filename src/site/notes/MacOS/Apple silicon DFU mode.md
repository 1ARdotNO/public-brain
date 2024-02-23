---
{"dg-publish":true,"permalink":"/mac-os/apple-silicon-dfu-mode/","tags":["public","macos"],"noteIcon":"1","created":"2024-02-23T14:19:31.843+01:00","updated":"2024-02-23T14:24:34.101+01:00"}
---

To get a AppleSilicon machine into DFU mode can sometimes be hard or even impossible from apple's instructions.

A good solution I found is to use https://bitbucket.org/twocanoes/dfu-blaster-public/downloads/ DFU Blaster tool from "Tim" aka. twocanoes,
DFU blaster uses the Serial thunderbolt console inteface to send the correct command to fore the machine into DFU without the keyboard gymnastics.

> [!warning] USB restrictions
>If your the computer you are using to assist in the recovery has USB restricions as part of corporate policy etc. this will not work

Machine should now go into DFU mode and you can continue your recovery actions.