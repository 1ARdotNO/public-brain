---
{"dg-publish":true,"permalink":"/stuff/clearing-hsts-in-chrome/","tags":["public","chrome"],"noteIcon":"1","created":"2023-10-18T09:41:48.677+02:00","updated":"2023-10-18T09:43:43.146+02:00"}
---

If you get an error message about invalid HSTS when trying to reach some site where the SSL certificate has changed or something like that, you can visit 
```
chrome://net-internals/#hsts
```
Then put the domain you want to fix into, and click delete
![Pasted image 20231018094335.png](/img/user/Stuff/attachments/Pasted%20image%2020231018094335.png)