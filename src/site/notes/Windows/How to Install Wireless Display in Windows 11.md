---
{"dg-publish":true,"permalink":"/windows/how-to-install-wireless-display-in-windows-11/","tags":["public","windows","miracast"],"noteIcon":"1","created":"2024-08-03T14:52:57.650+02:00","updated":"2023-06-02T14:38:07.000+02:00"}
---


 
 
![wireless display install command prompt successfull ](https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/11/wireless-display-install-command-prompt-successfull-1.jpg)
 
 You can also install Wireless Display using the Command Prompt. To install the app, you can use the Features on Demand(FODs) command in the command-line utility.
 
 To install Wireless Display with the Command Prompt:
 
 1.  Press the **Win** key and type **cmd**.
 2.  From the search results, right-click on **Command Prompt** and select **Run as administrator.**
 3.  In the Command Prompt window, type the following command and press Enter:
     
      `DISM /Online /Add-Capability /CapabilityName:App.WirelessDisplay.Connect~~~~0.0.1.0` 
     
 4.  Windows will download and install the **Wireless Display** app. This process may take some time, so wait till the progress bar reaches 100%.
 5.  When you see a success message, close the Command Prompt window, and restart your PC.
