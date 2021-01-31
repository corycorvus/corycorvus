![VIVE Tracker 2018](https://user-images.githubusercontent.com/3579516/81639513-ff10e780-93d0-11ea-97f5-fd2e49693c2d.png)

# Tips and Troubleshooting




## Tracking Tips
* Update firmware
* Keep the dongle at least 45 cm (18 in) away from the computer
* Space out receiver dongles to prevent interference
* Add base stations (Up to 4 total with Base Station version 2.0) to prevent tracking occlusion
* Use a good dedicated USB controller or external powered USB hub for solving bandwidth issues and clean USB power supply issues. USB cards with Multiple Transaction Translator (MTT) have the best performance.
* Remove or cover reflective surfaces (glass, mirrors, TVs, screens, framed pictures, laminate flooring)
* Reduce IR interference sources (direct sunlight, Leap Motion, Kinect, etc.)
* Reduce magnetic interference (no strong magnets or metal near trackers, see Developer Guidelines)
* Disable nearby 2.4Ghz WiFi (or switch to 5Ghz) to prevent channel interference
* Disable nearby bluetooth devices (2.4 to 2.4835 GHz)
* SteamVR Settings --> Startup / Shutdown --> set "Turn off controllers after" to "Never", and set "Turn off controllers when exiting SteamVR" to "Off"
* Upgrade computer if having CPU/GPU performance issues
* Do not use the "VIVE Tracker Role Changer" exe tool (Deprecated)
* Create a SteamVR System Report and check the logs for advanced troubleshooting


Note: Open the Web Console when SteamVR is running to view logs.

    localhost:27062/console/index.html


## SteamVR Base Stations
* [Clean base stations](https://www.vive.com/us/support/vive-pro/category_howto/cleaning-the-base-stations.html)
* Securely mount base stations
* All base stations have green light
* [Valve SteamVR Base Station FAQ](https://support.steampowered.com/kb_article.php?ref=7897-DHKB-9990)


## Tracker doesn't power on
* Connect it to your computer using a USB data cable
* Reset VIVE Tracker (press and hold the Power button for 10 seconds)


## Tracker doesn't pair
* Start SteamVR (Vive controllers off and unplugged)
* Connect the tracker dongle to the PC
* Put the tracker in pairing mode (press and hold the Power button until blinking)
* Select Devices>Pair Controller in the SteamVR settings
* Tracker status light turns green when it is paired

## Wireless pairing tips
* Ensure you have connected a USB dongle for each tracker
* Disable nearby bluetooth devices
* Place tracker within line of sight or near dongle


## Tracker drifts
* See Tracking Tips
* Check SteamVR report logs


## Base Station light blinking red
* Hardware failure. Contact HTC Support for RMA.

## Unpair all SteamVR devices
1. On the PC, browse to C:\Program Files(x86)\Steam\steamapps\common\SteamVR\tools\lighthouse\bin\win32
2. Run exe
3. Type "unpairall" in the console window and then hit enter.
4. Once finished, the console window will display two identifiers as confirmation.
5. Close the console and restart SteamVR.


## Tracker is rotated 90°
When assigned the SteamVR role "hold in hand" orientation will change 90°. To change roles see [Switching Roles](https://github.com/corycorvus/VIVE-Tracker-Wiki/wiki/Usage-Guide#switching-roles)

## Copying chaperone room setup

The room setup data is stored in the "chaperone_info.vrchap" file found in "C:\Program Files (x86)\Steam\config" and can be backed up or copied to another PC.

[SteamVR "chaperone_info.vrchap" documentation](https://developer.valvesoftware.com/wiki/SteamVR/chaperone_info.vrchap)