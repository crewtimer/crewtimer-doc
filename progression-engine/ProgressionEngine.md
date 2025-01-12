# CrewTimer Progression Engine

<!-- TOC -->

- [CrewTimer Progression Engine](#crewtimer-progression-engine)
  - [Installation](#installation)
  - [Using the add-on](#using-the-add-on)
  - [Event Names](#event-names)
  - [Progression suffixes](#progression-suffixes)
  - [Settings](#settings)
    - [Lane Mappings](#lane-mappings)
    - [Advancement Methods](#advancement-methods)
    - [Distribution Method](#distribution-method)
    - [Seeding Priority](#seeding-priority)
  - [Column Data](#column-data)
  - [References](#references)

<!-- /TOC -->

To facilitate progressions where athletes move from heats to semifinals to finals, _CrewTimer_ provides the [CrewTimer Progression Engine](https://workspace.google.com/marketplace/app/crewtimer_progression_engine/52923439813) add-on for **Google Sheets™** to assist with updating your configuration spreadsheet with results from races to populate placement in subsequent races.

The _CrewTimer Progression Engine_ add-on is used in conjunction with the _CrewTimer Mobile App_ and [CrewTimer Results Website](https://crewtimer.com) to provide race day timing and presentation of results. This is all driven from a spreadsheet utilizing _Google Sheets™_ where lineups for each event along with crew names, bow numbers, and related information is configured in the spreadsheet.

Once updates are made to the spreadsheet the _CrewTimer_ cloud infrastructure is notified to refresh it's configuration from the spreadsheet.

Once the add-on is installed, it provides the following:

- Summary of events in your regatta
- Analysis of your spreadsheet indicating potential issues
- Configuration of progression preferences such as 'Top 3 advance' or 'Top 2 plus 2 best times progress'
- Configuration of lane priorities - best time should be in lane 3 then 4 etc.
- Summary help tips
- Ability to notify \*CrewTimer- cloud to refresh lineups from the spreadsheet
- Quick link to open results and admin websites

A [video tutorial](https://youtu.be/KLHU3zyNCz4) of the CrewTimer Progression Engine is available on youtube.

<iframe id="ytplayer" type="text/html" width="320" height="180" src="https://www.youtube.com/embed/KLHU3zyNCz4" frameborder="0" allowfullscreen></iframe>

## Installation

To add the _CrewTimer Progression Engine_ add-on to your spreadsheet, search for 'CrewTimer Progression Engine' in the marketplace using the _Extensions -> Add-ons -> Get add-ons_ menu found in your spreadsheet. Once you have installed the add-on, look for it to appear as a menu item in the Extensions menu. You can then select the 'Open Sidebar' menu item which will open a sidebar in your document.

## Using the add-on

1. Install the add-on (see above)
2. Define your events and entries for each event. Tag unknown entries with TBD or similar for the crew name. An [example spreadsheet](https://docs.google.com/spreadsheets/d/1zukjxnHsH1Twg47m0xImOoAgvVIgkMYX5M832fhA8fc) is available - use File -> Make a Copy.
3. Tag each event name with a bracket suffix such as H1 for Heat1 and FA for an A final. (see below for a list of suffixes)
4. Wait for preliminary events to finished and be declared official
5. Select one of the preliminary events in the sidebar and review the progresssion plan
6. Click 'Preview Seeding' and review the proposed advancement plan
7. Click 'Apply' if the advancement is suitable, Cancel otherwise
8. Select 'Update Cloud' from the Quick Action menu to notify CrewTimer.com of your changes

You can revert the progression by using either the 'Undo' menu of the spreadsheet or the 'Clear' button in the sidebar for that event.

## Event Names

_CrewTimer Progression Engine_ relies on clues provided in the Event Name column to assist with progressions.

- A suffix indicating the progression level bracket (e.g. H1)
- A common Event Name used in all brackets

An example with two heats and a final:

| Event Name    | Meaning           |
| ------------- | ----------------- |
| M Jr 8+ H1    | Heat 1 of M Jr 8+ |
| M Jr 8+ H2    | Heat 2 of M Jr 8+ |
| M Jr 8+ Final | Final for M Jr 8+ |

## Progression suffixes

The bracket suffixes supported by the _CrewTimer Progression Engine_ are listed below.

| Designation  | Meaning                                 | Alternate Spelling     |
| ------------ | --------------------------------------- | ---------------------- |
| H1..H8       | The race is a Heat                      | 'Heat1', 'Heat 1', etc |
| QAD1..QAD4   | Quarter final for semis SAB1-2, SCD1-2  | 'QF1'...'QF4'          |
| QEH1..QEH4   | Quarter final for semis SEF1-2, SGH1-2  |                        |
| SAB1,SAB2    | Semi Final for Finals A and B           | 'Semi1', 'Semi 1', etc |
| SCD1,SCD2    | Semi Final for Finals C and D           |                        |
| SEF1,SEF2    | Semi Final for Finals E and F           |                        |
| SGH1,SGH2    | Semi Final for Finals G and H           |                        |
| FA,FB, ...   | The race is an A or B final             | 'Final'                |
| Final        | The race is an A final                  |                        |
| TT           | The race is a Time Trial Heat           | 'Time Trial'           |
| TT1, TT2     | There are multiple heats of Time Trials |                        |
| TFA,TFB, ... | The race is a timed final.              | 'Timed Final'          |
| R1..RN       | Repachages (not yet supported)          |                        |
| unspecified  | The race is an A final or has no heats  |                        |

## Settings

The Settings tab allows configuration of settings that apply to all races such as the following:

- Lane Mappings - Specifies Lane priority when assigning lanes in a race
- Advancement Method - Specifies how winners are chosen (Top 3, Top2, etc)
- Distribution Method - Specifies how winners (and losers) are distributed to successive races

### Lane Mappings

Lane mappings establish the priority order in which lanes are assigned. For a 6 lane sprint, this would typicall by from inside to outside with the inside lanes having higher priority. The best performing crews are then placed first into the highest available priority lane. Specifying a setting of '345216' would first assign lane 3 folloed by 4, then 5,2,1 and 6.

### Advancement Methods

The advancement method specifies how 'winners' that advance are determined. This is typicaly something like 'top 2', 'top 3', or 'top 2 plus next 2 best times'. While a number of options are provided by default, you can add your own customization to the list of options.

By default, each race defaults to 'Automatic' advancement which will choose the first advancement method that fills all the entries in the destination bracket(s).

The list of advancement methods can be ordered via drag-and-drop to prioritize the automatic selection. Of course, you can specify the advanement method if automatic does not meet your needs.

**CrewTimer prefers advancement hints to be defined in the Progression column of the spreadsheet**. For example, 'Top 2 + next 2 times to Event 123' would be properly interpreted.

An alternative is to use the **EventInfo** column to specify your progression. If the advancement spec is suitable for general viewing as extra info for an event, this can be a good choice.

Advancements specified in the Progression column take precedence over automatic selection as well as Advancements specified in the EventInfo column.

| Progression (bold is required text, non-bold is optional) | Interpretation                                                                  |
| --------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Top 3** to heats                                        | Places 1-3 to next bracket                                                      |
| **Top 2 + next 2** times advance                          | Places 1-2 plus 2 best times in bracket advance                                 |
| **Top 2 + 2 fastest** times advance                       | Places 1-2 plus 2 best times in bracket advance                                 |
| **1st to Final, next 2** to semi                          | 1st place advances to A final, places 2 and 3 move on                           |
| **Top 2 to Final, next 2** best times advance             | Places 1 and 2 advance to A final and next 2 best times move on to next bracket |
| **6 best times** advance                                  | The top 6 times across heats or semis progress and are seeded by time           |

### Distribution Method

Distribution method pertains to how winners are placed into multiple Heats, Quarter Finals, or Semi Finals. For example, four heats populating 2 semi-final races will alternate between the two semi-final races when doing placement. The distribution method specifies how the alternation is performed. A global default can be defined in the settings tab but race specific values can be specified with a 'Distribution' column.

| Method      | 'Distribution' Spreadsheet Column | Description                                                                                                                                                                                        |
| ----------- | --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reversing   | reversing                         | The races are assigned in definition order in one direction and then reversed back to the first race. For example, for three destination races, the pattern would be 1,2,3, 3,2,1, 1,2,3, 3,2,1... |
| Round Robin | roundrobin                        | The races are assigned in definition order over and over again. For example, for three destination races, the pattern would be 1,2,3, 1,2,3, 1,2,3, 1,2,3...                                       |
| Random      | random                            | The races are assigned randomly. For example, for three destination races, the pattern might be 1,3,2, 1,2,3, 3,1,2, 2,1,3, ...                                                                    |

### Seeding Priority

Seeding priority pertains to how winners are assigned specific lanes in an event. A global default can be defined in the settings tab but race specific values can be specified with a 'Seeding' column.

| Method         | 'Seeding' Spreadsheet Column | Description                                                                                                                                                                                         |
| -------------- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Place Priority | place                        | By default entries are seeded into the next bracket by place priority. First place entries are seeded first followed by others progressed by place. If any entries remain, they are seeded by time. |
| Time Priority  | time                         | All entries in a race are seeded lanes by their finish time regardelss of their place in qualifying events.                                                                                         |

## Ignoring column data when seeding events

Generally, when populating brackets with new entries, existing column data in the row is also copied on the assumption it is related to the entry. If a column should not be copied change the column title to end with underscore. e.g. 'CheckedIn\_' or 'CheckedIn_nocopy'.

## References

- [Example Progression spreadsheet](https://docs.google.com/spreadsheets/d/1zukjxnHsH1Twg47m0xImOoAgvVIgkMYX5M832fhA8fc)
- [CrewTimer Privacy Policy](https://crewtimer.com/privacy)
- [CrewTimer Results](https://crewtimer.com)
- [CrewTimer Admin Access](https://admin.crewtimer.com)
- Abbreviations are specfied in the [World Rowing Rules Appendix R7](https://worldrowing.com/technical/rules/2021-rule-book/).

Document Source: CrewTimerProgressionEngine.md in the crewtimer-apps-script repository.
