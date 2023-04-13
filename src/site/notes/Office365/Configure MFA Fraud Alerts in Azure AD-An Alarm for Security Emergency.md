---
{"dg-publish":true,"permalink":"/office365/configure-mfa-fraud-alerts-in-azure-ad-an-alarm-for-security-emergency/","tags":["public","office365","mfa"],"noteIcon":"1","created":"2023-03-14T12:05:25.561+01:00","updated":"2023-04-03T17:59:16.846+02:00"}
---


 ## **What is a Multi-Factor Authentication Fraud Alert?** 
 
  *MFA fraud alerts are used to alert the admins when the* ***multi-factor authentication request is initiated without the users’ concern.*** *In MFA fraud alerting, the users notify the admins by reporting fraudulent activity that occurred in their accounts.*  
 
 The users can report the fraudulent activity at the time of denying the MFA request in the authenticator app or by entering the fraud code in an automated telephone system. 
 
 ## **What is the Purpose of MFA Fraud Alerts?** 
 
 Now you might be wondering what the exact purpose of this MFA fraud alert is and what they do. So, let’s get to see the purpose of MFA fraud alerts. 
 
 -   The main purpose of this MFA fraud alert is to **notify the admin that a suspicious MFA request has been initiated for a user**.  Though these alert notifications do not solve the problem directly, it makes you get informed and well-prepared to face it! 
 -   Most importantly, MFA fraud alerts reduce the potential risk of [MFA fatigue attacks](https://blog.admindroid.com/safeguard-office-365-users-from-mfa-fatigue-attacks/), also known as MFA Bombing. One such technique that recently attacked the giant company Uber in September last year.
 
 -   -   MFA fatigue attack is a social engineering technique that uses human error to gain information. In detail, attackers steal the user’s credentials by brute force or password spray attacks. Then, they send continuous MFA requests to prompt the user to accept one accidentally. Once the user accepts an MFA request, the hacker easily gets into the user account and tends to exploit it. 
 
 Therefore, avoid MFA fatigue at the initial stage using **MFA fraud alerts!** It allows you to investigate and take necessary security measures against fraudulent activity. So, now let us see how to configure MFA fraud alerts in Microsoft 365. 
 
 ## **How to Configure MFA Fraud Alerts in Azure AD?** 
 
 With just a few clicks, you can set up MFA fraud alerts for your organization and protect against fraudulent activity. To enable the settings, navigate through the following path. 
 
 1.   ***Microsoft Entra admin center 🡢 Protect and Secure 🡢 Security Center (Click ‘Show more’) 🡢 Manage 🡢 Multi-factor Authentication.***   
      
 2.  Now on getting into the ‘multi-factor authentication’ page, select **Fraud alert** among the security settings.  
      
 3.   Then, you can configure the fraud alert settings below. 
 
 -   **Allow users to submit fraud alerts –** Enable this setting to allow users to submit a report when an MFA request is initiated that they did not request. As a result, you’ll be able to **identify the user accounts targeted by unknown MFA requests** and take measures to safeguard your organization against future emerging threats such as phishing scams.
 
 -   **Automatically block users who report fraud –**To immediately block the targeted user accounts that have been attempted for compromise, push this toggle button to the ‘On’ condition. 
 
 **PROS and CONS of the Block Users Option:** 
 
 -   -   If this block option is turned off, the user will not be blocked immediately. Therefore, as an alternative option, admins can configure to **send email alert notifications to specific users** about the suspicious MFA request. Then, they should investigate the situation and decide which response action to take.  
          
     -   While enabling this option has both advantages and disadvantages! One of the greatest advantages of enabling this setting is that it **immediately blocks further requests from hackers.**  
          
         -   But sadly, if a user reports a suspicious MFA request, the **user account will be blocked** until the admin unblocks the account. Eventually, blocking the user account will cause trouble for the user productivity.  So ultimately, the admin has to decide whether to enable this setting or not based on their organization’s security posture. 
 
 -   **Code to report fraud during initial greeting –** By default, users can report suspicious MFA requests by entering the code 0. Now, with this setting, admins can customize the code number to report a fraudulent MFA request. 
 
 ![MFA Fraud alerts page in Azure AD](/img/user/attachments/MFA_Fraud_alerts_page_in_Azure_AD.png)
 
  4. After finishing the configuration, store them using the **Save** option. Hereafter, your users will be able to report any suspicious multi-factor authentication requests in the Microsoft Authenticator app while denying the request. A sample of the report option is given below. 
 
 ![Report MFA Fraud alerts in Authenticator app](/img/user/attachments/Report_MFA_Fraud_alerts_in_Authenticator_app.png)
 
 As we are now clear in configuring the multi-factor authentication fraud alerts, let us see how to turn on notifications for the admin or security team. 
 
 ### **Turn On Notifications about MFA Fraud Alerts** 
 
 Instead of viewing the reports every time to know about the suspicious activities happening around the organization, admins can get notified in real-time about every unusual behavior. In order to receive notifications via email when a user reports a fraud alert via the authenticator app or automated telephone system, admins should follow the steps below and configure email alert notifications for specific users. 
 
 ***Microsoft Entra admin center*** **🡢** ***Protect and Secure*** **🡢** ***Security center*** **🡢** ***Multi-Factor Authentication*** **🡢** ***Notifications.*** 
 
 On the notification page, you can add the email address of the people you want to receive notifications of unknown MFA requests. Do not forget to save them once you add all the recipients. Look at the screenshot below for the notification page and email of MFA fraud alert. 
 
 ![MFA fraud alerts notification](/img/user/attachments/MFA_fraud_alerts_notification.png)
 
 ### **View Suspicious Activities Reports in Azure AD Audit Logs** 
 
 When a user reports an unfamiliar MFA request, it gets logged in the Azure AD audit logs as the user has been blocked for MFA. Admins can use this report to identify and disable the impacted users. Thereby, view the reports by navigating to the below path:   
 
 ***Microsoft Entra admin center*** **🡢** ***Users*** **🡢** ***All Users*** **🡢** ***Audit logs.***
 
 The report for fraud activity in Audit logs is present under activity type as **Fraud reported – user is blocked for MFA,** and **Fraud reported – no action taken**. 
 
 ![View suspicious activity reports in Audit logs](/img/user/attachments/View_suspicious_activity_reports_in_Audit_logs.png)
 
 ### **MFA Fraud Reports in Azure AD Sign-in logs** 
 
 When a user reports an unknown MFA request, the event is logged in the sign-in logs as sign-in request was rejected. MFA fraud report appears in result detail as part of the standard Azure AD sign-ins report. MFA fraud report is indicated as **MFA denied: Phone App Reported Fraud** in the result detail column.  
 
 You can also view the suspicious events in the Sign-ins report using the following path.  
 
 ***Microsoft Entra admin center*** **🡢** ***Users*** **🡢** ***All Users*** **🡢** ***Sign-in logs*** **🡢** ***Authentication details*****.** 
 
 ![MFA Fraud reports in Sign-in logs](/img/user/attachments/MFA_Fraud_reports_in_Sign-in_logs.png)
 
 Therefore, **implement multi-factor authentication fraud alerts** in your tenant to protect your organization from cyber security threats like MFA bombing. 
 
 #### **Recommended Security Measures For Fraud Alert Reporting:**
 
 -   In the first instance, when admins observe continuous user reporting activity, they can **manually block the specific user sign-in** if they consider the risks too high.  
      
 -   Otherwise, they can **reset the password of the targeted user** as that user account doesn’t impose much threat to the organization.

source: [Configure MFA Fraud Alerts in Azure AD-An Alarm for Security Emergency](https://o365reports.com/2023/03/14/configure-mfa-fraud-alerts-in-azure-ad-an-alarm-for-security-emergency/)
