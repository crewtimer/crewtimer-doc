# Legacy Kiosk Mode and Live Stream Support

**Note: This page documents the legacy livestream support in CrewTimer.  New users of livestream are encouraged to use the new [Livestream Overlay](https://crewtimer.com/help/LiveStream) capability.**

## Kiosk Mode

The CrewTimer results page supports a ‘kiosk’ mode which can be used to present results on a big screen or a tablet.  **Kiosk mode is entered by appending /kiosk to the regatta results URL**.  Kiosk mode removes all menus and options for navigation and will automatically scroll to the event with the most recent finish timestamp.  As new results arrive, the display will scroll to insure the most recent event is visible.

### iPad Kiosk Mode

If an iPad is used, it can be configured for kiosk mode by making a few setup changes.  The iPad can be mounted securely and allow viewers to scroll and see results without being able to access iPad settings or hardware buttons such as power, home, or volume.  This can be particularly useful when the spectator viewing area is not near the finish line results area.  To use iPad in kiosk mode:

1. When viewing results in kiosk mode in Safari, select the bookmark icon and select ‘Add to Home Screen’.  You may need to scroll the options to the left to see ‘Add to Home Screen’.  When this bookmark is subsequently used to view the regatta, the usual Safari navigation bar is removed.
2. In settings, turn on guided access.  Choose General/Learning/Guided Access (toward bottom of options).  When an app is placed in guided access mode, the hardware buttons are locked out so people cannot change apps or settings.   Set a passcode you can remember.
3. View the regatta results using the home screen CrewTimer icon.  Triple click the home button to activate Guided Access and select Start.
4. To exit Guided Access, triple click the home button again and enter your passcode.

## Live Stream Support

CrewTimer assists with livestreaming annotations by providing control of green screen presentation colors as well an elapsed timer for an event.  **For best results it is recommended to use the Event filter to show a single event at once so the position on the screen is fixed.**

When showing results, certain columns can be omitted from presentation by configuring them in the admin console.  Changing the window width can also eliminate columns and make it more compact.

![Live Stream Example](https://storage.googleapis.com/resources.crewtimer.com/images/LiveStreamPlainsRegatta.png)

### Green Screen

* Results presentation can be augmented with green backgrounds by appending /green to the results url - [https://www.crewtimer.com/regatta/r12071/green](https://www.crewtimer.com/regatta/r12071/green).
* Applying an alpha of 90% is effective in creating a results overlay for split times.
* Chroma key values for background colors in CrewTimer are f5f5f5 by default and 008000 when /green is utilized.

**Be sure to only select a single Event using the Event Filter selector**

![Example Green Screen](https://storage.googleapis.com/resources.crewtimer.com/images/LiveStreamGreenExample.png)

### Elapsed running time

An elapsed running time for a race is available by appending /elapsed to a results url: [https://www.crewtimer.com/regatta/r12071/elapsed](https://www.crewtimer.com/regatta/r12071/elapsed).  This can [also be combined with /green](https://www.crewtimer.com/regatta/r12071/elapsed/green).

The elapsed time will be 0.0 when a race has not started and will blank when at least one entry has finished.

The presentation of the elapsed running time can be configured with the following optional url parameters.

| Parameter    | Description                        | Example                 |
| ------------ | ---------------------------------- | ----------------------- |
| elapsedBg    | rgb background color               | 080 or 008000 for green |
| elapsedColor | The rgb text color of elapsed time | fff or ffffff for white |
| elapsedSize  | The font size of the elapsed text  | 16, 32, 64              |

* Color annotations do not include #
* Arguments are preceded by the ? symbol
* Arguments are separated by the & symbol
* Font size can be further controlled with browser zoom
* The width of the screen can be used to make a compressed view

Example: [https://www.crewtimer.com/regatta/r12071/elapsed?elapsedBg=ff0&elapsedColor=f00&elapsedSize=32](https://www.crewtimer.com/regatta/r12071/elapsed?elapsedBg=ff0&elapsedColor=f00&elapsedSize=32)

### Live Stream Test Regatta

As shown in the examples above the r12071 'Live Stream Test Regatta' can be used for testing.  The first four events present a variety of situations which can be useful for testing before the event.  Just replace r12071 with the regatta id for your regatta before going live.

### Livestreaming with OBS Studio

To utilize [OBS Studio](https://obsproject.com/) with CrewTimer results overlay, follow these steps:

1. Open the desired URL you want in Chrome. E.g. [https://www.crewtimer.com/regatta/r12071/green](https://www.crewtimer.com/regatta/r12071/green). For kiosk mode, also append /kiosk.
2. Optional - make a web app: Right click the three menu dots in Chrome, select More Tools -> Create Shortcut. Check open as window.
3. In OBS Studio, add a window capture video source to a scene and specify the CrewTimer results window.
4. Right Click the source in OBS and select filter. Add a Color Key filter with Custom Key color #008000 or green.
5. If not using /green for background, use  #f5f5f5 and also add similarity 1 and smoothness 1.
6. Set Opacity 90% for a slight see-through style.
7. Use the results filter to select a single event.
