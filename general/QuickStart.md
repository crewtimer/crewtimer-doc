# CrewTimer QuickStart

## CrewTimer Resources

Watch these videos to get started with CrewTimer:

- [CrewTimer Overview](https://youtu.be/qVsdQYN4Uzg)

- [Sprint Race CrewTimer Volunteer Timer Tutorial by John Corelli](https://www.youtube.com/watch?v=efWTV3J3GiM)
- [Head Race CrewTimer Volunteer Timer Tutorial by John Corelli](https://www.youtube.com/watch?v=j_WCOiJDS-Q)

- [CrewTimer Mobile App Tutorial](https://www.youtube.com/watch?v=5wZ6JfZRbj8)
- [CrewTimer Admin Tutorial](https://www.youtube.com/watch?v=RQEBX74VSVE)

- [CrewTimer Progression Engine Tutorial](https://youtu.be/KLHU3zyNCz4)

Browse past issues of the CrewTimer newsletter:

- [CrewTimer Newsletter](https://us14.campaign-archive.com/home/?u=4a5ea7fa5d69fb8cc530b0951&id=fe2b98d0cf)

## CrewTimer Worksheets

- [Bow Order Worksheet](https://drive.google.com/file/d/1-Zrq7jEETN6hrCVI2zRltQwAW1dWmT3r/view?usp=sharing) - Useful for recording finish order while timing
- [Penalty Worksheet](https://drive.google.com/file/d/1-S_SVyIWP2OlKJfX7JpF7TPhrQWeQpyj/view?usp=sharing) - Record history of penalties to insure none are missed

## QuickStart Process

1. View the [overview video](https://youtu.be/qVsdQYN4Uzg).
2. In a hurry? Skip the next two videos but come back later and watch them as they have important  details that will help you run a successful regatta.
3. View the [Mobile App Tutorial](https://www.youtube.com/watch?v=5wZ6JfZRbj8)
4. View the [Admin Tutorial](https://www.youtube.com/watch?v=RQEBX74VSVE)
5. Visit the [CrewTimer Admin Site](https://admin.crewtimer.com)
6. Register and/or sign in
7. Click the + icon to add a new regatta
8. Configure your regatta and use the demo spreadsheet or configure your own spreadsheet.
9. Note your Mobile PIN and save your configuration
10. Note your Mobile ID from your regatta summary
11. Install the CrewTimer app on your Android device
12. In settings, enable <www.crewtimer.com> integration
13. Enter your Mobile ID and Mobile PIN
14. Start timing your regatta!

## Step by Step Getting Started

### Create Your Regatta

Once you log in you'll see a list of your regattas. To configure a new regatta, click on the '+' icon and set your desired Regatta Name, Date, and other fields. One of the fields is Google Doc URL which is a link to a Google spreadsheet which describes your regatta.

The best way to get started is to begin with a copy of the example spreadsheet (choose file-> make a copy):

- [CrewTimer example Head or Sprint race](https://docs.google.com/spreadsheets/d/1K2UWYS9Vfb4HlHtMGRi5pGRWj4CM9ZrKNbWo58vdvh4/edit?usp=sharing)

Also available is a French version and manual provided by Bruno Pommiez:

- [CrewTimer exemple pour REGATES ou PCM](https://docs.google.com/spreadsheets/d/1OAHqU631r0Pa-UqAQUdxxnLrJ_YjSajtlcIvvTj2394/edit?usp=sharing)
- [Mémo tablette CrewTimer](https://drive.google.com/file/d/1DZvooqkDjxM8e1h9bcT_6BZrzABY0LV0/view?usp=sharing)

Once you open one of these spreadsheets, select File/Make a Copy to start your own spreadsheet.  Delete or change rows to suit your needs.  Additional columns are OK and are ignored by CrewTimer.  If you have an Excel spreadsheet you can import this into Google Sheets and start from that as well.  The column headings should match the headers in the example sheets which are further described in the CrewTimer Data Dictionary link above.  The minimum set is:

- Event Num, Event Name, Crew, Bow

If you have a requirement to use a different header name for spreadsheet columns please let CrewTimer know as some header aliases are allowed.  e.g. 'Start' for 'Event Time' or 'Event No.' or 'Event #' for 'Event Num', etc.  As noted below, the download format from Regatta Central is also supported.

### Connect your Spreadsheet

To connect your Google Sheet to CrewTimer, a share link is copied from your spreadsheet and pasted into your regatta configuration.  To make the spreadsheet available to CrewTimer, select the Share icon in the upper right of your Google Sheet, then select Get Shareable Link, then select 'Anyone with the link can view'.

Copy the share URL and paste into your regatta configuration page as your Google Doc URL.  This url is a private URL known only to you and CrewTimer.  It does not give CrewTimer or anyone else permission to modify your spreadsheet.

The first time you save a configuration with a Google Doc URL CrewTimer will retrieve the spreadsheet and configure your regatta events. CrewTimer will not update it's lineup configuration unless you explicitly request the spreadsheet to be refreshed. This is done by selecting the 'Refresh Linups' action from the regatta list page.
To validate your setup, select the 'Results' option from the action list for your regatta.

## Configure the CrewTimer mobile app

If you haven't done so already, download the CrewTimer app from the Play Store or App Store by searching for 'CrewTimer'.  Once you have the CrewTimer app loaded you'll need to enable the CrewTimer.com integration features:

1. Select Settings/Regatta Menu and check the Enable <www.CrewTimer.com> integration option.
2. For credentials, enter the Mobile ID shown on your regatta list page. e.g. abcd.efgh
3. Enter the Mobile PIN shown on your regatta configuration page.
4. Exit Settings

The mobile app will contact <www.CrewTimer.com> and download the configuration of your regatta.  If you made a mistake on the Mobile ID or PIN, go back to settings and correct it.

## Other Features

- Use the Clear Race Data action to restart your regatta timing data from scratch.  Use this if you tested your mobile devices before the regatta and need to erase any time events.
- Check the 'Public Visible' option to make your regatta visible to anyone on the Internet.  Without this checked, only you can see the results.
- Users viewing the results from the Internet will see results updated immediately so no need to 'refresh' to get new results.
- PDF results are available for printing or archive by using the Chrome browser and printing the page.  From there select Save as PDF or Save to Google Drive.

## Regatta Central download

CrewTimer supports the spreadsheet format produced by the generic spreadsheet downloaded from Regatta Central as boats.xls.  To integrate this spreadsheet with CrewTimer, follow the [Regatta Central Lineups](/help/DataDictionary#regatta-central-lineups) section of the [Data Dictionary](/help/DataDictionary)

## Masters Handicaps

CrewTimer supports three Masters Handicap types as selected on the regatta configuration page:

- None - No handicap is applied for any entries.
- Manual - A column labeled handicap is applied to entries that also have an age specified.  The handicap is specified in seconds as a positive number that will be subtracted from the elapsed time of the entry.
- US - Handicaps will be applied to all entries that specify an age >= 27 using the formula specified by USRowing.  Entries with an age less than 27 will not have a handicap applied.

If you need a different handicap system applied, please contact CrewTimer with the details of your handicap system.

## Support

- Email [info@crewtimer.com](mailto:info@crewtimer.com?subject=CrewTimer)
- Phone Glenn at 425-405-0576
