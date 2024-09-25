---
{"dg-publish":true,"permalink":"/office365/app-registration-metadata/","tags":["public","office365","azuread"],"noteIcon":"1","created":"2024-08-03T14:52:58.302+02:00","updated":"2023-04-03T17:59:16.000+02:00"}
---

# about
When managing enterprise apps in [[AzureAD\|AzureAD]] there are 2 ways to create and interact with the apps, 
- [[Concepts/Enterprise apps in Azure AD\|Enterprise apps in Azure AD]] 
- [[Concepts/App registration in Azure AD\|App registration in Azure AD]]
Every app can be managed from each option, but depending on how it is created it gives you a diffrent set of options as defaults. Resulting in the need to use some "tricks" to merge functionalities from one to the there in some cases.

## Examples
- DefectDojo requires for the automatic group provisioning to work.
	- [[Office365/App registration metadata#groupMembershipClaims\|App registration metadata#groupMembershipClaims]]
	- [[Office365/App registration metadata#displayname for groupclaims\|App registration metadata#displayname for groupclaims]]

### Useful properties

#### groupMembershipClaims 

```json
// causes only the groupMembershipClaims that is assigned to the application to be pased through to the app on auth.
"groupMembershipClaims": "ApplicationGroup",
```

#### displayname for groupclaims
Under token configuration in app registration, when creating a groups claim, you are able to set the identifying property to send to several values, but the option to use the "cloud_displayname" is not available in the gui for the app registration. 
*Using the sAMAccountname here does not seem to work as expected, it probably only works with groups synced from on-prem that has this property*
![Pasted image 20230314152838.png](/img/user/Office365/attachments/Pasted%20image%2020230314152838.png)
> [!NOTE] 
> names passthrough of cloud-only groups seem to only work with [[Concepts/Enterprise apps in Azure AD\|Enterprise apps in Azure AD]].
> [microsoft ref.](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-group-claims#:~:text=Emit%20group%20name%20for%20cloud%2Donly%20groups)
> 


By changing this property under the `additionalProperties`to `cloud_displayname `you will enable the same functionality as is available for [[Concepts/Enterprise apps in Azure AD\|Enterprise apps in Azure AD]] 
```json
// causes only the groupMembershipClaims that is assigned to the application to be pased through to the app on auth.
"optionalClaims": {
	"idToken": [
		{
			"name": "groups",
			"source": null,
			"essential": false,
			"additionalProperties": [
				"cloud_displayname"
			]
		}
],
```