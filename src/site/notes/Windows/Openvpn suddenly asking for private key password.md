---
{"dg-publish":true,"permalink":"/windows/openvpn-suddenly-asking-for-private-key-password/","tags":["openvpn","windows","ssl","public"],"noteIcon":"1","created":"2024-05-27T16:10:17.439+02:00","updated":"2024-05-27T16:14:53.746+02:00"}
---

After OpenVPN version 2.6.0 the auth mechanism has changed a bit, so clients using a certificate and key that is old, might have a problem where the user is continuosly prompted to enter their "private key password" even if the private key used for the auth does not have a password.

The solution is to add a line to the config file telling openvpn to use the legacy auth mechanism.
Just add the following line in your config file;
```
providers legacy default
```

ref:
[New OpenVPN 2.6.0 Client (Windows 10 64bit) fails to connect - Virtual Private Networks / OpenVPN - IPFire Community](https://community.ipfire.org/t/new-openvpn-2-6-0-client-windows-10-64bit-fails-to-connect/9283/3)
[Suddenly openvpn client asks about private key password. : r/sysadmin](https://www.reddit.com/r/sysadmin/comments/z9miwu/suddenly_openvpn_client_asks_about_private_key/)
[OpenVPN client 2.6.X private key password prompt - Virtual Private Networks / OpenVPN - IPFire Community](https://community.ipfire.org/t/openvpn-client-2-6-x-private-key-password-prompt/10991/9)