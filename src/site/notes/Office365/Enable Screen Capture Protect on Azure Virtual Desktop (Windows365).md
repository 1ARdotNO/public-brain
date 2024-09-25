---
{"dg-publish":true,"permalink":"/office365/enable-screen-capture-protect-on-azure-virtual-desktop-windows365/","tags":["public","office365","windows365"],"noteIcon":"1","created":"2024-08-03T14:52:58.248+02:00","updated":"2023-04-13T22:02:12.000+02:00"}
---


## about
To enable the Screen Capture Protection feature we need a very simple PowerShell Script (it can also be done using admx GPO templates, but this is the easiest way for Intune managed systems.)

Microsoft article: [Screen capture protection in Azure Virtual Desktop - Azure | Microsoft Learn](https://learn.microsoft.com/en-us/azure/virtual-desktop/screen-capture-protection)

## script 
```powershell
#Enable ScreenCaptureProtection

Set-ItemProperty "HKLM:SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services" -Name fEnableScreenCaptureProtection -Value 1 -Type DWORD
```

## Implementation
1.  Sign in to Microsoft Endpoint Manager portal ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/))
2.  Select Devices and then select Scripts or Windows devices -> Windows Policies and select PowerShell Scripts.
3.  To add a new PowerShell script, click Add button and deploy it to Windows 10 devices.
4. Specify the name of the PowerShell script and you may add a description as well. Click Next.
5. On the Script Settings window, you specify the script location. Click the folder icon and specify the PowerShell that you intend to deploy using Intune to devices.

![attachments/Pasted image 20230413145326.png](/img/user/Office365/attachments/Pasted%20image%2020230413145326.png)
6. Lastly we configure Assignments. This determines to who you deploy the PowerShell script. Click Add Group and select your AVD Session Host group.
7. To trigger the changes immediately reboot your AVD Session host and check the registry if the Key is applied.

![No alt text provided for this image](https://media.licdn.com/dms/image/C4E12AQH-M7UU14wyEw/article-inline_image-shrink_1500_2232/0/1624545418284?e=1686787200&v=beta&t=AYzMM9QQy3pFz2-v_pwNVj1845JHiC13-RAMbtDGaqo)
### Running into errors? Review IntuneManagementExtension Log File

Win32app and PowerShell Scripts deployed are installed using the Intune Management Extension and there are log files to troubleshoot application deployment. The log files for the Intune Management Extension are located in C:\ProgramData\Microsoft\IntuneManagementExtension\Logs. Review the IntuneManagementExtension.log.

![No alt text provided for this image](https://media.licdn.com/dms/image/C4E12AQHzPZgZArJ5Ew/article-inline_image-shrink_1500_2232/0/1624545354713?e=1686787200&v=beta&t=AoIQKdu80UG60mXo4BRFhMTe6S3sbRXUnjs6MtaejQ4)

Sources: [Enable Screen Capture Protect on Azure Virtual Desktop AVD with Microsoft Endpoint Manager MEM](https://www.linkedin.com/pulse/enable-screen-capture-protect-azure-virtual-desktop-avd-baur/)