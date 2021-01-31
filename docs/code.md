## Open Source Projects
---


### UnRar Android Plugin
> A simple native android plugin for Unity to UnRar files.
> 
> [UnRar Android Plugin](https://github.com/corycorvus/UnRar-Android-Plugin)


### EyeTool - Eye Tracking Toolkit
> Collection of useful eye tracking functions and code samples.
> 
> [EyeTool](https://github.com/corycorvus/EyeTool)


### Unity Native Android Toolkit
> Toolkit to access a variety of native android features in Unity. Also includes features to create new native plugins.

 <br>

## Code Snippets
---

### DRM

#### Unity Distribution Portal (UDP) DRM

> [TestUDP.CS](https://gist.github.com/corycorvus/8f2cd4461d7927291e18eb0f50786b94) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/8f2cd4461d7927291e18eb0f50786b94/raw/1317a92a6524966a93f71895038838c33b05a2ea/TestUDP.cs)


#### Viveport DRM

> [ViveportDRM.cs](https://gist.github.com/corycorvus/9a981f397c4ce86082f7f8834e2e936e) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/9a981f397c4ce86082f7f8834e2e936e/raw/59af66df2801e40e4c5be20baee46c63050ec242/ViveportDRM.cs)



#### Oculus DRM

> [OculusPlatformEntitlementCheck.cs](https://gist.github.com/corycorvus/5e96c75c25c6de1c6e14acde2ab30ff9) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/5e96c75c25c6de1c6e14acde2ab30ff9/raw/8b0f4756022b855f74946b4755b61a0027f35e74/OculusPlatformEntitlementCheck.cs)

---



### Detect VR HMD & Controller Types

> [DetectVR.cs](https://gist.github.com/corycorvus/5e4f76f24b77eef111c28ebdb32edf36) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.github.com/corycorvus/5e4f76f24b77eef111c28ebdb32edf36/raw/cfc95f785481b7c0beb5692f2b48939109670abd/DetectVR.cs)

### Unity .gitignore

> [.gitignore](https://gist.github.com/corycorvus/258d4ece8c709d7fa81fc6e66b7a4f6e) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/258d4ece8c709d7fa81fc6e66b7a4f6e/raw/c0579312280c10032a88eb8d7cbe51126b381cde/.gitignore) 

```csharp
# .gitignore for Unity by Cory Corvus

# Ignore everything
/*
/*/

# Keep assets & project settings
!/Assets/
!/ProjectSettings/

# Git meta files
!.gitignore
!README.md
!.gitattributes

# Builds
*.unitypackage
```

### VIVE Eye Tracking Calibration

> [EyeCalibration.cs](https://gist.github.com/corycorvus/41184879b3f0765461333de59e0571fc) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/41184879b3f0765461333de59e0571fc/raw/14ba50005e49a6c0235dc6e47d990dabdfe1f418/EyeCalibration.cs)

```csharp
void EyeCalibration() 
{
    Debug.Log("Start Calibration");
    int result = ViveSR.anipal.Eye.SRanipal_Eye_API.LaunchEyeCalibration(System.IntPtr.Zero); // Ptr not implemented so using Zero
    Debug.Log("Finish Calibration: " + result);
}
```

### VR Controller Vibration Haptic Pulse

> [HapticPulse.cs](https://gist.github.com/corycorvus/2b0788719f06fc162a8d5466ba58ac4d) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/2b0788719f06fc162a8d5466ba58ac4d/raw/67439b49a430b1ea6249b813725102cecfb81f58/HapticPulse.cs)


### Power Off SteamVR Device
> [steamvr_device_poweroff.cs](https://gist.github.com/corycorvus/2bcfc6c95285200fa9931b10fdf78a22) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/2bcfc6c95285200fa9931b10fdf78a22/raw/4d5efee40929a19a0f2c44b00d4ac32adc752b4f/steamvr_device_poweroff.cs)

```csharp
    System.Diagnostics.Process process = new System.Diagnostics.Process();

    process.StartInfo.FileName = "C:\\Program Files (x86)\\Steam\\steamapps\\common\\SteamVR\\tools\\lighthouse\\bin\\win64\\lighthouse_console.exe";
    process.StartInfo.Arguments = "/serial 81F6B76702 poweroff";

    process.StartInfo.UseShellExecute = true;
    process.StartInfo.CreateNoWindow = true;
    process.StartInfo.WindowStyle = System.Diagnostics.ProcessWindowStyle.Hidden;

    process.Start();
```

### VIVE Tracker Serial Number (C++)

> [vive_tracker_serial.cpp](https://gist.github.com/corycorvus/1f558e874e5900d35b80fa1ff9bbd8c8) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/1f558e874e5900d35b80fa1ff9bbd8c8/raw/a14ed3e4025007dfa2918e6ae432532f11dbc0c4/vive_tracker_serial.cpp)

```cpp
char serialNumber[1024];
vr::VRSystem()->GetStringTrackedDeviceProperty(deviceID, vr::Prop_SerialNumber_String, serialNumber, sizeof(serialNumber));

printf("Serial Number = %s \n", serialNumber);
```


### Windows Native Dialog Plugin

> Class for displaying native Windows modal dialogs in Unity.
> 
> [WindowsNativeDialog.cs](https://gist.github.com/corycorvus/e79f48edebfc3cd527ba56f989f209b1) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/e79f48edebfc3cd527ba56f989f209b1/raw/e4df7c389325abb598218d366809e115e4189628/WindowsNativeDialog.cs)


### Unity Singleton

> Unity Singleton example
> 
> [UnitySingleton.cs](https://gist.github.com/corycorvus/e5f468158ce9255384957314d2350b9f) &ensp; [<img width="22px" src="_media/download.png" />](https://gist.githubusercontent.com/corycorvus/e5f468158ce9255384957314d2350b9f/raw/45a703259b2d33343c8ad020f3a23d143fa2e372/UnitySingleton.cs)

```csharp
        // Unity Singleton Example
        // Call with "ClassName.instance.Example();"
        public static ClassName instance = null;              //Static instance of singleton which allows it to be accessed by any other script.

        //Awake is always called before any Start functions
        void Awake()
        {
            //Check if instance already exists
            if (instance == null)                
                //if not, set instance to this
                instance = this;            
            //If instance already exists and it's not this:
            else if (instance != this)                
                //Then destroy this. This enforces our singleton pattern, meaning there can only ever be one instance of a GameManager.
                Destroy(gameObject);                
            //Sets this to not be destroyed when reloading scene
            DontDestroyOnLoad(gameObject);            
        }
```

