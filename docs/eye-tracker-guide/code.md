# Code Samples

![Eye Tracker Gaze](https://user-images.githubusercontent.com/3579516/84325275-3fc66280-ab2f-11ea-8432-f4c7b8aa2557.png)


## Snippets
* main functions
* get data 120hz
* log data
* heat maps

### Calibration
```csharp
int calibrationResult= ViveSR.anipal.Eye.SRanipal_Eye_API.LaunchEyeCalibration(System.IntPtr.Zero); // Ptr not implemented so using Zero
```

### Needs Calibration Check
```csharp
bool needsCalibration = false;
ViveSR.anipal.Eye.SRanipal_Eye_API.IsUserNeedCalibration(ref needsCalibration);
```

### Is Pro Eye Check
```csharp
bool isProEye = ViveSR.anipal.Eye.SRanipal_Eye_API.IsViveProEye();
```

### Set Filtering
```csharp
void SetFiltering(double filteringLevel) 
{
    EyeParameter parameter = new EyeParameter
    {
        gaze_ray_parameter = new GazeRayParameter(),
    };

    parameter.gaze_ray_parameter.sensitive_factor = filteringLevel;
    Error error = SRanipal_Eye_API.SetEyeParameter(parameter);
}
```


### Focus

_Note: Focus() wraps the unity API Physic.Raycast()_

### Filtering

Filtering is added to prevent gaze tremble (ex. when looking at distant objects). Use SetEyeParameter to set the filtering level with "sensitive_factor". You can adjust the variable to effect the cutoff slope in the filter.

1 is raw gaze vector without adding a filter post-processing for gaze tremble.

0 is post processed with strongest filter to remove gaze tremble.`

The default value is 0.007 and you can multiply or divide the variable by 10 until you notice the effect on the gaze data.

_Note: SetEyeParameter filtering only works on gaze rays._



### EyeData_v2

EyeData_v2 has "expression_data", which supports more facial expression blendshapes.

### Convergence Distance

_Note: "convergence_distance_mm" is currently not implemented._


### Main SDK Functions

```c
//via verboseData    
    pupil_diameter_mm                       // pupil diameter in millimeters (~2.5)
    pupil_position_in_sensor_area           // pupil position relative to lenses (0.5,0.5 is center)
    eye_openness                            // eye openness (0 closed, 1 open)
    gaze_origin_mm                          // millimeter position of cornea center relative to each lens center (~ 30,-1,-25/-30,1,-25)
    gaze_direction_normalized               // gaze direction vector
    convergence_distance_mm                 // currently not implemented

SRanipal_Eye.Focus                                      // check current object collider in focus
GetValidity                                             // data validity bitmask
SRanipal_Eye.LaunchEyeCalibration();                    // eye calibration
SetEyeParameter / GetEyeParameter                       // filtering level

SRanipal_Eye_Framework.Instance.EnableEyeVersion        // framework version
SRanipal_Eye_Framework.Instance.StartFramework();       // start framework
SRanipal_Eye_Framework.Instance.StopFramework();        // stop framework
SRanipal_Eye_Framework.Status                           // framework status

    Vector2 vector2;
    float eyeOpenLeft;
    SRanipal_Eye.GetPupilPosition(EyeIndex.LEFT, out vector2);
    SRanipal_Eye.GetEyeOpenness(EyeIndex.LEFT, out eyeOpenLeft);
```