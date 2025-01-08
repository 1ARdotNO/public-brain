---
{"dg-publish":true,"permalink":"/mac-os/i-phone-and-i-os-enrolment-error-company-portal/","tags":["public","intune","macos","ios","apple","iphone","companyportal","azuread"],"noteIcon":"1"}
---

During iOS company portal enrollment the following error might present;
"your account can't be enrolled with this retired method"

This is something that happened recently, most likely due too some change from Microsoft side.

It happens when you use "user enrollment" for your [enrollment type profile](https://intune.microsoft.com/?ref=AdminCenter#view/Microsoft_Intune_Enrollment/UserInitiatedEnrollmentProfileMenuBlade)

I found this page [Set up user enrollment with Company Portal for iOS - Microsoft Intune \| Microsoft Learn](https://learn.microsoft.com/en-us/mem/intune/enrollment/apple-user-enrollment-with-company-portal) , which seems to point to that this enrollment type is deprecated and no longer working.
![Pasted image 20250108105820.png](/img/user/MacOS/attachments/Pasted%20image%2020250108105820.png)

The solution is to edit your enrollment type profile and transition to another enrollment type, [account-driven user enrollment](https://learn.microsoft.com/en-us/mem/intune/enrollment/apple-account-driven-user-enrollment) instead as it matches the old user enrollment most closely 
![Pasted image 20250108105850.png](/img/user/MacOS/attachments/Pasted%20image%2020250108105850.png)