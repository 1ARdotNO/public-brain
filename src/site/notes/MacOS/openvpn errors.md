---
{"dg-publish":true,"permalink":"/mac-os/openvpn-errors/","tags":["vpn","macos"],"noteIcon":"1"}
---

(fITG
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