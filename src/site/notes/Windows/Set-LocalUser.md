---
{"dg-publish":true,"permalink":"/windows/set-local-user/","tags":["powershell","windows"],"noteIcon":"1","created":"2022-12-23T10:51:18.849+01:00","updated":"2022-12-23T10:51:18.849+01:00"}
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