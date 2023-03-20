---
{"dg-publish":true,"permalink":"/mac-os/filevault-password-out-of-sync-issues/","tags":["public","macos","domain","activedirectory"],"noteIcon":"1","created":"","updated":""}
---


The following steps will remove and re-add a user to filevault so that the password will be in sync with the user again.  (This can happen when using mobile accounts with active directory when changing password from AD or another device)
You will need another admin account with a securetoken assigned to complete the process

1.  Type **sudo fdesetup remove -user** _**username**_ and press Return, where _username_ is your olanordmann username.
![Pasted image 20221124115406.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115406.png)
3. Type the password of the admin account to which you are signed in, and then press Return.
![Pasted image 20221124115423.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115423.png)
Type **sudo fdesetup add -usertoadd** _**username**_ and press Return, where _username_ is your olanordmann username.
![Pasted image 20221124115435.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115435.png)
Type the username of an administrator's account on your Mac, and then press Return.
![Pasted image 20221124115450.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115450.png)
Type the password for the administrator's account from Step 6, and press Return.
![Pasted image 20221124115536.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115536.png)
Type the current  password for the account you are re-adding, and then press Return.
![Pasted image 20221124115547.png](/img/user/MacOS/attachments/Pasted%20image%2020221124115547.png)