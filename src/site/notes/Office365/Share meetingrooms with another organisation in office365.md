---
{"dg-publish":true,"permalink":"/office365/share-meetingrooms-with-another-organisation-in-office365/","tags":["public"],"noteIcon":"1","created":"2023-08-15T14:20:13.000+02:00","updated":"2023-03-13T12:39:17.000+01:00"}
---

#office365 
## about 
Often it is useful to enable members of another org. to access your meeting rooms, both for booking and for viewing busy/free status.

# Implementation

#### Create a group with all the affected meeting rooms within
- This group needs to be a security enabled distribution group.

#### Setup organization sharing
Go to exchange controll center > Organization > Sharing
Click the `+` under organization sharing to add and entry.
Setup as shown in the picture, make sure to define the group created earlier in the "browse..." box, otherwise all meetingsrooms will be made available.
![Pasted image 20230307152755.png](/img/user/Office365/attachments/Pasted%20image%2020230307152755.png)
This allows the other org to see /free/busy status of the meeting rooms in the group.

In the org you are sharing with this also needs to be configured, but you do not have to share anything back if you do not want to, ie. do not check the "enable calendar free/busy information sharing"

#### Enable external calendar processing
Connect to exchangeonline using #powershell and run this command for each room
```powershell
get-mailbox -identity "room@company.com" | Set-CalendarProcessing -ProcessExternalMeetingMessages $true
```
This allows ANY external email to book the room, we will restrict this in the next step

#### Create transport rule to restrict sender domain
Go to exchange control center, Mailflow > Rules
Create a new rule as follows ( for the first field, "Apply this rule if..." you can utilize the group created earlier)
![Pasted image 20230307153429.png](/img/user/Office365/attachments/Pasted%20image%2020230307153429.png)

After this, any person from the other org will be able to add the room in their outlook, see status and also book the room :-) 

Some additional info on this can be found here;
 - [Enable External Users to Book Meeting Rooms · (dot)pwsh](https://dotsh.no/2020/02/14/enable-external-booking-of-meeting-rooms/)
 - [Create an organization relationship in Exchange Online | Microsoft Learn](https://learn.microsoft.com/en-us/exchange/sharing/organization-relationships/create-an-organization-relationship)
 - [Redirecting](https://answers.microsoft.com/en-us/msoffice/forum/all/external-booking-view-of-availability-of-meeting/9411ad13-08ec-4c8c-b3f2-47b2e5393843)
 - [Sharing meeting rooms between 2 office365 Domains/Accounts - Microsoft Community](https://answers.microsoft.com/en-us/msoffice/forum/all/sharing-meeting-rooms-between-2-office365/c5d6ba4e-678a-49c1-8780-ca39fdb2c0d0)