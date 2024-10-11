# CrewTimer FinishLynx Connect

On this page:
<!-- TOC -->

- [CrewTimer FinishLynx Connect](#crewtimer-finishlynx-connect)
  - [Introduction](#introduction)
  - [Installing CrewTimer FinishLynx Connect](#installing-crewtimer-finishlynx-connect)
  - [FinishLynx Configuration](#finishlynx-configuration)
  - [Operation Notes](#operation-notes)
  - [Synchronizing Time](#synchronizing-time)
  - [Alternatives to FinishLynx Comm Port plugin](#alternatives-to-finishlynx-comm-port-plugin)

## Introduction

CrewTimer supports timing generated from FinishLynx software connected to FinishLynx cameras.
Communication between the FinishLynx application and CrewTimer cloud is provided by a plugin which
receives updates from FinishLynx via the ScoreBoard module of FinishLynx.  To use this
integration, the following is needed:

- Computer running FinishLynx
- FinishLynx Network Comm Port option.  An alternative reported to work is [Virtual Serial Ports Emulator](https://eterlogic.com/Downloads.html) or the free version of the [Virtual Serial Ports](https://freevirtualserialports.com/) utility. See more details below for use of alternate Serial Port emulation.
- CrewTimer FinishLynx Connect PC application

Once the CrewTimer FinishLynx Connect application has been installed, it is configured with
your CrewTimer mobile ID and pin in much the same way that mobile apps are configured.  In
addition, the user can specify where to place FinishLynx configuration files.

For a quick overview see the [CrewTimer FinishLynx Connect video](https://www.youtube.com/watch?v=633Bw2ub20Q).

## Installing CrewTimer FinishLynx Connect

- Download the CrewTimer FinishLynx Connect Installer from the [Downloads Page](https://admin.crewtimer.com/help/Downloads).
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
When switching events in FinishLynx, the changes are immediately available.  However, events that are currently open will not receive changes.

## Synchronizing Time

Built in time synchronization is not always reliable on Windows PCs.  Time is often 'off' even when it claims to be synchronized.

To ensure your PC time is properly syncyronized, CrewTimer recommends use of [Speedsoft Time Sync](https://www.speed-soft.de/software/time_sync/index.php).

Once this is installed and running:

- Open a web browser to [nist.gov](https://nist.gov) and compare the time to your computer time.
- Compare the time shown on the CrewTimer mobile app to your computer time.

## Alternatives to FinishLynx Comm Port plugin

Times in FinishLynx are normally communicated via a 'scoreboard' interface which sends results via a COM port.  By using the FinishLynx Network Comm port option the
connection can be done via a TCP/IP connection from FinishLynx to CrewTimer FinishLynx Connect.

If the Network Comm port option is not available, a Virtual Comm Port can be used.

1. Download the [Virtual Serial Ports Emulator](https://eterlogic.com/Downloads.html) from eterlogic.com.  The 32 bit version is free, the 64 bit version is $24.95 lifetime.  The 64 bit version can be used for 30 days to try it out.
2. Run the Virtual Serial Port Emulator.
3. Create a 'Connector' on a free Comm port and note the Comm port number.
4. Create a TCP Client connecting to 127.0.0.1.  Change the default 0 port number to 5000 (The same as the CrewTimer FinishLynx Connect port setting).  *Be careful not to write the port in the TCP Console Textbox*
5. Keep control point @ null and finish.
6. Start emulation by clicking the Play button.
7. Create the Scoreboard in FinishLynx but instead of 127.0.0.1 select the Comm port established above.
8. Test with CrewTimer.
