---
{"dg-publish":true,"permalink":"/office365/error-when-setting-up-autopilot-device/","tags":["public"],"noteIcon":"1"}
---


When configuring a [[autopilot\|autopilot]] device you can get an error that stops the process after entering their credentials.
The error relates to conditional access policy where they are not authorized to use this device. 

The app name is listed as "Microsoft Authentication Broker"
AFAIK this error only appears if this machine is using autopilot, and you have reset the device and want to set it up again. 

The solution is to delete the old device from intune, this causes the error to dissappear.

this page contains som more info;
[AutoPilot and Conditional Access conflict : Intune](https://www.reddit.com/r/Intune/comments/k5hpe3/autopilot_and_conditional_access_conflict/)