---
{"dg-publish":true,"permalink":"/mac-os/macos-printing-issue-after-14-4/","tags":["print","macos"],"noteIcon":"1","created":"2024-08-03T14:55:51.825+02:00","updated":"2024-03-14T19:39:14.000+01:00"}
---

# New Mac OS 14.4 update - broke printing, no drivers listed

Seems somehow to be related to Microsoft defender.
Even if you have the Full disk access enabled for defender in mobileconfig distributed by intune, [Intune-based deployment for Microsoft Defender for Endpoint on Mac | Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/mac-install-with-intune?view=o365-worldwide#step-3-full-disk-access)
This will somehow affect the printers.
If you go to privacy and security, and enable full disk access for 
```
“Microsoft defender Endpoint security extension”  
com.microsoft.dlp
```
that will "fix" the problem, but unclear why this suddenly happened with this update.
Either this is a bug or some unintentional change from apples side, ooooor microsoft needs to update defender, or the documentation for defender.

A note regarding earlier versions of macos, when the mobileconfig as above is published, the options do NOT appear as checked in the PPPC control panel. even if it seems that defender does have these accesses.