
# Data Dictionary

This document describes the spreadsheet configuration columns supported by CrewTimer.  The first section defines the required columns while the following section describes optional columns.

## Required Headers

| Field Name      | Acceptable Aliases                                | Description                                                                                                 |
| --------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Event&nbsp;Num  | Event&nbsp;#, &nbsp;EventNum,&nbsp;Event&nbsp;No. | The event number associated with the event.  Usually a number but can also include alpha such as 2A and 2B. |
| Event&nbsp;Name | Event, EventName, Description                     | The name of the event.  E.g. Mens Varsity 8+ or Mixed Masters 4x-.                                          |
| Crew            |                                                   | The name of the crew                                                                                        |
| Bow             | Bow #                                             | The bow number associated with the provided Crew name                                                       |

## Optional Headers

Optional headers can be used to further define a regatta and are most often shown on the web results view.

| Field Name        | Acceptable Aliases | Description                                                                                                                                                                                                                                                                                                                                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Event&nbsp;Abbrev | EventAbbrev        | An abbreviation for the event name.  E.g. MJV8+.  CrewTimer will create it’s own abbreviation if none provided.  Abbreviations are shown on the mobile app buttons.'                                                                                                                                                                                                       |
| Event&nbsp;Time   | Start              | Approximate clock time the event should start                                                                                                                                                                                                                                                                                                                              |
| Event&nbsp;Info   | EventInfo          | Specify additional information to show on the results page for this event.  If Progression column is not present it can also specify a progression algorithm.                                                                                                                                                                                                              |
| Crew&nbsp;Abbrev  |                    | An abbreviation for the Crew name.                                                                                                                                                                                                                                                                                                                                         |
| Stroke            |   Cox              | Informational item shown on results page.                                                                                                                                                                                                                                                                                                                                  |
| Day               |                    | The Day to show for multi-day regattas. E.g Saturday, Sunday or Day 1, Day 2                                                                                                                                                                                                                                                                                               |
| RaceType          |                    | 'Sprint', 'Head' or 'Info'.   'Sprint' and 'Head' indicate the type of timing. 'Info' declares an informational item in the schedule such as a break or lunch.   This allows a regatta with mixed Time Trials (head timing) and Sprint races. If unspecified, the global setting in the admin control for the regatta is used. Requires mobile app version 5.0.7 or later. |
| Combine           |                    | Specifies an event number to combine with for a sprint start.  For example 3 shells from events '2' and '3' are started together as lanes 1-3 and 4-6.  Specify '2' for the Combine column of events '2' and '3'.  If event 4 also should be included, specify '2' for event '4' for as well.  Leave blank if not a combination event.                                     |
| Status            |                    | Can flag entries as Scratch, Exhibition, DNS, DNF, DQ, Exclude.  These can only be cleared by clearing the entry in the spreadsheet.                                                                                                                                                                                                                                       |
| Progression       |                    | Specifies a progression algorithm to use with the [CrewTimer Progression Engine](https://admin.crewtimer.com/help/Progressions).                                                                                                                                                                                                                                           |
| Note              |                    | Ignored by CrewTimer                                                                                                                                                                                                                                                                                                                                                       |

## Handicaps

Handicaps can be automatically computed by CrewTimer or they can be manually assigned in your spreadsheet.  In either case an Age column is required.   When ‘Manual’ handicaps is specified in your regatta configuration, the Handicap column is used to assess the handicap adjustment.  If USRowing is selected as the handicap method then the Handicap column is ignored and CrewTimer calculates the USRowing handicap based on the specified age.  Other handicap types operate similarly.

**Note:** CrewTimer needs a hint as to the boat type to properly compute handicaps.  When using handicaps, be sure to include the boat type in the Event Name.  For example 1x, 2x, 2-, 4x, 4-, 4+, 8+, 8.

| Field Name | Acceptable Aliases            | Description                                                                                                                                                                     |
| ---------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Event Name | Event, EventName, Description | Event name with boat type included (1x, 2x, 2-, 4x, 4-, 4+, 8+, 8). Canadian handicaps should also include the gender (W4+, M4+, Mx4+, 'Mens 8+', 'Womens 8+', 'Mixed 8+', etc) |
| Age        | Avg_Age,&nbsp;Avg&nbsp;Age    | Average age of the entry.                                                                                                                                                       |
| Handicap   |                               | When manual handicaps are configured for a regatta, this column represents the handicap associated with this entry.  Specified as seconds of handicap advantage.                |
| Handicap Multiplier |  | A race specific handicap multiplier.  If a particular race or set of races have a different distance than the default specified in the admin configuration, the distance factor can be adjusted on a per race basis by specifying a handicap factor. Typically 1.0 represents a 1km distance. |

## Time only or Exhibition entries

Entries that are racing for time only and are not eligible for placement can be indicated as exhibition by using one of the following:

1. Place ‘Exhib’ or Exhibition in the Age column of your regatta definition.
2. Asses an ‘Exhib’ penalty via the mobile app

## Regatta Central Lineups

Regatta Central lineups can be downloaded directly from Regatta Central and imported into CrewTimer.   To integrate this spreadsheet with CrewTimer, follow the following steps:

1. Download your boats.xls file from Regatta Central.  Staff -> Quick Links -> Data Files
2. Import boats.xls into Google Drive
3. Right click on boats.xls and select 'Open with Sheets'.  This will convert it into a Google Sheets spreadsheet instead of an excel spreadsheet.
4. Edit your spreadsheet as desired and add bow numbers for all your entries.  If a bow number is not specified, CrewTimer will choose a number starting at 600 as a temporary number.
5. Share your document and paste the sharing url into CrewTimer.

If you download the RegattaMaster spreadsheet instead of the Generic form from RegattaCentral it will work as long as you insure the 'boats' sheet is first in the list of sheets.  The following additional header names are supported for import of Regatta Central lineups:

| Field Name                                 | CrewTimer Equivalent |
| ------------------------------------------ | -------------------- |
| Description                                | Event&nbsp;Name      |
| Event                                      | Event&nbsp;Num       |
| Avg&nbsp;Age                               | Age                  |
| Boat&nbsp;Label                            | Stroke               |
| Invoiced&nbsp;Club&nbsp;(Common&nbsp;Name) | Crew                 |
| Invoiced&nbsp;Club&nbsp;(Abbreviation)     | Crew&nbsp;Abbrev     |
| Club                                       | Crew                 |
| Bow/Lane#                                  | Bow                  |
| Team_Common                                | Crew                 |
| Team_Abbreviation                          | Crew Abbrev          |
| Bow_Lane_ID                                | Bow                  |

The 'Event Time (final)' column from RC represenets both a date (for multi day regattas) and time.  To utilize this column with CrewTimer, proceed as follows:

1. Change column title to 'Event Time'.
2. For a multi-day regatta, duplicate the column values and title as 'Day'.
3. Format the 'Event Time' column to show just the time by selecting the entire column and then Format->Number->Custom date and time->13:25 or 1:25PM
4. Format the 'Day' column (if present).  Format->Number->Custom date and time.  Select a format similar to what you want and edit the format as desired.  e.g. Tuesday.
