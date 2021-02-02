![Tracker Size and Coordinates](https://user-images.githubusercontent.com/3579516/81855160-cb8aa600-9513-11ea-9330-47e0f3299ae2.png)


# Hardware Info




## Tracker Specs

|                  | Tracker                                             | Tracker (2018)                                      |
| ---------------- | --------------------------------------------------- | --------------------------------------------------- |
| Tracking         | Supports SteamVR BS1.0                              | Supports SteamVR BS1.0 and BS2.0                    |
| Status Indicator | LED                                                 | LED                                                 |
| Input            | Power button, micro-USB, Pogo pin                   | Power button, Pogo pin                              |
| Charging         | Micro-USB                                           | Micro-USB                                           |
| Attachment       | 1/4-inch UNC threaded mount (standard tripod mount) | 1/4-inch UNC threaded mount (standard tripod mount) |
| Model            | 99HALM003-00                                        | 99HANL002-00                                        |
| Logo Color       | Grey                                                | Blue                                                |


[Link](https://developer.vive.com/us/vive-tracker-for-developer/)



## Tracker Size
The overall size of the VIVE Tracker is 99.65mm * 42.27mm (height); 


## Tracker Weight
89g


## LED Status

| Color      | Status            |
| ---------- | ----------------- |
| Green      | Normal Mode       |
| Blue       | Not Connected     |
| Blink Blue | Pairing Mode      |
| Blink Red  | Low Battery       |
| Orange     | Charging Mode     |
| White      | Full Charge (Off) |


[Checking the Status Light](https://www.vive.com/us/support/wireless-tracker/category_howto/checking-the-status-light.html)


## IR Frequency
~850nm IR


## RF / BT Frequency
2.402-2.48 GHz

[FCC](https://fccid.io/NM82PYV100)


## FOV
Tracker Field of View (FOV) is 270°

![VIVE Tracker FOV](https://user-images.githubusercontent.com/3579516/81854170-61bdcc80-9512-11ea-8f49-af17ba0ac3f5.png)


## Maximum Trackers

Officially: 11 VIVE Trackers, plus 2 VIVE controllers

Unofficially: 62 (64 - base stations - HMD = MAX)

Note: More than 15 will likely have interference issues, more than 30-50 will have extreme interference issues.


## Pogo Pins

![Tracker POGO pins](https://user-images.githubusercontent.com/3579516/81854532-e6104f80-9512-11ea-9093-bcde9a3781a7.png)

| Pin No. | Type                | Button   | Description                                                  |
| ------- | ------------------- | -------- | ------------------------------------------------------------ |
| 1       | Digital Output      | Vibrator | General purpose output pin                                   |
| 2       | GND                 |          | Ground                                                       |
| 3       | Digital/Power Input | Grip     | General purpose input pin: Internal pull up resistor to VDD, Active-low, Power input pin |
| 4       | Digital Input       | Trigger  | General purpose input pin: Internal pull up resistor to VDD, Active-low |
| 5       | Digital Input       | Trackpad | General purpose input pin: Internal pull up resistor to VDD, Active-low |
| 6       | Digital Input       | Menu     | General purpose input pin: Internal pull up resistor to VDD, Active-low |

* See Developer Guideline for more info about pogo pins and input


## Coordinate System

Vive Tracker uses the “Right-handed coordinate system”. 

Unity: X(right), Y(up), Z(forward)

OpenVR: X(right), Y(up), Z(backward)

* Note: There are reports of some models with a 90° yaw offset
* Note: When assigned the SteamVR role "hold in hand" orientation will change

![Tracker Role Coordinate](https://user-images.githubusercontent.com/3579516/81856189-515b2100-9515-11ea-9968-53d14c40aaf4.png)


## Base Station Versions

_Base Station Version 1.0_

Max: 2 stations (3.5x3.5 meters)

FOV: 120°

![base_station_01](https://user-images.githubusercontent.com/3579516/81875730-bde61800-9535-11ea-9744-f8d97b5fad18.jpg)

_Base Station Version 2.0_

Max: 4 stations (10x10 meters)

FOV: 150°

![base_station_02](https://user-images.githubusercontent.com/3579516/81875734-bfafdb80-9535-11ea-8255-d8ea581e8f0c.png)