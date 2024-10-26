# CrewTimer Firmware Upgrade

## Introduction

The CrewTimer bluetooth devices (clickers, relays, and horns) support firmware upgrades in the field with firmware image files provided by CrewTimer. The procedure below describes how to upgrade your device.

**Note:** The firmware update image for the clicker, relay, and horn are identical and generally should be updated together if you own both.

## Identifying your clicker version

Only V2 or later clickers have firmware updates available. If you have a V1 clicker a firmware update is not necessary.

- V1 clickers have an LED on either side of the USB connector and utilize micro USB. Firmware updates are not required.
- V2 clickers have three LEDs on one side of the USB connector and except for a few beta users, have V2 printed on the bottom.
- V3/V4 clickers have a USB-C charging port.

## Upgrading the Firmware

1. Ensure you have a firmware upgrade file available with a `.uf2` suffix. Download the latest firmware from [CrewTimer Hardware Help](https://crewtimer.com/help/Hardware).
2. Plug your device into a PC or Mac computer via the USB port.
3. Press and hold the button until the device fast-blinks and then quickly press the button three times in a row.
4. Depending on the date of manufacture, either you will see a ‘breathing’ green led or all the lights should go out except for the red charging led. If a blue LED shows up, see the Upgrade Issues section below.
5. You should see a new disk/drive on your computer named `FTHR840BOOT` or `RAK4631` as if it is a flash memory stick.
6. Copy the `.uf2` firmware file provided by CrewTimer to the drive. If running MacOS Ventura and you get an error 100093, switch to a terminal window and copy manually: ```cp ~/Downloads/crewtimer-x.yy.uf2 /Volumes/RAK4631```
7. As soon as the file is copied, the device will eject from the computer and upgrade itself. After about 8-10 seconds it will reboot with the new firmware.
8. Connect the device to your mobile app and verify the version number matches the expected firmware version of the upgrade file.

## Upgrade issue for Beta V2 clickers

If the `FTHR840BOOT` drive does not show up or the blue LED is illuminated when you initiate the upgrade you will need to use an alternate approach to initiate the upgrade:

1. Using a SIM card tool or small paper clip, insert it into the reset hole next to the USB connector. You should feel a click when the reset button is pressed.
2. While still connected to your computer, press the reset button twice in very quick succession. You should not see the usual green led activity if successful.
3. Proceed with step 5 above.

## Support

For questions or suggestions, send an email to [info@crewtimer.com](mailto:info@crewtimer.com).

[CrewTimer Hardware Help](https://crewtimer.com/help/Hardware)
