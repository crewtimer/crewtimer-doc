# Tracking Station Support

Tracking station support provides a mechanism to track non timing related activity of entries in the regatta.  For example, a regatta might want to track when boats are launched so a starter can determine if all expected boats for a race are on the water.

Example tracking stations for a regatta might be as follows:

- Launch
- Starter Check-in
- Recovery

It is also possible to track other activity such as post race boat weight or pre-race coxswain weigh-in.

CrewTimer provides two mechanisms to view tracking activity:

- Tracking bubbles on the bottom of Bow Buttons in the mobile app
- A tracking web page showing tracking information

## Configuring Tracking Stations

Tracking stations are configured in the admin website in the detail configuration page under the *Tracking Stations* section.

There are two properties associated with each Tracking Station:

| Property | Description |
| - | - |
| Name | The name of the Tracking Station.  This shows up on the tracking website as well as the mobile user interface.|
| Require Number Checkbox | When checked the mobile interface will allow entering a number when recording tracking and the number will also be shown on the tracking website.  Typically this is a weight. |

## Recording Tracking Activity

>**CrewTimer Mobile -> Settings -> Station Type**

The CrewTimer mobile app allows choosing a station type under the Settings menu.  Usually this menu allows choosing between Timing, Penalties, and Timing+Penalties. 

When Tracking Stations are defined in the admin interface they can be selected on the **Station Type** menu selection.

After a Tracking Station has been chosen as the station type, tracking events are recorded by two different gestures:

- **Double Tap a bow number**
- **Long press a bow number**

Once a tracking event has been recorded it can be deleted by pressing the trash can or modified by tapping the event in the timing history.

## Viewing Tracking Activity

### Bow Bubbles
Each tracking station shows up on the bottom of each bow button as a bubble.  When a time for a tracking station has been recorded the bubble will turn green.

>The order of the bubbles match the order shown in the admin panel.

### Tracking website

The other view for tracking stations is available from the results website by selecting the upper right menu and clicking on Tracking.

Each Tracking Station is shown as a column with the time shown when the entry was tracked.  If the station requires a number to be entered, it is shown along with the time.
