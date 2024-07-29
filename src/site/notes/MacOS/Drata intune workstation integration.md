---
{"dg-publish":true,"permalink":"/mac-os/drata-intune-workstation-integration/","tags":["public","macos","intune","drata"],"noteIcon":"1","created":"2024-04-10T12:19:11.159+02:00","updated":"2024-04-11T20:03:06.000+02:00"}
---

## about

Drata has a plugin that is connected to Intune via an app that collects data from the workstations.

This integration checks various properties of the computer to ensure it is compliant with Antivirus, encryption, screen lock etc.

#### Problem with computers being flagged as “not conmpliant” for auto updates

This seems to stem from some bug in drata’s end. The machines are incorrectly tagged with this error if there are any configuration profiles that have an error in being applied, such as conflict or failed.

A common cause of this is the “Filevault policy”, this policy will fail if filevault was setup on the computer before the intune integration was done. This is mostly the case on computers that was deployed a long time ago, before intune was used in the company.

The fix for this is to manually rotate the filevault key on the computer, this will cause intune to pick it up again, and the error flag will be cleared after a full sync of the computer.
See [[MacOS/force macos filevault key rotation intune\|force macos filevault key rotation intune]]