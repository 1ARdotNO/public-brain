---
{"dg-publish":true,"permalink":"/mac-os/munkireport/","tags":["public","munki","azuread","saml"],"noteIcon":"1","created":"2023-08-15T14:20:38.000+02:00","updated":"2023-06-02T14:38:07.000+02:00"}
---




### notes

##### FIDO error
You might encounter an error relating to FIDO when using yubikey or similar to authneticat with SAML with munkireport.
```error
Message: AADSTS75011: Authentication method 'X509, MultiFactor' by which the user authenticated with the service doesn't match requested authentication method 'Password, ProtectedTransport'.
```
The solution is similar to [[Office365/SSO issue with Slack on Azure AD joined machine\|SSO issue with Slack on Azure AD joined machine]]  
Set the following env on your munkireport server to false (the default is true)
```docker
AUTH_SAML_SECURITY_REQUESTED_AUTHN_CONTEXT=false
```
ref. [SAML authentication · munkireport/munkireport-php Wiki · GitHub](https://github.com/munkireport/munkireport-php/wiki/SAML-authentication#:~:text=AUTH_SAML_SECURITY_REQUESTED_AUTHN_CONTEXT)