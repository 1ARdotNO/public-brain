---
{"dg-publish":true,"permalink":"/mac-os/openvpn-errors/","tags":["vpn","macos"],"noteIcon":"1","created":"2024-08-03T14:55:34.702+02:00","updated":"2024-02-05T11:26:36.000+01:00"}
---

G
If the error 
```
openvpn error calling protected() method on socket
```

The problem is that the `ovpnagent`service is not running
To verify this you can run the following command 
```
ps auxww | grep ovpnagent
```
If you do not see `/Library/Frameworks/OpenVPNConnect.framework/Versions/Current/usr/sbin/ovpnagent `in the results, that means itis not running.

To fix it, go to settings > login items > background tasks, and ensure that Openvpn client is "Checked" 