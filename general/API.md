# CrewTimer Admin API

The CrewTimer Admin API is used to create, update, and manage a regatta thru request messages.  Each request message is directed to a micro service handler based on a microservice seletor (the 'op' field).

<!-- TOC -->

- [CrewTimer Admin API](#crewtimer-admin-api)
  - [Target URL](#target-url)
  - [Services](#services)
  - [Authentication](#authentication)
  - [Example payloads](#example-payloads)
    - [Create a regatta service](#create-a-regatta-service)
    - [Refresh lineups service](#refresh-lineups-service)
    - [Update service](#update-service)
      - [Entries update](#entries-update)
      - [Example update JSON](#example-update-json)
    - [Clear timing data service](#clear-timing-data-service)
    - [Clear mobile timing data service](#clear-mobile-timing-data-service)
    - [Delete a regatta service](#delete-a-regatta-service)
    - [Set Entry Status service](#set-entry-status-service)
  - [Configuration Fields](#configuration-fields)
  - [Other Services](#other-services)
    - [QR Code mobile app settings](#qr-code-mobile-app-settings)
      - [Optional JSON Properties](#optional-json-properties)
      - [QR Code Testing](#qr-code-testing)

<!-- /TOC -->
Each micro service provides a different admin function regarding operation of the regatta.  This allows verbs such as 'create' and 'delete' as well as actions such as 'refresh', 'clear', and 'update'.

- API operations utilize an http POST request with JSON encoded payloads and responses.
- Authentication is done via the JSON message body and requires no special headers. API requests without authentication will fail.
- All API requests must be made over HTTPS. Calls made over plain HTTP will fail.

## Target URL

CrewTimer has both a production server and a development test server.  When testing the API, the development server should be used.

| Purpose     | API URL                                                                        | Admin GUI Access                                                   |
| ----------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
| Development | [https://dev.crewtimer.com/api/regatta](https://dev.crewtimer.com/api/regatta) | [https://admin.dev.crewtimer.com](https://admin.dev.crewtimer.com) |
| Production  | [https://crewtimer.com/api/regatta](https://crewtimer.com/api/regatta)         | [https://admin.crewtimer.com](https://admin.crewtimer.com)         |

## Services

| Service op  | Description                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| create      | Create a CrewTimer regatta                                                                                   |
| refresh     | Refresh lineups for a regatta from a configuration URL.  Not used if 'entries' provided in create or update. |
| update      | Update lineups from the provided configuration                                                               |
| clear       | Clear all timing data and start regatta from scratch                                                         |
| clearmobile | Clear timing history from mobile devices. Existing timing data is retained                                   |
| delete      | Delete a regatta                                                                                             |

## Authentication

Every service request must provide the following fields:

| field   | description                                                                                                                                | example                                                                                                           |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| op      | Determines the service to invoke                                                                                                           | create, refresh, update, clear, clearmobile, delete                                                               |
| email   | The email address associated with your CrewTimer account                                                                                   | <expert-timing@example.com>                                                                                       |
| uid     | A unique identifier provided by CrewTimer to help authenticate your api access                                                             | ptfXcSdwB3YcZ2u8LFUJO6VF2Fs1                                                                                      |
| config  | Configuration details about the regatta.  See table below for details                                                                      |                                                                                                                   |
| entries | An optional array of entries detailing the regatta lineups if url-fetching is not used. This can also be provided with the update service. | ```[{ EventNum: '1', Event: 'Mens 8+', Crew: 'ERA', Bow: '1' },{ Crew: 'PRC', Bow: '2' }]```. See below for more. |

## Example payloads

### Create a regatta service

The following 'config' fields can be set by the create service.  These fields can also be updated indivually or as a group using the 'update' service.

| field      | description                                                                                                                           | example                                                                                                                        |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| title      | The regatta title                                                                                                                     | ```"title" : "AnyTown Demo Regatta"```                                                                                         |
| info       | An informational field shown on the results page header                                                                               | ```"info" : "Some optional descriptive info shown on results page"```                                                          |
| date       | The date of the first day of the regatta                                                                                              | ```"date" : "2019-03-16"```                                                                                                    |
| RaceType   | The default race type if not specified in lineups.  Can be 'Sprint' or 'Head'.                                                        | ```"RaceType" : "Sprint"```                                                                                                    |
| MobilePin  | The mobile pin to use for full access in the mobile app.  If not specified when creating a regatta one will be assigned by CrewTimer. | ```"MobilePin" : 12345```                                                                                                      |
| MobilePins | Additonal mobile pins used to lock the mobile UI into a specific station type                                                         | ```"MobilePins" : [ { "pin": "11111", "stationType": "Penalties" }, { "pin": "33333", "stationType": "Timing+Penalties" } ]``` |
| url        | An optional url to query for csv data representing lineups                                                                            | ```"url" : "https://someplace-on-the-internet-with-lineup-csv"```                                                              |

Example JSON:

```json
{
    "op" : "create",
    "email" : "glenne@engel.org",
    "uid" : "ptfXcSdwB3YcZ2u8LFUJO6VF2Fs1",
    "config" : {
        "title" : "AnyTown Demo Regatta",
        "info" : "Some optional descriptive info shown on results page",
        "date" : "2019-03-16",
        "RaceType" : "Sprint",
        "url" : "https://someplace-on-the-internet-with-lineup-csv",
        "MobilePins" : [
            { "pin": "11111", "stationType": "Timing" },
            { "pin": "22222", "stationType": "Penalties" },
            { "pin": "33333", "stationType": "Timing+Penalties" }
        ]
    }
}
```

Response

```json
{
  "config" : {
    "mobileId" : "r10000",
    "mobilePin" : "27543",
    "status" : "OK"
    }
}
```

Curl example:

```sh
curl https://dev.crewtimer.com/api/regatta --request POST \
 -H "Content-Type: application/json" \
 --data '{
  "op":"create",
  "email" : "youremail@gmail.com",
  "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
  "config" : {
    "title" : "API TEST",
    "info" : "50th Annual Spiffy Regatta",
    "date" : "2021-05-01",
    "RaceType" : "Sprint",
    "url" : "https://docs.google.com/spreadsheets/d/1K2UWYS9Vfb4HlHtMGRi5pGRWj4CM9ZrKNbWo58vdvh4/edit#gid=0",
    "MobilePins" : [
            { "pin": "11111", "stationType": "Timing" },
            { "pin": "22222", "stationType": "Penalties" },
            { "pin": "33333", "stationType": "Timing+Penalties" }
        ]
  }
}'

{"config":{"mobileId":"r10000","mobilePin":"82722","status":"OK"}}
```

### Refresh lineups service

Existing timing data is unmodified.  This action will reload lineups from the configured data url.

```json
{
    "op" : "refresh",
    "email" : "youremail@gmail.com",
    "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
    "regatta" : "r10000",
}
```

### Update service

Existing timing data is unmodified when the update service is used.  Configuration fields, if present, will be updated with any values provided.

#### Entries update

If an 'entries' field is provided, it replaces existing lineups with
the data provided.  For each entry, only the following fields are
required:

- EventNum
- Event
- Bow
- Crew

Other fields will be utilized if present but are optional.

#### Example update JSON

This example updates the 'MobilePins' field which lock the mobile app into a specific station type as well as updating the lineups via the 'entries' field. The entries field must specify every entry.

```json
{
    "op" : "update",
    "email" : "youremail@gmail.com",
    "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
    "regatta" : "r10000",
    "config": {
        "MobilePins" : [
            { "pin": "11111", "stationType": "Penalties" },
            { "pin": "33333", "stationType": "Timing+Penalties" }
        ]
    },
    "entries" : [{
        "EventNum": "1",
        "Event": "Mens Varsity 8+",
        "Bow": "1",
        "Crew": "Greenlake Crew",

        "Start": "8:45:00",
        "Day": "Saturday",
        "Flight": "1",
        "EventAbbrev": "MV8+",
        "EventInfo": "Top 2 to Event 10",
        "Stroke": "",
        "CrewAbbrev": "GLC",
        "Age": "",
        "Exhibition": false
    },
    {
        "EventNum": "1",
        "Event": "Mens Varsity 8+",
        "Bow": "2",
        "Crew": "Everett Rowing",

        "Start": "8:45:00",
        "Day": "Saturday",
        "Flight": "1",
        "EventAbbrev": "MV8+",
        "EventInfo": "Top 2 to Event 10",
        "Stroke": "",
        "CrewAbbrev": "ERA",
        "Age": "",
        "Exhibition": false
    }]
}
```

### Clear timing data service

Any existing timing data is deleted and the cached data in the mobile device is cleared.

```json
{
    "op" : "clear",
    "email" : "youremail@gmail.com",
    "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
    "regatta" : "r10000",
}
```

### Clear mobile timing data service

Any existing timing data in the mobile device is cleared. Existing server timing results are retained.

```json
{
    "op" : "clearmobile",
    "email" : "youremail@gmail.com",
    "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
    "regatta" : "r10000",
}
```

### Delete a regatta service

```json
{
    "op" : "delete",
    "email" : "youremail@gmail.com",
    "uid" : "X7XRcJ1Ld6N22X7nr3PUB4wrn2",
    "regatta" : "r10000",
}
```

### Set Entry Status service

This service allows setting the status of an entry to one of DNS, DNF, Scratch, Exhibition, Excluded, or DQ.

```json
{
  "op": "store-lap",
  "email":"youremail@gmail.com",
  "uid":"X7XRcJ1Ld6N22X7nr3PUB4wrn2",
  "regatta":"'r10000",
  "config": {
    "Bow": "3",
    "EventNum": "5",
    "Gate": "Pen",
    "PenaltyCode": "DNS",  // or "DNF", "Scratch", "Exhibition", "Excluded" or "DQ"
    "Reporter": "Steve",
    "SequenceNum": 1,
    "Time": "19:23:22.111",
    "src": "MyApp",
    "uuid": "8cXE69TETtTLT5st2gPdRp"
    }
}
```

uuid should be a guid in string form. Any unique string convenient to you is OK.  All fields are string but SequenceNum.  You can send 1 for SequenceNum all the time and it'll work OK.  It's purpose is to avoid timing issues where quick successive changes might arrive out of order so the highest SequenceNum wins.

If you want to 'Delete' a value you have sent previously, send the same message and uuid but add "State": "Deleted" as an additional field.

If you edit an entry from Bow 3 to Bow 4 you must either mark deleted the Bow 3 entry or send the Bow 4 entry with the same uuid as used for Bow 3 and it'll replace it.

## Configuration Fields

The typescript template below defines the 'config' fields available when using the 'create' or 'update' service.  The ? following a name indicates an optional field.

```typescript
export interface RegattaConfigFields {

  /** The starting date of the regatta. e.g. '2016-09-24' */
  Date: string;

  /** The title shown on the website and mobile app */
  Title: string;

  /** The default timing method if not specified in lineups */
  RaceType: 'Sprint' | 'Head';

  /** Informational text shown on the website results page */
  InfoText?: string;

  /** The url of a source for Event lineups.  Typically a link to a Google Sheet but can be any URL. */
  DocUrl?: string;

  /** True if the regatta is 'done'.  This blocks input from the mobie app and marks all races official.  */
  Finished?: boolean;

  /** True to show the regatta on crewtimer.com */
  Public?: boolean;

  /** The Handicap system to use.  Manual requires a Handicap column while the others require an Age column */
  HandicapType?: 'None' | 'Manual' | 'US' | 'RCA' | 'RCA_RAW';

  /** A multiplier for computing handicaps relative to a 1k race.
   * A 2k race would use a multiplier of "2".
   */
  HandicapMultiplier?: string;

  /**
   * Specifies the desired points engine to use.  See CrewTimer support for options.
   */
  PointsEngine?: string;

  /** A comma separated list of Penalties or Referee actions which can be applied to individual entries.
   * The format is Text[(Code)][:seconds] with Code and seconds being optional.  The default is USRowing defaults:
   * Missed Course Buoy(Buoy):10
   * Out Of Order Start(Order):10
   * Start Staging Yield(Staging):10
   * Failure To Yield(FTYield):30
   * Missing Bow #(Bow#):60
   * Did Not Start(DNS)
   * Did Not Finish(DNF)
   * Scratch
   * Exhibition(Exhib
   */
  CustomCodes?: string;

  /** The mobile pin requird on the mobile device.
   * This pin gives full access.  See MobilePins for restricted pins.
   */
  MobileKey?: string; // pin

  /** Optional Mobile Pins to lock down the mobile UI to a specific station type.
   * Specified as an array of pin/stationType.  e.g. { pin: '1111', stationType: 'Penalties' }
   */
  MobilePins?: { pin: string; stationType: 'Timing' | 'Penalties' | 'Timing+Penalties' }[];

  /** A comma separated list of waypoints/timing stations.
   * Backup waypoints have an additona numeric suffix.  e.g. Start2, Finish2
   */
  Waypoints: string;

  /** Which waypoints to show on the results page.  Default is to show all except 'backup' waypoints. */
  ResultWaypoints: string;

  /** The number of result digits to show on website results */
  ResultDigits: '1' | '2' | '3';

  /** Hide finish times until an event has been declared official. */
  ResultsPendOfficial?: boolean;

  /** True to hide all lineups and results.  Used when regatta under construction. */
  ResultsPending?: boolean;

  /** An array of result columns names to omit on web results
   * For example: ["Start","Raw Time","Adjust","Stroke","Split"]
   */
  ResultOmitCols?: string[];

  /** A comma separated list of penalty locations.
   * When specified, the mobile app will allow a location to be specified with each penalty.
   */
  PenaltyLocations?: string;

  /** An array of control point names
   * For example: ["Launch", "Recovery"]
   */
  TrackingStations?: string[];

  /** The data source for Event lineups */
  DataSource?: 'GoogleSheets' | 'RegattaMaster' | 'RegattaWorkbench';

  /** Alternate titles for the results website.
   * e.g. Titles = { 'Crew': 'Club', 'Stroke': 'Athletes' }
   * Common overrides are Event, Crew, Stroke, Bow, Lane, Split
   */
  Titles?: {[title:string]:string};

  /** A comma separated list of admin emails.
   * The users in the list will have admin access to this regatta via their crewtimer.com login.
   */
  Admins?: string;
}
```

## Other Services

### QR Code mobile app settings

By using QR Codes, mobile devices can scan the qrcode and have it start the CrewTimer Mobile App and configure it with specific settings.  Version 5.7.4 of the mobile app is required to utilize this feature.

The URL provided by a CrewTimer QR code has the unique feature in that it will prompt users to install the CrewTimer Mobile App if it is not alredy installed.  If the app is already installed, it will start the app and configure it.

This capability is referred to as [Deferred Deep Linking](https://en.wikipedia.org/wiki/Mobile_deep_linking#Deferred_deep_linking)

A CrewTimer QR Code uses a base URL of `https://link.crewtimer.com/m/` with four required arguments:

| URL Argument | Value                                                                                |
| ------------ | ------------------------------------------------------------------------------------ |
| link         | A url of the form `https%3A//crewtimer.com/goto/<mobileID>/<base64 JSON properties>` |
| apn          | net.entazza.crewtimer                                                                |
| ibi          | net.entazza.crewtimer                                                                |
| isi          | 1450216565                                                                           |

- Note the %3A in place of colon in the link parameter.  This is required for the Android camera app and works on iOS as well.
- `<mobileID>` is the CrewTimer mobileID such as r12071
- `<base64 JSON properties>` is a base64 representation of additional required arguments specified as JSON (See below).

The URL arguments 'apn', 'ibi', and 'isi' are needed to properly trigger the mobile device to open the CrewTimer app and are not optional.

The base64 encoded JSON properties must specify the following:

| Property Name | Description                                                                                                                                                |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| mobilePin     | A mobile pin associated with the mobileID to customize behavior. This can be the 'master' pin or it can be one of the limited pins customized by the user. |

For example, `{"mobilePin":"121212"}` would encode as 'eyJtb2JpbGVJRCI6InIxMjA3MSIsIm1vYmlsZVBpbiI6IjEyMTIxMiJ9eyJtb2JpbGVQaW4iOiIxMjEyMTIifQ=='.  The [JSON to Base64 Utility](https://codebeautify.org/json-to-base64-converter#) can be used to verify proper encoding.

Thus, the full URL using the above example (albeit with an invalid pin) would be

```txt
https://link.crewtimer.com/m/?
link=https%3A//crewtimer.com/goto/r12071/eyJtb2JpbGVQaW4iOiIxMjEyMTIifQ==&
apn=net.entazza.crewtimer&
ibi=net.entazza.crewtimer&
isi=1450216565
```

#### Optional JSON Properties

The following optional properties can be specified.

| Property Name | Description                                                                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| waypoint      | The default timing waypoint with which to configure the mobile app.  e.g. Start, 1000m, Finish                                                    |
| stationType   | One of "Timing", "Penalties", or "Timing+Penalties".  This is only applicable when used with the master pin as user pins specify this implicitly. |

#### QR Code Testing

When testing QR Codes, it works well to change the mobile device Configuration Source to 'Local' to reset any prior settings prior to scanning the QR Code.  You can also test your url by emailing it to yourself and clicking on it from a mobile device.
