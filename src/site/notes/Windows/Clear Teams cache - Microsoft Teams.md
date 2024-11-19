---
{"dg-publish":true,"permalink":"/windows/clear-teams-cache-microsoft-teams/","title":"Clear Teams cache - Microsoft Teams","tags":["clippings","public"],"noteIcon":"1","created":"2024-11-14T12:29:22.136+01:00","updated":"2024-11-19T11:50:05.124+01:00"}
---


> [!NOTE] Camera not working in teams
If teams repeatedly prompts for Camera rights in Privacy settings even thoug it is already enabled, this is the fix!


#### Delete the files

1. If Teams is still running, right-click the Teams icon on the taskbar, and then select **Quit**.
2. Open the **Run** dialog box by pressing the Windows logo key ![](https://learn.microsoft.com/en-us/microsoftteams/troubleshoot/teams-administration/media/clear-teams-cache/windows-logo-key.png) +R.
3. In the **Run** dialog box, enter the following path, and then select **OK**.

Console 

```
%userprofile%\appdata\local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams
```
4. Delete all files and folders in the directory.
5. Restart Teams.