---
{"dg-publish":true,"permalink":"/mac-os/apple-silicon-dfu-mode/","tags":["public","macos"],"noteIcon":"1","created":"2024-08-03T14:55:34.713+02:00","updated":"2024-02-23T14:27:22.000+01:00"}
---

To get a AppleSilicon machine into DFU mode can sometimes be hard or even impossible from apple's instructions.

A good solution I found is to use https://bitbucket.org/twocanoes/dfu-blaster-public/downloads/ DFU Blaster tool from "Tim" aka. twocanoes,
DFU blaster uses the Serial thunderbolt console inteface to send the correct command to fore the machine into DFU without the keyboard gymnastics.

> [!warning] USB restrictions
>If your the computer you are using to assist in the recovery has USB restricions as part of corporate policy etc. this will not work

![Pasted image 20240223142611.png](/img/user/MacOS/attachments/Pasted%20image%2020240223142611.png)
Machine should now go into DFU mode and you can continue your recovery actions.


> [!info] Charger
> Charger on the target computer was not neccessary in my case with firmware recovery, but it is probably "smart" too ensure power does not run out while it is doing the tasks
