---
{"dg-publish":true,"permalink":"/office365/sso-issue-with-slack-on-azure-ad-joined-machine/","tags":["public","office365","azuread","slack","saml"],"noteIcon":"1","created":"2024-08-03T14:53:21.519+02:00","updated":"2023-06-02T14:36:03.000+02:00"}
---


### about
When logging into slack you might encounter this error 
```
Message: AADSTS75011: Authentication method 'X509, MultiFactor' by which the user authenticated with the service doesn't match requested authentication method 'Password, ProtectedTransport'.
```
This only happens if the machine is joined to azuread or if FIDO device was used to sign in to Azure/office365 in the browser.

### solution
disable `AuthnContextClassRef` for slack SAML payloads.
This must be done in the slack end of things. 
Go to admin panel, **Settings and Permissions**, **Authentication**, **Change settings** for you SAML.
Then expand "Advanced options"	 and change AuthnContextClassRef to `Don't send this value` 

### explanation
By default this setting in slack is set to `urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport` 
This basically means that slack sends a payload to AAD stating, this user must be signed in with a password. If the user is then instead signed in with passwordless or via the operatingsystem( azuread joined) it will cause this error. 

Chaning this setting to `Don't send this value`  causes slack to not request any specific authentication method from the SAML provider. YOu can instead if you need enforce specific methods in the AAD using [[Conditional Access Policies\|Conditional Access Policies]] 