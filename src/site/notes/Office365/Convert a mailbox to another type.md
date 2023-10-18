---
{"dg-publish":true,"permalink":"/office365/convert-a-mailbox-to-another-type/","tags":["public"],"noteIcon":"1","created":"2023-08-15T14:20:13.000+02:00","updated":"2023-03-07T20:45:39.000+01:00"}
---

#office365 #outlook 
### You can convert the following mailboxes to a different type:

-   User mailbox to room or equipment mailbox
-   User mailbox to shared mailbox
-   Shared mailbox to user mailbox
-   Shared mailbox to room or equipment mailbox
-   Room or equipment mailbox to user mailbox
-   Room or equipment mailbox to shared mailbox

 ## Use the Exchange Management Shell to convert a mailbox
 
 To convert a mailbox to a different type, use this syntax:
 
 ```powershell
Set-Mailbox -Identity <MailboxIdentity -Type <Regular | Room | Equipment | Shared [-Password (ConvertTo-SecureString -String '<Password' -AsPlainText -Force)] [-EnableRoomMailboxAccount <$true | $false] [-RoomMailboxPassword (ConvertTo-SecureString -String '<Password' -AsPlainText -Force)] [-ResetPasswordOnNextLogon <$true | $false]
 ```
This example converts the shared mailbox named Marketing Dept 01 to a user mailbox with the new password P@ssw0rd25, and the requirement to change the password the next time the user logs in to the mailbox.

PowerShellCopy

```powershell
Set-Mailbox -Identity "Marketing Dept 01" -Type Regular -Password (ConvertTo-SecureString -String 'P@ssw0rd25' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
```

This example converts the user mailbox named Conference Room 01 to a room mailbox.

PowerShellCopy

```powershell
Set-Mailbox -Identity "Conference Room 01" -Type Room
```

This is the same example, but the user account for the room mailbox is enabled, and the password is P@ssw0rd25

PowerShellCopy

```powershell
Set-Mailbox -Identity "Conference Room 01" -Type Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'P@ssw0rd25' -AsPlainText -Force)
```

**Note**: Even when you convert a user mailbox with a known password to a room mailbox, you still need to use the _RoomMailboxPassword_ parameter to specify a password.

For detailed syntax and parameter information, see [Set-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailbox).