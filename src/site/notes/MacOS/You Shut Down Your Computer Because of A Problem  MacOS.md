---
{"dg-publish":true,"permalink":"/mac-os/you-shut-down-your-computer-because-of-a-problem-mac-os/","tags":["public","macos","intel","t2"],"noteIcon":"1","created":"2023-08-15T14:20:47.000+02:00","updated":"2023-02-18T19:36:59.000+01:00"}
---


If you have [forcibly shut down your Mac](https://iboysoft.com/wiki/mac-force-shutdown.html) due to unresponsiveness or other problems, it makes sense to see the error "You shut down your computer because of a problem." However, it seems strange to receive the warning when your Mac is turned off as you normally have.

![Get the warning You shut down your computer because of a problem](/img/user/attachments/Get_the_warning_You_shut_down_your_computer_because_of_a_problem.jpg)

### Delete the responsible log file

You may not notice, but many macOS processes are working in the background.

By deleting this report, you can avoid "You shut down your computer because of a problem" from reappearing.

1.  Open Finder and click Go > Go to Folder from the top menu bar.
2.  Copy and paste the following path to the search box and hit Enter./Library/Logs/DiagnosticReports/
3.  Type "sleep" in the top-right search bar.
4.  Look for a file named Sleep Wake Failure that was created recently.![Delete Sleep Wake Failure log file](/img/user/attachments/Delete_Sleep_Wake_Failure_log_file.jpg)
5.  Right-click on the file and choose " Move to Trash."
6.  Shut down your Mac.
7.  Turn on your Mac after 30 seconds.


 


sources: [[Solved] You Shut Down Your Computer Because of A Problem 2022](https://iboysoft.com/howto/you-shut-down-your-computer-because-of-a-problem.html)