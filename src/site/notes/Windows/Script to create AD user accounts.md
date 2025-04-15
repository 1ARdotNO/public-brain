---
{"dg-publish":true,"permalink":"/windows/script-to-create-ad-user-accounts/","tags":["public","ai","ad"],"noteIcon":"1"}
---



```powershell
# Import the Active Directory module
Import-Module ActiveDirectory

# Set the parameters for the new user account
$SamAccountName = "jdoe"
$FirstName = "John"
$LastName = "Doe"
$DisplayName = "$FirstName $LastName"
$UserPrincipalName = "$SamAccountName@yourdomain.com"
$Password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Path = "OU=Users,DC=yourdomain,DC=com"

# Create the new user account
New-ADUser `
    -SamAccountName $SamAccountName `
    -UserPrincipalName $UserPrincipalName `
    -DisplayName $DisplayName `
    -GivenName $FirstName `
    -Surname $LastName `
    -AccountPassword $Password `
    -Enabled $true `
    -Path $Path

# Add the user to a group
Add-ADGroupMember "GroupName" $SamAccountName
```

This script creates a new user account with the specified parameters and enables it. You can also add additional attributes like email address, office location, title, etc. by modifying the `New-ADUser` cmdlet. Finally, you can add the user to one or more groups using the `Add-ADGroupMember` cmdlet.