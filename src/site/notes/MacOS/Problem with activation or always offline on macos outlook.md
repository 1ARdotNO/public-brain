---
{"dg-publish":true,"permalink":"/mac-os/problem-with-activation-or-always-offline-on-macos-outlook/","tags":["public","outlook","macos"],"noteIcon":"1","created":"2024-08-03T14:52:59.242+02:00","updated":"2022-12-23T10:51:18.000+01:00"}
---

There can be a problem with outlook on mac where it looses its activation and is forced into offline mode.
And refuses to be reactivated, the solution is to remvoe all cache;

Go to /Users/USERNAME/Library/Group Containers/

Delete these three;  
[UBF8T346G9.ms](http://ubf8t346g9.ms/ "http://ubf8t346g9.ms/")  
UBF8T346G9.Office  
UBF8T346G9.OfficeOsfWebHost

then restart office