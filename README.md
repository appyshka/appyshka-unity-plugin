SDK Version: 0.6.4

Appyshka Unity Plugin
=====================

Unity3D Plugin for displaying Appyshka ads on Android

# Appyshka Unity Plugin

The Appyshka Unity Plugin allows you to provide Appyshka ads in Unity projects deployed as native Android applications. The following ad formats are supported by the plugin:
-banner ads (single banner, banner list)
-static fullscreen ads

The plugin is distributed as [.unitypackage file](package/Appyshka.unitypackage) for simple importing.

## Integration instructions
---
1. Open your project in Unity editor.
2. Import the [Appyshka.unitypackage file](package/Appyshka.unitypackage) to your project
3. Select the files you want to import:
	- Appyshka folder is required
	- Plugins/Android folder is required. Note that it contains AndroidManifest.xml file, if you already have such file in your Plugins/Android/ catalog skip it.
4. Implementation example scene could be found in Appyshka/Demo catalog
4. In the scene where you want to display ads, create object with Appyshka.cs script attached. You can simply drop the Appyska prefab to your scene to do so.

### Android instructions
---
1. If you already had the AndroidManifest.xml file in Plugins/Android/ and skipped the one contained in Appyshka .unitypackage, add the necessary permissions and activities required by Appyshka SDK:
```
	<uses-permission android:name="android.permission.INTERNET" />
																			
	<activity android:name="com.appyshka.sdk.APBannerWallActivity" />
```
3. To generate your project for Android, click File -> Build Settings, select the Android platform, then Switch Platform, mark Google Android Project checkbox, then Export. 
4. Import generated projects into your Eclipse workspace and run your application

## API Documentation
---
The Appyska/Internal/Appyska.cs plugin exposes the following methods:
```
// Starts loading banner wall ad
public static void InitBannerWall (string appId)

// If an banner wall ad is loaded this will take over the screen and show the ad
public static void ShowBannerWall (string appId)

// Creates a single banner with the given appId placed based on the alignment parameter
public static void ShowBanner (string appId, BannerAlignment alignment)

// Creates a banner list containing adsCount ads with the given appId placed based on the alignment parameter
public static void ShowBannerList (string appId, BannerAlignment alignment, int adsCount)

// Destroys the banner and removes it from the view
public static void HideBanner ()

```

### Also the following events notifying about the state of the ads are available:
```
// Fired when a single banner ad fails to load
public static event Action SingleBannerNoAdFoundEvent;

// Fired when a single banner ad is loaded
public static event Action SingleBannerAdLoadedEvent;

// Fired when a single banner ad is displayed
public static event Action SingleBannerAdShownEvent;

// Fired when a single banner ad is clicked
public static event Action SingleBannerAdClickedEvent;

// Fired when a single banner ad is closed
public static event Action SingleBannerAdClosedEvent;

// Fired when a banner list ad fails to load
public static event Action BannerListNoAdFoundEvent;

// Fired when a banner list ad is loaded
public static event Action BannerListAdLoadedEvent;

// Fired when a banner list ad is displayed
public static event Action BannerListAdShownEvent;

// Fired when a banner list ad is clicked
public static event Action BannerListAdClickedEvent;

// Fired when a banner list ad is closed
public static event Action BannerListAdClosedEvent;

// Fired when a banner wall ad fails to load
public static event Action BannerWallNoAdFoundEvent;

// Fired when a banner wall ad is loaded
public static event Action BannerWallAdLoadedEvent;

// Fired when a banner wall ad is displayed
public static event Action BannerWallAdShownEvent;

// Fired when a banner wall ad is clicked
public static event Action BannerWallAdClickedEvent;

// Fired when a banner wall ad is dismissed
public static event Action BannerWallAdDismissedEvent;
```

See also the Appyshka/Demo/Scripts/AppyshkaUIManager.cs to see an example how the presented API can be utilized.
