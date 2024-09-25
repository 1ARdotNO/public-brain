---
{"dg-publish":true,"permalink":"/windows/register-the-physical-device-with-windows-autopilot/","tags":["public","windows","windows365"],"noteIcon":"1","created":"2024-08-03T14:55:33.177+02:00","updated":"2023-11-21T11:06:43.000+01:00"}
---

1. At the physical device's sign-in prompt, use Shift+F10 to open a command prompt.
 
2. In the command prompt, run the following commands

3. When prompted, sign in with a user that has the Intune Administrator role. After sign-in, the device is automatically enrolled in Intune. Make a note of the serial number.

```cmd
PowerShell.exe -ExecutionPolicy Bypass 
[Net.ServicePointManager]::SecurityProtocol  = [Net.SecurityProtocolType]::Tls12 
Install-Script -name Get-WindowsAutopilotInfo -Force 
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned 
Get-WindowsAutopilotInfo -Online
```