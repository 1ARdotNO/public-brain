---
{"dg-publish":true,"permalink":"/office365/opsgenie-active-on-call-to-aad-security-group/","tags":["public","office365","opsgenie","azuread"],"noteIcon":"1"}
---


### about
This is a script that can be helpful in on-call situation if you need to assign particular rights to the person on-call, but who is not not needed in their regular duties.
Setup on-call schedules in opsgenie, add the schedule id to the uri in the script, and define what AAD group you want it to add the user to.
Then use that group to grant the permissions needed in your services, also 3rd party services work if you have SSO/SAML/groups sync functionality.


> [!NOTE] needs offic365 credentials to be provided in `$o365cred` and an opsgenie API key with Config read permissions to be set in `$ENV:opsgenie`
```powershell
##The purpose of this job is to automatically populate the sec_on-call-active group in office365 that automatically assigns a set of permissions to the person who is currently on-call

#connect to azure
connect-azuread -credential $o365cred
 

#Call opsgenie to determine who is currently on-call

$params = @{
	'Uri' = "https://api.opsgenie.com/v2/schedules/SCHEDUELEID/on-calls"
	'Headers' = @{'Authorization' = 'GenieKey ' + $ENV:OPSGENIE }
	'Method' = 'get'
	'ContentType' = 'application/json'
}

$opsgenieresult=Invoke-RestMethod @params
$oncallemails=$opsgenieresult.data.onCallParticipants.name

$group=Get-Azureadgroup -SearchString sec_on-call-active


#add members to group
$oncallemails | ForEach-Object {
$usertoadd=Get-AzureADUser -ObjectId $_
if( $_ -notin (Get-AzureADGroupMember -ObjectId $group.objectid).userprincipalname){
	"adding $($usertoadd.displayname) to group"
	Add-AzureADGroupMember -ObjectId $group.objectid -RefObjectId $usertoadd.ObjectId

}else{
	"user $($usertoadd.displayname) already a member of group"
}

}

#remove any members not in the list
Get-AzureADGroupMember -ObjectId $group.objectid | ForEach-Object {
	if($_.userprincipalname -notin $oncallemails){
		"removing $($_.displayname) from group"
		Remove-AzureADGroupMember -ObjectId $group.objectid -MemberId $_.objectid
	}

}

  
  

Disconnect-AzureAD
```