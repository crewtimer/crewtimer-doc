# CrewTimer FinishLynx Connect

On this page:
<!-- TOC -->

- [CrewTimer FinishLynx Connect](#crewtimer-finishlynx-connect)
  - [Introduction](#introduction)
  - [Installing CrewTimer FinishLynx Connect](#installing-crewtimer-finishlynx-connect)
  - [FinishLynx Configuration](#finishlynx-configuration)
  - [Operation Notes](#operation-notes)
  - [Release Notes](#release-notes)
    - [Version 1.0.11](#version-1011)
    - [Version 1.0.10](#version-1010)
    - [Version 1.0.9](#version-109)
    - [Version 1.0.8](#version-108)
    - [Version 1.0.7](#version-107)
    - [Version 1.0.6](#version-106)
    - [Version 1.0.5](#version-105)
    - [Version 1.0.4](#version-104)
    - [Version 1.0.3](#version-103)
    - [Version 1.0.2](#version-102)

## Introduction

CrewTimer supports timing generated from FinishLynx software connected to FinishLynx cameras.
Communication between the FinishLynx application and CrewTimer cloud is provided by a plugin which
receives updates from FinishLynx via the ScoreBoard module of FinishLynx.  To use this
integration, the following is needed:

- Computer running FinishLynx
- FinishLynx Network Comm Port option.  An alternative reported to work is the free version of the [Virtual Serial Ports](https://freevirtualserialports.com/) utility.
- CrewTimer FinishLynx Connect PC application

Once the CrewTimer FinishLynx Connect application has been installed, it is configured with
your CrewTimer mobile ID and pin in much the same way that mobile apps are configured.  In
addition, the user can specify where to place FinishLynx configuration files.

For a quick overview see the [CrewTimer FinishLynx Connect video](https://www.youtube.com/watch?v=633Bw2ub20Q).

## Installing CrewTimer FinishLynx Connect

- Download the [CrewTimer FinishLynx Connect Installer](https://storage.googleapis.com/resources.crewtimer.com/installers/CrewTimer%20FinishLynx%20Connect%20Setup%201.0.11.exe)
- Run the installer.  If a previous version is running you will be prompted to remove it during installation.

## FinishLynx Configuration

1. Run CrewTimer FinishLynx Connect and enter your race credentials
2. Specify the FinishLynx Folder to match your FinishLynx Database Input Directory setting, usually c:\\Lynx.  This will place a CrewTimer.lss scoreboard file into the specified folder.  This file is used by the ScoreBoard module in FinishLynx.  Verify the FinishLynx configuration as follows:
   - Open File/Options/Database in FinishLynx.
   - Ensure Data Source 'Files' is checked.
   - Note the location of the Input Directory.
   - Enter the same directory location in CrewTimer Connect.
3. Start or Restart FinishLynx (v12.10 or later)
4. Set up Scoreboard
   - Create New Scoreboard
      - Script: CrewTimer.lss
      - Serial Port: Network(connect)
      - Port: 5000
      - IP Address: 127.0.0.1 if CrewTimer connect running on same machine
      - Running Time: Off
      - Results:
          - Auto
          - Uncheck Paging
          - Options - checkmark 'Always send place'.  Needed for DNS, DNF support.
          - Time Precison: thousandths
5. Restart FinishLynx to start scoreboard
6. Load any CrewTimer lineup changes 'File/Goto Event' and clicking the 'Load Schedule' button.

## Operation Notes

CrewTimer will create a Lynx.evt file which has all of the events defined in CrewTimer cloud.  In
addition, it also creates an 'All Entries' event that consists of all entries.  The 'All Entries' event may be useful
for head races where races are continuously running to avoid switching between events.

When typing in a bow number, the operator can use just the bow number in most cases.  To associate a bow
number with a particular event, prefix the bow number with the event number.  For example 4-3 indicates Event 4, Bow 3.
This can be used when focused on a single event but a boat appears that is from a different event.  Just prefix the
appropriate event onto the bow number and proceed.

When lineups are changed in CrewTimer cloud, CrewTimer FinishLynx Connect will also refresh it's Lynx.evt and Lynx.sch files.
However, for FinishLynx to pick up any changes the operator must select 'Load Schedule' from the Goto Event Dialog or restart FinishLynx.

## Release Notes

### Version 1.0.11

- Added tooltip for creation of custom flight from regex.

### Version 1.0.10

- Allow using a regex to specify combined FinishLynx events.  This allows multiple events to be timed with one FL event.

### Version 1.0.9

- Allow quote characters in event name
- Update internal tooling
- Support Manual and RadioLynx starts
- Add support for Day selection
- Replace CrewTimer.lss if outdated
- Support DNF, DNS, DQ, and Scratch from FinishLynx 'Set Status' right click

### Version 1.0.8

- Improve formatting of Status page

### Version 1.0.7

- Improve Time Trial support

### Version 1.0.6

- Add support for 'All Events' FL Event

### Version 1.0.5

- Internal Test Release

### Version 1.0.4

- Add support for persistent window size, location, and selected tab

### Version 1.0.3

- Add support for sprint starts
- Add support for mixing time trial starts (head race timing) with sprint starts per event

### Version 1.0.2

- First public release
