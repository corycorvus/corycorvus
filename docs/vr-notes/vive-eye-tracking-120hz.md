# VIVE Eye Tracking at 120hz

---



_Note: First setup the VIVE Eye Tracking SDK and verify basic functionality (calibration & demo scene)_

_Note: Callback runs on a separate thread to report data at ~120hz_

_Note: **Unity is not thread-safe and cannot call any UnityEngine api from within callback thread**._



## Unity Guide

---



## Setup Project for Eye Tracking

- Import VIVE Eye Tracking SDK Unity Plugin (SRanipal)

- Add the SRanipal Eye Framework  to the Unity scene

  - Drag "SRanipal Eye Framework" prefab into scene hierarchy

    or

  - Attach "SRanipal_Eye_Framework.cs" script to gameobject in scene

- Setup Framework Settings

  - Check "Enable Eye" (enabled by default)
  - Check "Enable Eye Data Callback"



## Setup EyeData Callback



### Register EyeData Callback

Note: Only register callback when the eye tracking framework status is working and do not register more than one callback at once.

``` csharp

SRanipal_Eye.WrapperRegisterEyeDataCallback(Marshal.GetFunctionPointerForDelegate((SRanipal_Eye.CallbackBasic)EyeCallback));
```



### Use EyeData Callback

```csharp
        private static EyeData eyeData = new EyeData();

        /// Required class for IL2CPP scripting backend support
        internal class MonoPInvokeCallbackAttribute : System.Attribute
        {
            public MonoPInvokeCallbackAttribute() { }
        }

        [MonoPInvokeCallback]
        private static void EyeCallback(ref EyeData eye_data)
        {
            eyeData = eye_data;
            // do stuff with eyeData...
        }

```



### Unregister EyeData Callback

Note: Must unregister callback when complete or application is disabled/quit.

``` csharp
                SRanipal_Eye.WrapperUnRegisterEyeDataCallback(Marshal.GetFunctionPointerForDelegate((SRanipal_Eye.CallbackBasic)EyeCallback));
```



## Unity Sample Code

---


```csharp
using UnityEngine;
using ViveSR.anipal.Eye;
using System.Runtime.InteropServices;

/// <summary>
/// Example usage for eye tracking callback
/// Note: Callback runs on a separate thread to report at ~120hz.
/// Unity is not threadsafe and cannot call any UnityEngine api from within callback thread.
/// </summary>
public class CallbackExample : MonoBehaviour
{
    private static EyeData eyeData = new EyeData();
    private static bool eye_callback_registered = false;

    private void Update()
    {
        if (SRanipal_Eye_Framework.Status != SRanipal_Eye_Framework.FrameworkStatus.WORKING) return;

        if (SRanipal_Eye_Framework.Instance.EnableEyeDataCallback == true && eye_callback_registered == false)
        {
            SRanipal_Eye.WrapperRegisterEyeDataCallback(Marshal.GetFunctionPointerForDelegate((SRanipal_Eye.CallbackBasic)EyeCallback));
            eye_callback_registered = true;
        }
        else if (SRanipal_Eye_Framework.Instance.EnableEyeDataCallback == false && eye_callback_registered == true)
        {
            SRanipal_Eye.WrapperUnRegisterEyeDataCallback(Marshal.GetFunctionPointerForDelegate((SRanipal_Eye.CallbackBasic)EyeCallback));
            eye_callback_registered = false;
        }
    }

    private void OnDisable()
    {
        Release();
    }

    void OnApplicationQuit()
    {
        Release();
    }

    /// <summary>
    /// Release callback thread when disabled or quit
    /// </summary>
    private static void Release()
    {
        if (eye_callback_registered == true)
        {
            SRanipal_Eye.WrapperUnRegisterEyeDataCallback(Marshal.GetFunctionPointerForDelegate((SRanipal_Eye.CallbackBasic)EyeCallback));
            eye_callback_registered = false;
        }
    }

    /// <summary>
    /// Required class for IL2CPP scripting backend support
    /// </summary>
    internal class MonoPInvokeCallbackAttribute : System.Attribute
    {
        public MonoPInvokeCallbackAttribute() { }
    }

    /// <summary>
    /// Eye tracking data callback thread.
    /// Reports data at ~120hz
    /// MonoPInvokeCallback attribute required for IL2CPP scripting backend
    /// </summary>
    /// <param name="eye_data">Reference to latest eye_data</param>
    [MonoPInvokeCallback]
    private static void EyeCallback(ref EyeData eye_data)
    {
        eyeData = eye_data;
        // do stuff with eyeData...
    }
}
```





