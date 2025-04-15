---
{"dg-publish":true,"permalink":"/office365/copy-named-location/","tags":["public","office365","azuread"],"noteIcon":"1"}
---



### about
Sometimes you want to make a copy of a list of named locations for conditional access policies and remove or add some things to that copy. This describes how to make that duplicate that you can then modify

### Script


```powershell
# Make a copy

import-module azuread

$source=Get-AzureADMSNamedLocationPolicy -PolicyId "id of you original policy"

New-AzureADMSNamedLocationPolicy -DisplayName "new policy name" -CountriesAndRegions @($eea.CountriesAndRegions | ForEach-Object {"$_"}) -OdataType "#microsoft.graph.countryNamedLocation"
```

```powershell
# modify aanother

import-module azuread

$source=Get-AzureADMSNamedLocationPolicy -PolicyId "id of you original policy"

set-AzureADMSNamedLocationPolicy -PolicyId "id of you other policy" -CountriesAndRegions @($eea.CountriesAndRegions | ForEach-Object {"$_"}) -OdataType "#microsoft.graph.countryNamedLocation"
```

