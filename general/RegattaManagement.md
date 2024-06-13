# Regatta Management

## Before the Regatta

1. Review the video [CrewTimer Mobile Tutorial](https://www.youtube.com/watch?v=5wZ6JfZRbj8&t=3s).
2. Visit [https://admin.crewtimer.com](https://admin.crewtimer.com) to configure your regatta.
3. Create a Google Sheets spreadsheet with your lineups.
4. Set sharing mode of your spreadsheet to ‘anyone with a link’.
5. Copy the link into your regatta configuration.
6. From the admin interface view your regatta results to verify your lineups by selecting the ‘Results’ action.  This url can be used to view the results at any time.
7. Install the CrewTimer Android app onto Start and Finish tablets.  Visit the play store to verify you do not have an app update available.
8. Test entering start times and finish times from your tablets.
9. When testing is complete, select ‘Clear Race Data’ from the admin interface.  The CrewTimer mobile app will clear local timing data withing 30 seconds.
10. Make sure your tablets are fully charged and have 3G/4G access or have a reliable hotspot which can be used.

## Day of Regatta

1. Make any last minute changes to your lineups.
2. Select ‘Refresh Lineups’ from the admin interface after any changes are made.
3. Verify the lineups appear properly on both the web results page and on the tablets.
4. Train timing assistants on use of the mobile app.
5. Record a time for each waypoint in turn.  Verify it shows up on website. Perform the ‘Clear Race Data’ admin action to erase test timers.  The CrewTimer mobile app will clear local timing data within 30 seconds.

## Going Live

1. Perform the  ‘Clear Race Data’ admin action from the web interface.
2. Configure the regatta to be publicly visible from the admin interface.  This will allow the regatta to show up on [https://www.crewtimer.com](https://www.crewtimer.com) to all users.

## During the Regatta

1. Update the spreadsheet to reflect new entries or changes to the lineup.  Any entry which has not been started can be updated.
2. Select ‘Refresh Lineups’ from the web admin interface after any changes are made.  Changes are shown immediately on the website and within 30-60 seconds on tablets.

## After the Regatta

1. Visit [https://admin.crewtimer.com](https://admin.crewtimer.com) and select the ‘Finished’ checkbox.  This will prevent any accidental updates from the tablets.
2. Clear the regatta ID on each tablet and uncheck [www.crewtimer.com](www.crewtimer.com) integration.

## Tablet Tips

* Use a separate tablet for recording Start and Finish Times.
* When the mobile app starts it asks for you to choose your position as either Start or Finish.  **Timers should verify the tablet matches their position**.
* CrewTimer synchronizes with government time servers to insure accurate results and synchronization between tablets.  Results are recorded as time of day.
* Times are stored locally on each tablet in persistent storage and are maintained if the app is restarted or if the tablet loses power.
* The mobile app will show yellow or red background on times which have not been communicated to the cloud.

## Backup Timing

Since CrewTimer records all times both locally on the tablet and in the cloud, backup timing needs come into play in several situations:

* A tablet is lost, dropped into the water, or becomes inoperable.
* An operator misses recording a time.
* An operator knows they were either early or late.

In the latter two cases it is possible to 'estimate' a time correction in some cases where finish times are within the margin of error for the estimation.  In cases where
the times need to be more accurate, Backup Timing Waypoints should be used (see below).

### Considerations

* Mobile devices are extremely reliable and are not prone to failure unless abused.  Reports of a phone or tablet spontaneously ‘breaking’ while in use is unheard of but should be considered in a worst case scenario.  The purpose of a backup timing system is to prevent collapse of the regatta and backup timing may not be required to be as accurate or timely as using CrewTimer.  Keep in mind the most important element is to retain the relative elapsed time of shells in each event.  Backup systems should be simple and easily communicated.
* CrewTimer is hosted on Google servers so will always be available if Internet access is available.
* CrewTimer uses time of day for event timing so any backup system can utilize time of day for recording times.

## What can go wrong

While CrewTimer attempts to prevent most sources of error, it is possible that you may encounter issues caused by user error or new user knowledge being insufficient.  Issues in the heat of the moment can be very stressful.  The following list shows some situations you may encounter.

| Problem | Solution |
| - | - |
| No Finish times | Turn off 'Hide Finish till Official' on the regatta configuration page. |
| No Finish times | Finish tablet is configured for Start (the default).  Fixing times already recorded requires using adjust results to find the correct finish time and pasting it into the finish box.  Marking the errant Start as ignored. Knowing bow finish order may be helpful. |
| Regatta credentials don't work | typo. Erase and very carefully enter again.  Even then it's easy to make the same mistake once it's in your head incorrectly.|
| Manually updated bow shows up on wrong event |  Double check the 'Event' field on the mobile device for that timestamp. |
| My numbers are red and not showing up on website | Reestablish your Internet connection, possibly by using a phone as hotspot. |
| Clickers no longer work | The Start and Finish clickers were swapped at some point and then distributed.  Unpair clicker (long press till fast blink, single click) and reconnect with tablet on Bluetooth CrewTimer menu. |
| My times are always provisional |  Use Adjust Results to mark an event official or configure a tablet for 'Timing+Penalties' with the Finish waypoint and use the Official button. |
| Late entry was timed that wasn't on lineups.  Bow was manually entered/created on the fly. | Edit spreadsheet to add bow and refresh lineups. |

In a pinch, you can also call CrewTimer at +1-425-405-0576.

### Recommendations

#### Proctect the tablet

* If tablets are used in a launch, they should be placed into a zip lock bag for protection.  The touch interface still works when placed into a zip lock bag.
* Provide each timing position with a Portable Battery Pack to charge tablets if they run low.

#### Add Backup Timing Waypoints

Add Start2 and Finish2 waypoints with their own mobile devices.  This provides a second set of eyes and record of times.  Start2 and Finish2 times can be selected for use in place of Start and Finish times in the web admin interface for 'Adjust Results'.  The times can also be manually typed into the Start and Finish tablets.  Remember, the tablets themselves retain all times that are entered in non-volatile storage.  This scenario retains the benefits of accurate and timing and has minimal overhead.

#### Use Stopwatches

This is the traditional backup method for timing.  However, use of stopwatches requires synchronization and figuring out mapping of splits to shells can be problematic unless they are are recorded in real time.  For this reason, use of backup waypoints is preferred as a backup solution.  CrewTimer does however support entry of stopwatch splits in the 'Adjust Results' admin interface.

## Kiosk Mode

The CrewTimer results page supports a ‘kiosk’ mode which can be used to present results on a big screen or a tablet.  **Kiosk mode is entered by appending /kiosk to the regatta results URL**.  Kiosk mode removes all menus and options for navigation and will automatically scroll to the event with the most recent finish timestamp.  As new results arrive, the display will scroll to insure the most recent event is visible.

### iPad Kiosk Mode

If an iPad is used, it can be configured for kiosk mode by making a few setup changes.  The iPad can be mounted securely and allow viewers to scroll and see results without being able to access iPad settings or hardware buttons such as power, home, or volume.  This can be particularly useful when the spectator viewing area is not near the finish line results area.  To use iPad in kiosk mode:

1. When viewing results in kiosk mode in Safari, select the bookmark icon and select ‘Add to Home Screen’.  You may need to scroll the options to the left to see ‘Add to Home Screen’.  When this bookmark is subsequently used to view the regatta, the usual Safari navigation bar is removed.
2. In settings, turn on guided access.  Choose General/Learning/Guided Access (toward bottom of options).  When an app is placed in guided access mode, the hardware buttons are locked out so people cannot change apps or settings.   Set a passcode you can remember.
3. View the regatta results using the home screen CrewTimer icon.  Triple click the home button to activate Guided Access and select Start.
4. To exit Guided Access, triple click the home button again and enter your passcode.

