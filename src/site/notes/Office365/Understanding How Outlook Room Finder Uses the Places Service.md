---
{"dg-publish":true,"permalink":"/office365/understanding-how-outlook-room-finder-uses-the-places-service/","tags":["public"],"noteIcon":"1"}
---

#office365 #powershell #outlook 
source: [Understanding How Outlook Room Finder Uses the Places Service](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/)
![Microsoft Outlook](/img/user/attachments/Microsoft_Outlook.jpg)

Outlook Room Finder uses the Places service to find free conference rooms available in your organization’s building. Here’s what you need to know about how it works.

Table of Contents \[[hide](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#)\]

-   [What is the Outlook Room Finder?](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#What_is_the_Outlook_Room_Finder)
-   [What is the Outlook Places service?](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#What_is_the_Outlook_Places_service)
    -   [The role of the OWA Room Finder](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#The_role_of_the_OWA_Room_Finder)
    -   [Supported platforms](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Supported_platforms)
-   [What information uses the Places Service?](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#What_information_uses_the_Places_Service)
    -   [Room mailboxes](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Room_mailboxes)
        -   [What’s the difference with workspaces?](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#What8217s_the_difference_with_workspaces)
    -   [Room lists](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Room_lists)
        -   [Using room lists to mirror a building layout](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Using_room_lists_to_mirror_a_building_layout)
    -   [Floor plans](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Floor_plans)
-   [The importance of metadata for improving suggestions](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#The_importance_of_metadata_for_improving_suggestions)
    -   [Room equipment and geo-coordinates](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Room_equipment_and_geo-coordinates)
    -   [How updating metadata works](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_updating_metadata_works)
-   [How the Outlook Room Finder works](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_the_Outlook_Room_Finder_works)
    -   [How to get a list of rooms](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_to_get_a_list_of_rooms)
    -   [How room suggestions work](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_room_suggestions_work)
    -   [How to search for a room by name](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_to_search_for_a_room_by_name)
    -   [Using filters to find rooms](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Using_filters_to_find_rooms)
        -   [Find a room by specifying a room type](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Find_a_room_by_specifying_a_room_type)
        -   [How to find current room availability](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_to_find_current_room_availability)
    -   [How can I create availability information?](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#How_can_I_create_availability_information)
-   [Conclusion](https://petri.com/deep-dive-understanding-how-outlook-room-finder-uses-the-places-service/#Conclusion)

## What is the Outlook Room Finder?

Over the years, the various iterations of what we refer to as ‘Outlook’ have gotten better at helping users schedule meetings. The importance of this post is to describe how the engineering teams behind Outlook have made considerable progress around reserving conference rooms and equipment.

Microsoft has been adding new features for years and has kept meeting scheduling enhancements on the roadmap. The [**Outlook Room Finder**](https://docs.microsoft.com/en-us/outlook/troubleshoot/calendaring/room-finder) was built specifically to assist users in locating appropriately sized and equipped conference rooms and equipment nearby geographically. You can use Outlook on the Web, the Outlook desktop app, and the Outlook mobile app!

Where does the Outlook Room Finder grab its information from? One moment…

## What is the Outlook Places service?

Microsoft released the Places Service [back at the end of 2019](https://insider.office.com/et-ee/blog/location-suggestions-in-outlook-for-windows) to help facilitate the discovery of meeting locations with room mailboxes. The ‘suggested calendar locations’ feature at the time was the genesis and laid the groundwork for more recent innovations like Room Finder.

The Places Service uses the details and metadata (when you add it) of [**room mailboxes**](https://docs.microsoft.com/en-us/exchange/recipients/room-mailboxes?view=exchserver-2019) as the main source of information about locations. Administrators can update metadata using the [**PowerShell ‘Set-Place’**](https://docs.microsoft.com/en-us/powershell/module/exchange/set-place?view=exchange-ps) cmdlet including city, country, building, capacity, and other equipment (screens, projectors, Surface Hubs, etc.). You’ll learn more about how this works later on.

### The role of the OWA Room Finder

The Outlook Web App (OWA) Room Finder is part of [Microsoft’s ‘One Outlook’ vision](https://petri.com/microsoft-revamps-outlook-one-outlook-vision/). It was first released to Outlook on the Web (like many features) because the engineering teams can ship production code faster to the web. Features then start to roll out to the Outlook desktop app, Outlook mobile, etc.

As part of Microsoft’s ‘One Outlook’ initiative, the Outlook desktop app now actually uses the ‘OWA Room Finder’ code using the Edge WebView2 runtime. As you may recall, this [started to roll out to all computers](https://petri.com/microsoft-to-push-edge-webview2-runtime-to-pcs/) running Microsoft 365 desktop apps last year.

### Supported platforms

The Outlook Room Finder is currently available on various Outlook clients including Outlook on the Web and the Outlook desktop app. The Outlook mobile clients also utilize these features. Eventually, sometime this year (hopefully), the One Outlook application, also [codenamed “Project Monarch”](https://petri.com/one-outlook-project-monarch/) will also support this functionality.

## What information uses the Places Service?

### Room mailboxes

The first items that we’ll discuss that use the Places Service are **room mailboxes**. These are special mailboxes in Exchange Online that incorporate custom attributes to allow for a schedulable meeting.

You can create a room mailbox using the [Exchange Admin Center](https://docs.microsoft.com/en-us/exchange/exchange-admin-center). Just expand **Recipients** and click on **Resources**. Then, click **Add a resource**.

![Adding the 'Sunnygrove Conference Room' using the Exchange Admin Center](/img/user/attachments/Adding_the_'Sunnygrove_Conference_Room'_using_the_Exchange_Admin_Center.png)

Adding the ‘Sunnygrove Conference Room’ using the Exchange Admin Center

#### What’s the difference with workspaces?

A **[workspace](https://docs.microsoft.com/en-us/exchange/troubleshoot/outlook-issues/create-book-workspace-outlook)** is a variation of a room mailbox. It is meant to describe other spaces to work including a hotel space, an individual cubicle, and small offices to temporarily inhabit. You’ll need to use PowerShell to utilize workspaces using the Set-Mailbox cmdlet. I’ll show this later on, too.

### Room lists

To make the Room Finder shine, you’ll want to create a **[room List](https://docs.microsoft.com/en-us/exchange/recipients/room-mailboxes?view=exchserver-2019#create-a-room-list)**, which is a special distribution list for rooms and workspaces. Each room list contains room mailboxes, ideally in the same building (or city).

That way, when a user is scheduling a meeting with the need for conference space, they can select a building (room list), and all available conference rooms (room mailboxes) will be displayed. As of this writing, PowerShell is your only option for creating and working with room lists.

#### Using room lists to mirror a building layout

Let me take you through an example here. I have created a few conference rooms (room mailboxes) in my developer Microsoft 365 tenant.

![Here are our four new conference rooms](/img/user/attachments/Here_are_our_four_new_conference_rooms.png)

Here are our four new conference rooms

Boulder and Sunset are in Milwaukee, and Sunnygrove and Tropical are in Chicago. Let’s create two room lists, one for Milwaukee and one for Chicago.

New\-DistributionGroup -Name "Milwaukee Conference Rooms" -RoomList

New\-DistributionGroup -Name "Chicago Conference Rooms"\-RoomList

New-DistributionGroup -Name "Milwaukee Conference Rooms" -RoomList New-DistributionGroup -Name "Chicago Conference Rooms"-RoomList

New-DistributionGroup -Name "Milwaukee Conference Rooms" -RoomList
New-DistributionGroup -Name "Chicago Conference Rooms"-RoomList

![Adding the new "Milwaukee Conference Rooms" room list](/img/user/attachments/Adding_the_new_!Milwaukee_Conference_Rooms!_room_list.png)

Adding the new “Milwaukee Conference Rooms” room list

![Adding the new "Chicago Conference Rooms" room list](/img/user/attachments/Adding_the_new_!Chicago_Conference_Rooms!_room_list.png)

Adding the new “Chicago Conference Rooms” room list

Now, we need to add our 4 conference room mailboxes to these lists. More PowerShell to the rescue!

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Boulder Conference Room"

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Sunset Conference Room"

Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Sunnygrove Conference Room"

Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Tropical Conference Room"

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Boulder Conference Room" Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Sunset Conference Room" Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Sunnygrove Conference Room" Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Tropical Conference Room"

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Boulder Conference Room"
Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member "Sunset Conference Room"
Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Sunnygrove Conference Room"
Add-DistributionGroupMember -Identity "Chicago Conference Rooms" -Member "Tropical Conference Room"

![Adding the new conference rooms to the room lists](/img/user/attachments/Adding_the_new_conference_rooms_to_the_room_lists.png)

Adding the new conference rooms to the room lists

Note – It often will take 24 hours or more after creating room lists and populating them with members before the Room Finder will see the new information!

### Floor plans

Another note that may help some organizations – Workplaces also support **[floor plans](https://docs.microsoft.com/en-us/microsoftsearch/manage-floorplans)** to assist people to find a location they’ve booked. Floor plans are available in the Calendar feature in Outlook and can be found in Microsoft Search. The floor plans and their locations are configured via the Search & intelligence section of the Microsoft 365 admin center.

![Utilizing Floor Plans in the Microsoft 365 admin center](/img/user/attachments/Utilizing_Floor_Plans_in_the_Microsoft_365_admin_center.png)

Utilizing floor plans in the Microsoft 365 admin center

## The importance of metadata for improving suggestions

The default attributes included in room mailboxes allow users to schedule meetings. However, the Room Finder is most useful when additional metadata is made available to it.

Instead of populating ALL user and room mailboxes with the additional mailbox properties needed here, Microsoft instead opted to create a separate store to manage location metadata and other attributes.

### Room equipment and geo-coordinates

The metadata in Outlook Places can include room equipment and geographic locations. You could include custom features that are suited to your business such as a conference room requiring badge access, or if it is equipped for large, catered meals. Other equipment could include a Surface Hub or Teams Rooms devices.

Just a reminder, using geocoordinates is used with floor plans above. You can visit [this link](https://docs.microsoft.com/en-us/microsoftsearch/manage-floorplans) to learn more about how to set this up in your organization.

### How updating metadata works

You use the Set-Place cmdlet to populate this additional information in room mailboxes. Let me demonstrate.

Set-Place -Identity "Boulder Conference Room" -Building "HQ" -Floor 2

Set-Place -Identity "Sunset Conference Room" -Building "HQ" -Floor 2

Set-Place -Identity "Sunnygrove Conference Room" -Building "Downtown" -Floor 1

Set-Place -Identity "Tropical Conference Room" -Building "Downtown" -Floor 1

Set-Place -Identity "Boulder Conference Room" -Building "HQ" -Floor 2 Set-Place -Identity "Sunset Conference Room" -Building "HQ" -Floor 2 Set-Place -Identity "Sunnygrove Conference Room" -Building "Downtown" -Floor 1 Set-Place -Identity "Tropical Conference Room" -Building "Downtown" -Floor 1

Set-Place -Identity "Boulder Conference Room" -Building "HQ" -Floor 2
Set-Place -Identity "Sunset Conference Room" -Building "HQ" -Floor 2
Set-Place -Identity "Sunnygrove Conference Room" -Building "Downtown" -Floor 1
Set-Place -Identity "Tropical Conference Room" -Building "Downtown" -Floor 1

![Viewing the Places metadata in our conference rooms](/img/user/attachments/Viewing_the_Places_metadata_in_our_conference_rooms.png)

Viewing the Places metadata in our conference rooms

## How the Outlook Room Finder works

### How to get a list of rooms

Administratively, you can use PowerShell to determine all the room mailboxes in your tenant.

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | fl DisplayName, RecipientTypeDetails

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | fl DisplayName, RecipientTypeDetails

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | fl DisplayName, RecipientTypeDetails

![Viewing all our room mailboxes / conference rooms](/img/user/attachments/Viewing_all_our_room_mailboxes_!_conference_rooms.png)

Viewing all our room mailboxes / conference rooms

Of course, you can display more pertinent info to our discussion by including the Places metadata including city, building, and floor.

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | Sort DisplayName | Get-Place | ft DisplayName,City,Building,Floor

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | Sort DisplayName | Get-Place | ft DisplayName,City,Building,Floor

Get-EXOMailbox -RecipientTypeDetails RoomMailbox | Sort DisplayName | Get-Place | ft DisplayName,City,Building,Floor

![Displaying more detailed metadata in our conference rooms](/img/user/attachments/Displaying_more_detailed_metadata_in_our_conference_rooms.png)

Displaying more detailed metadata in our conference rooms

### How room suggestions work

When the Outlook Room Finder is utilized, it first checks for the last building you selected thinking it plausible that you’d use a similar conference room now. If the user has not used one previously, the Room Finder will display the first 20 rooms in your tenant.

These ‘suggestions’ are not geographic and not specific to a location. Machine Learning or AI are definitely not used in retrieving this list.

### How to search for a room by name

When creating a meeting, click in the ‘Search for a room or location field. If you happen to know the names of conference rooms nearby, you can start typing in their name, and Outlook should suggest an appropriate (and available) conference room. Room Finder utilizes the metadata previously entered and the current free/busy information in your conference rooms (room mailboxes) to make accurate suggestions.

![Searching conference rooms by name](/img/user/attachments/Searching_conference_rooms_by_name.png)

Searching conference rooms by name

### Using filters to find rooms

Users can use filters to find rooms appropriate to their location and how equipped various conference rooms are. Items such as projectors, screens, video conference devices, etc. can be filtered in the Room Finder experience.

#### Find a room by specifying a room type

If you are utilizing **workspaces**, you’ll be able to specify a room type in the Room Finder. You’ll be able to choose between conference room and workspace. Let’s go ahead and create a workspace.

New\-Mailbox -Room "Colorado Space" | Set-Mailbox -Type Workspace

New-Mailbox -Room "Colorado Space" | Set-Mailbox -Type Workspace

New-Mailbox -Room "Colorado Space" | Set-Mailbox -Type Workspace

Next, we’ll use the Set-Place cmdlet to add some more metadata.

Set-Place -Identity "Colorado Space" -City "Milwaukee" -Floor 2 -Building "HQ"

Set-Place -Identity "Colorado Space" -City "Milwaukee" -Floor 2 -Building "HQ"

Set-Place -Identity "Colorado Space" -City "Milwaukee" -Floor 2 -Building "HQ"

![Viewing the metadata for our Workspace](/img/user/attachments/Viewing_the_metadata_for_our_Workspace.png)

Viewing the metadata for our Workspace

The (almost) last step is to add the new workspace to an existing room list.

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member ColoradoSpace@x3v6p.onmicrosoft.com

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member ColoradoSpace@x3v6p.onmicrosoft.com

Add-DistributionGroupMember -Identity "Milwaukee Conference Rooms" -Member ColoradoSpace@x3v6p.onmicrosoft.com

![Adding our Workspace to the "Milwaukee Conference Rooms" room list](/img/user/attachments/Adding_our_Workspace_to_the_!Milwaukee_Conference_Rooms!_room_list.png)

Adding our Workspace to the “Milwaukee Conference Rooms” room list

Finally, let’s enforce the capacity limits of the workspace and set a minimum booking duration for the workspace to three hours.

Set-CalendarProcessing "Colorado Space" -EnforceCapacity $True -MinimumDurationInMinutes 180

Set-CalendarProcessing "Colorado Space" -EnforceCapacity $True -MinimumDurationInMinutes 180

Set-CalendarProcessing "Colorado Space" -EnforceCapacity $True -MinimumDurationInMinutes 180

![Verifying the calendaring availability features in our Workspace](/img/user/attachments/Verifying_the_calendaring_availability_features_in_our_Workspace.png)

Verifying the calendaring availability features in our Workspace

#### How to find current room availability

As long as you’ve taken care of the ‘working hours’ for your conference rooms, Outlook will only make suggestions for meeting times by taking into account everyone’s free/busy information. When setting up your meeting, the key items to add are the participants and the length of the meeting. Don’t worry about the actual time, yet.

Outlook will utilize the meeting length time, the participants, and the potential conference rooms/workspaces to make suggested meeting dates and times. Now that all the new room lists, conference rooms, workspaces have been processed by all the necessary background processes in Microsoft 365, let’s see how all this works now when scheduling a new meeting.

First, I’ll create a new meeting in Outlook on the Web, fill in the title, some attendees, and set the length to one hour.

![Creating a new meeting in Outlook](/img/user/attachments/Creating_a_new_meeting_in_Outlook.png)

Creating a new meeting in Outlook

Now, as this meeting will take place in Milwaukee, let’s set the **Building** to ‘Milwaukee’ and we’ll see our new room list, ‘Milwaukee Conference Rooms.’ I’ll click that.

![There's our new room list - "Milwaukee Conference Rooms"!](/img/user/attachments/There's_our_new_room_list_-_!Milwaukee_Conference_Rooms.png)

There’s our new room list – “Milwaukee Conference Rooms”!

Now that the new room list has been processed, you can see that we can choose between our new conference rooms.

![And there are our new conference rooms as members of said room list](/img/user/attachments/And_there_are_our_new_conference_rooms_as_members_of_said_room_list.png)

And there are our new conference rooms as members of said room list

We can choose either the Boulder or Sunset conference rooms. And, as you can see, the capacity and features are listed for our convenience.

So, let’s say we have 10 guests to accommodate. If I bump up the Capacity to 10, you’ll notice the ‘Boulder Conference Room’ disappears from the list dynamically as it only has a capacity for eight attendees.

![After filtering to rooms with at least 10 attendee capacity, only the Sunset Conference Room will foot the bill](/img/user/attachments/After_filtering_to_rooms_with_at_least_10_attendee_capacity,_only_the_Sunset_Conference_Room_will_fo.png)

After filtering to rooms with at least 10 attendee capacity, only the Sunset Conference Room will foot the bill

Next, if I go to Features and select ”Video”, now the Boulder conference room is missing as it doesn’t have those capabilities.

![After filtering for rooms with Video capabilities, Sunset Conference Room is our pick](/img/user/attachments/After_filtering_for_rooms_with_Video_capabilities,_Sunset_Conference_Room_is_our_pick.png)

After filtering for rooms with Video capabilities, Sunset Conference Room is our pick

And, why don’t we touch on Workspaces. If I wanted to reserve a Workspace for the day, I can change the ‘Type’ field to Workspace and there’s our ‘Colorado Space’ ready to choose.

![After we change the type to workspace, we can choose our "Colorado Space" workspace in Milwaukee](/img/user/attachments/After_we_change_the_type_to_workspace,_we_can_choose_our_!Colorado_Space!_workspace_in_Milwaukee.png)

After we change the type to workspace, we can choose our “Colorado Space” workspace in Milwaukee

### How can I create availability information?

In order to keep all your resources’ availability accurate, you’ll want to double-check the working hours and time zone information for your conference rooms. First, verify their current settings using the [Get-MailboxCalendarConfiguration](https://docs.microsoft.com/en-us/powershell/module/exchange/get-mailboxcalendarconfiguration?view=exchange-ps) command

Get-MailboxCalendarConfiguration -Identity "Boulder Conference Room"

Get-MailboxCalendarConfiguration -Identity "Boulder Conference Room"

Get-MailboxCalendarConfiguration -Identity "Boulder Conference Room"

![Viewing the calendar configuration for "Boulder Conference Room"](/img/user/attachments/Viewing_the_calendar_configuration_for_!Boulder_Conference_Room.png)

Viewing the calendar configuration for “Boulder Conference Room”

We’re going to need to update the time zone and the working hours using Set-MailboxCalendarConfiguration. We’ll change the time zone to Central and the start time to 7:00 AM.

Set-MailboxCalendarConfiguration -Identity "Boulder Conference Room" -WorkingHoursTimeZone "Central Standard Time" -WorkingHoursStartTime 07:00:00

Set-MailboxCalendarConfiguration -Identity "Boulder Conference Room" -WorkingHoursTimeZone "Central Standard Time" -WorkingHoursStartTime 07:00:00

Set-MailboxCalendarConfiguration -Identity "Boulder Conference Room" -WorkingHoursTimeZone "Central Standard Time" -WorkingHoursStartTime 07:00:00

![We've updated the Start Time and Time Zone for our conference room...](/img/user/attachments/We've_updated_the_Start_Time_and_Time_Zone_for_our_conference_room.png)

We’ve updated the start time and time zone for our conference room…

## Conclusion

The Outlook Room Finder is an extremely helpful and useful feature for your users, especially as ‘hybrid mode’ becomes more prevalent in the workplace throughout 2022. However, out of the box, a lot of these settings are missing, making the Room Finder not so helpful. Hopefully, this guide gives you a great jumpstart into this feature to boost the efficiency and end-user experience for your employees.

Incidentally, another very welcome feature is coming to Outlook – [RSVP enhancements for meetings](https://www.microsoft.com/en-us/microsoft-365/blog/2021/09/09/brace-yourselves-hybrid-work-is-hard-heres-how-microsoft-teams-and-office-365-can-help/). When accepting a meeting request, you’ll be able to click Yes, and then choose ‘Virtually’ or ‘In Person.’ This is scheduled to be released to Outlook on the Web sometime in the 2nd quarter of 2022.
