---
{"dg-publish":true,"permalink":"/windows/set-local-user/","tags":["powershell","windows"],"noteIcon":"1"}
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


