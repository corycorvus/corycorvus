# VR Store DRM



## Steam
---

[Steam DRM](https://partner.steamgames.com/doc/features/drm)

Steam provides an DRM wrapper that can be automated as part of the SteamPipe upload script.


## Oculus
---

[Oculus DRM - Unity](https://developer.oculus.com/documentation/unity/ps-entitlement-check/)

[Oculus DRM - Unreal](https://developer.oculus.com/documentation/unreal/ps-entitlement-check/)

[Oculus DRM - Native](https://developer.oculus.com/documentation/native/ps-entitlement-check/)


Oculus store requires integration of the "Entitlement Check" via the Oculus SDK.

##### Oculus DRM Unity Sample Code

```csharp
using UnityEngine;
using Oculus.Platform;

public class AppEntitlementCheck: MonoBehaviour {

  void Awake ()
  {
    try
    {
      Core.AsyncInitialize();
      Entitlements.IsUserEntitledToApplication().OnComplete(EntitlementCallback);
    }
    catch(UnityException e)
    {
      Debug.LogError("Platform failed to initialize due to exception.");
      Debug.LogException(e);
      // Immediately quit the application.
      UnityEngine.Application.Quit();
    }
  }

  // Called when the Oculus Platform completes the async entitlement check request and a result is available.
  void EntitlementCallback (Message msg)
  {
    if (msg.IsError) // User failed entitlement check
    {
      // Implements a default behavior for an entitlement check failure -- log the failure and exit the app.
      Debug.LogError("You are NOT entitled to use this app.");
      UnityEngine.Application.Quit();
    }
    else // User passed entitlement check
    {
      // Log the succeeded entitlement check for debugging.
      Debug.Log("You are entitled to use this app.");
    }
  }
}
```


## Viveport
---

[Viveport DRM api](https://developer.vive.com/resources/viveport/sdk/documentation/english/viveport-sdk/apis/drm-api/)

[Viveport DRM wrapper vs api](https://service.viveport.com/hc/en-us/articles/360035791212-What-is-the-difference-between-DRM-SDK-and-DRM-wrapper-)

Viveport store supports DRM via both wrapper and Viveport SDK. The DRM wrapper is enabled via checkbox on store submission.

##### Viveport DRM Unity Sample Code

```csharp
using System.Collections;
using UnityEngine;
using Viveport;

public class ViveportSampleDRM : MonoBehaviour
{
    // Get a VIVEPORT ID and VIVEPORT Key from the VIVEPORT Developer Console. Please refer to here:
    // https://developer.viveport.com/documents/sdk/en/viveport_sdk/definition/get_viveportid.html

    static string VIVEPORT_ID = "VIVEPORT ID of the content";           // replace with developer VIVEPORT ID
    static string VIVEPORT_KEY = "VIVEPORT Key of the content";         // replace with developer VIVEPORT Key

    private const int SUCCESS = 0;
    private static bool bInitComplete = false;

    void Awake()
    {
        MainThreadDispatcher mainThreadDispatcher = GameObject.FindObjectOfType();
        if (!mainThreadDispatcher)
        {
            gameObject.AddComponent();
        }
    }

    void Start()
    {
        Api.Init(InitStatusHandler, VIVEPORT_ID);       // initialize VIVEPORT platform
        Invoke("CheckInitStatus", 10);                  // check that VIVEPORT Init succeeded
    }

    void OnDestroy()
    {
        Api.Shutdown(ShutdownHandler);
    }

    private static void InitStatusHandler(int nResult)          // The callback of Api.init()
    {
        if (nResult == SUCCESS)
        {
            Debug.Log("VIVEPORT init pass");
            Api.GetLicense(new MyLicenseChecker(), VIVEPORT_ID, VIVEPORT_KEY);    // the response of Api.Init() is success, continue using Api.GetLicense() API
            bInitComplete = true;
        }
        else
        {
            Debug.Log("VIVEPORT init fail");
            Application.Quit();
            return;                                             // the response of Api.Init() is fail
        }
    }
    private static void ShutdownHandler(int nResult)            // The callback of Api.Shutdown()
    {
        if (nResult == SUCCESS)
        {
            Application.Quit();                                 // the response of Api.Shutdown() is success, close the content
        }
        else
        {
            return;                                             // the response of Api.Shutdown() is fail
        }
    }

    private void CheckInitStatus()
    {
        if (!bInitComplete)
        {
            Debug.LogWarning("Viveport init check fail");     // init requires VIVEPORT app installed and online connection
            Application.Quit();
        }
        else
            Debug.Log("Viveport init check pass");
    }

    class MyLicenseChecker : Api.LicenseChecker
    {
        public override void OnSuccess(long issueTime, long expirationTime, int latestVersion, bool updateRequired)
        {
            // the response of Api.GetLicense() is DRM success, user is allowed to use the content and continue with content flow
            Debug.Log("Viveport DRM pass");
            Debug.Log("issueTime: " + issueTime);
            Debug.Log("expirationTime: " + expirationTime);
            MainThreadDispatcher.Instance().Enqueue(SuccessAction());
        }

        public override void OnFailure(int errorCode, string errorMessage)
        {
            // the response of Api.GetLicense() is DRM fail, user is not allowed to use the content
            Debug.LogWarning("Viveport DRM fail:"+ errorCode + " Message :" + errorMessage);
            MainThreadDispatcher.Instance().Enqueue(FailAction());
        }

        // Use these methods to call Unity functions from the API callbacks on the main thread
        IEnumerator SuccessAction()
        {
            yield return null;
        }

        IEnumerator FailAction()
        {
            Application.Quit();
            yield return null;
        }
    }
}
```


## Google Play
---

[Google Play App Licensing](https://developer.android.com/google/play/licensing)

[Google Play Application License Verification - Unity](https://github.com/Unity-Technologies/GooglePlayLicenseVerification)


## Epic Game Store
---

No store wide DRM.