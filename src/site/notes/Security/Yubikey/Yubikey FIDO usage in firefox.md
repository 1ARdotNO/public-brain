---
{"dg-publish":true,"permalink":"/security/yubikey/yubikey-fido-usage-in-firefox/","tags":["public"],"noteIcon":"1"}
---


### about
In firefox yubikey using [[FIDO\|FIDO]] with PIN ([[Concepts/CTAP2\|CTAP2]]) is not supported by default.
THis causes issues when trying to authenticate to a service that requires this.
The window either errors out or just "hangs"
The fix for this is to enable some settings in [[Firefox\|Firefox]]´s `about:config`

### Implementation

open about:config in the address bar in [[Firefox\|Firefox]]
Search for webauth, and set these 2 keys to true (the default is false)
```
security.webauthn.ctap2 = true
security.webauth.u2f = true
```

