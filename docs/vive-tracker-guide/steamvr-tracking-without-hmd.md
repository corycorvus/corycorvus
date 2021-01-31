

## SteamVR tracking without HMD

Note: If SteamVR updates it may be necessary to re-enable the default null driver.

### 1. Enable the default null driver

Edit the file "default.vrsettings", change "enable" to "true", save the file.

Default folder: 

    C:\Program Files (x86)\Steam\steamapps\common\SteamVR\drivers\null\resources\settings

**default.vrsettings**

        "enable": true,


### 2. Change SteamVR VR Settings

Edit the file "steamvr.vrsettings", make changes/additions below, save the file.

    C:\Program Files (x86)\Steam\config

**steamvr.vrsettings** "steamvr" section

      "requireHmd" : false,
      "forcedDriver" : "null",
      "activateMultipleDrivers" : true,
      "enableHomeApp" : false,


## SteamVR Room Setup without an HMD

### 1. Start SteamVR
![SteamVR null driver](https://user-images.githubusercontent.com/3579516/82004928-e8f56800-9618-11ea-924e-65a517b56985.PNG)

### 2. Pair tracker
[Tracker pairing steps](https://github.com/corycorvus/VIVE-Tracker-Wiki/wiki/Usage-Guide#dongle-pairing)

![SteamVR null driver with tracker](https://user-images.githubusercontent.com/3579516/82004937-eeeb4900-9618-11ea-8947-5d22115e432b.PNG)

### 3. Switch role to "Held in Hand"
[Switching role steps](https://github.com/corycorvus/VIVE-Tracker-Wiki/wiki/Usage-Guide#switching-roles) 

Note: Due to a current limitation it is only possible to send input via pogo pins when tracker role is set to "Held in Hand".

![SteamVR Manage Vive Trackers_crop](https://user-images.githubusercontent.com/3579516/82005146-7d5fca80-9619-11ea-8def-55eb200c61c3.png)

### 4. Start SteamVR Room Setup
Note: Choose "Room-Scale"

![room setup](https://user-images.githubusercontent.com/3579516/82005209-a2ecd400-9619-11ea-9890-54f465ee1c90.PNG)

### 5. Connect pogo pins 2+4 
Note: This step is required if using a VIVE tracker instead of a controller.

Connect the pogo pins 2+4 (ground + trigger) to activate trigger.

Note: Use a small piece of wire or a bent paperclip.

[Pogo pin diagram](https://github.com/corycorvus/VIVE-Tracker-Wiki/wiki/Hardware-Info#pogo-pins)

![pogo1](https://user-images.githubusercontent.com/3579516/82006421-9e75ea80-961c-11ea-8943-7889b24d93f9.jpg)
 ![pogo2](https://user-images.githubusercontent.com/3579516/82006370-7dad9500-961c-11ea-8596-6a4b53c39a46.jpg)

### 6. Complete Room Setup
Finish the room setup process. 

Note: If using a tracker then connect the pins whenever it asks you to pull the trigger.

Note: When drawing room boundaries, choose "Advanced" and use trigger/pogo when tracker is placed in each corner of the tracking space. 

Note: If tracker orientation is off by 90° change tracker role to anything other than "Held in Hand".