---
{"dg-publish":true,"permalink":"/programmering/powershell-notes/powershell-error-handling-with-external-commands/","tags":["public"],"noteIcon":"1","created":"2023-08-15T14:20:13.000+02:00","updated":"2023-01-17T01:05:23.000+01:00"}
---

#powershell 
### about
When using external tools/commands with powershell directly, error handling is not super straight forward. Either use "Invoke-expression" or similar (does not 100% of the time though) or use $LASTEXITCODE wich is what I have found most reliable.

> [!WARNING]
> `$LASTEXITCODE ` does not reset itself automaticallyupon a successful command in all cases, especially in loops etc. so the variable needs to be reset after one itteration, or just make sure to reset it before each time a command runs. 
> (this is not best practive by microsoft, but `$LASTEXITCODE ` lacks a lot of documentation and it is not "forbidden" to write to this variable, so it is the best way I ahve found to manage this.)


### examples
- Uses try catch block to wrap it so that you can also include multiple commands in the block
```powershell
try{
	"Mounting overlayfs..."
	# Reinitialize ExitCode before calling external command
	$global:LASTEXITCODE = 0
	mount -t overlay o   #this is the external tool being called
	if($LASTEXITCODE -ne 0){throw ""}
}catch{
	$internalerrorflag=$true
	write-error "Error running external command overlay mount!"
}
```
- Can also be called for single command with out try catch
```powershell
# Reinitialize ExitCode before calling external command
$global:LASTEXITCODE = 0
mount -t overlay o   #this is the external tool being called
if($LASTEXITCODE -ne 0){write-error "KABOOM!"}
```