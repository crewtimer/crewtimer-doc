
# CrewTimer Hardware Resources

## Device Manuals

* [CrewTimer Bluetooth Clicker](https://storage.googleapis.com/resources.crewtimer.com/docs/CrewTimer%20Bluetooth%20Clicker.pdf)
* [CrewTimer Relay](https://storage.googleapis.com/resources.crewtimer.com/docs/CrewTimer%20Relay.pdf)
* [CrewTimer Mobile Horn Operation](https://storage.googleapis.com/resources.crewtimer.com/docs/CrewTimer%20Mobile%20Horn.pdf)
* [CrewTimer Mobile Horn Kit Assembly](https://storage.googleapis.com/resources.crewtimer.com/docs/CrewTimerMobileHornKit.pdf)

## Firmware

Firmware updates are provided for all CrewTimer Hardware devices **Except V1 Clickers**.  The same firmware image is used for all types of hardware.  To upgrade the firmware in your devices, download the firmware image below and follow the instructions in the PDF document.

* [CrewTimer Firmware Image](https://storage.googleapis.com/resources.crewtimer.com/firmware/crewtimer-3.02.uf2)
* [CrewTimer Firmware Upgrade Instructions PDF](../general/FirmwareUpgrade.md)

### Firmware History

| Version | Date       | Notes                                                                                                                                        |
| ------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 3.02    | 2024-06-13 | Remove long press.  Clicks held for more than 2 seconds and less than 5s were discarded.  >5s still enters command mode.                     |
| 3.01    | 2024-05-13 | Remove need for configuration straps.  Hardware config stored in flash memory.                                                               |
| 2.23    | 2023-12-23 | Support for importing clicks that occur while unpaired.  Allows changing mobile devices without losing clicks.                               |
| 2.22    | 2023-05-21 | Support for additional I/O for Beach Sprints                                                                                                 |
| 2.21    | 2023-04-28 | Internal Release for Beach Sprint testing                                                                                                    |
| 2.20    | 2023-04-09 | Fix LoRa issue causing missed horn or relay triggers                                                                                         |
| 2.19    | 2022-04-05 | Allow Mobile Horn to also accept a clicker switch input for timing.                                                                          |
| 2.18    | 2022-12-15 | Fix bug in clicker where horn/relay could miss sounding 2nd actuation. Fix bug where horn would not automatically turn off after inactivity. |
| 2.17    | 2022-12-08 | Support for Mobile Horn Box                                                                                                                  |
| 2.16    | 2022-11-19 | Remove entry to test mode via zero clicks after fast blink                                                                                   |
| 2.15    | 2022-11-05 | Increase internal clicker memory to 512 clicks                                                                                               |
| 2.09    | 2022-01-19 | Support Relay module (needs Mobile v5.3.1).                                                                                                  |
| 2.07    | 2021-11-03 | First horn release                                                                                                                           |
| 2.02    | 2021-10-06 | Ignore clicks while unconfigured.                                                                                                            |
| 2.01    | 2021-09-19 | Initial V2 Clicker                                                                                                                           |
