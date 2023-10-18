---
{"dg-publish":true,"permalink":"/windows/set-local-user/","tags":["powershell","windows"],"noteIcon":"1","created":"2023-08-15T14:20:12.000+02:00","updated":"2023-03-27T22:00:05.000+02:00"}
---


### Change the password on an account

 ```powershell
$Password = Read-Host -AsSecureString
$UserAccount = Get-LocalUser -Name "User02"
$UserAccount | Set-LocalUser -Password $Password
```

### Enable account


 ```powershell
$UserAccount = Get-LocalUser -Name "User02"
$UserAccount | Enable-LocalUser
```


