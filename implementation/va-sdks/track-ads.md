# Track Ads

**Important:** The following instructions provide guidance for implementation
across all 2.x SDKs. If you are implementing a 1.x version of the SDK, you can
download the Developers Guide further down this page.

## Overview

Ad playback includes tracking ad breaks, ad starts, ad completes, and ad
skips. You can use the video player's API to identify key player events and to
populate the required and optional ad variables.

Here are the key elements to track ad playback:
* On ad break start, including pre-roll
  * Create the `adBreak` object instance for the ad break, for example, `adBreakObject`. 
  * Call `trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakObject);`. 

* On every ad asset start
  * Create the ad object instance for the ad asset, for example, `adObject`. 
  * Populate the ad metadata, `adCustomMetadata`. 
  * Call `trackEvent(MediaHeartbeat.Event.AdStart, adObject, adCustomMetadata);`. 

* On every ad asset complete
  * Call `trackEvent(MediaHeartbeat.Event.AdComplete);`. 

* On ad skip
  * Call `trackEvent(MediaHeartbeat.Event.AdSkip);`. 

* On ad break complete
  * Call `trackEvent(MediaHeartbeat.Event.AdBreakComplete);`. 

## Implement

To implement ad playback:

1. Identify when the ad break boundary begins, including pre-roll, and create an AdBreakObject by using the ad break information. 

   Here is the Ad break object reference:

   |**Variable Name**|**Description**|**Required**|
   |---|---|---|
   |name| Ad break name such as pre-roll, mid-roll, and post-roll.| Yes |
   |position| The number position of the ad break starting with 1.|  Yes|
   |startTime| Playhead value at the start of the ad break.| Yes|
   
   The general format for the ad break object is:
    
   ``` javascript
   var adBreakObject = 
     MediaHeartbeat.createAdBreakObject(<ADBREAK_NAME>, <POSITION>, <START_TIME>);
   ```

2. Call `trackEvent()` with `AdBreakStart` in the `MediaHeartbeat` instance to begin tracking the ad break. 
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakObject);
   ```

3. Identify when the ad asset starts and create an AdObject instance using the ad information. 

   Here is the AdObject reference:
   
   |**Variable Name**|**Description**|**Required**|
   |---|---|---|
   |name| Friendly name of the ad asset.| Yes|
   |adId| Unique identified for the ad asset.| Yes|
   |position| The number position of the asset in the ad break, starting with 1.| Yes|
   |length| Ad asset length| Yes|
   
   The general format for the ad object is:
    
   ``` javascript
   var adObject = MediaHeartbeat.createAdObject(<AD_NAME>, <AD_ID>, <POSITION>, <LENGTH>);
   ```

4. Attach all the custom ad metadata to the video tracking session through context data variables. 

   For custom metadata, create a variable object for the custom data variables
   and populate with the data for the current ad asset. For example:
    
   ``` javascript
    /* Set custom context data */
    var adCustomMetadata = {
        affiliate: "Sample affiliate",
        campaign: "Sample ad campaign",
        creative: "Sample creative"
    };
   ```

5. Call `trackEvent()` with the `AdStart` event in the `MediaHeartbeat` instance 
   to begin tracking the ad playback.  Be sure to include a reference to your 
   custom metadata variable as the third parameter in the event call:
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, 
                             adObject, 
                             adCustomMetadata);
   ```

6. When the ad asset playback reaches the end of the ad, call trackEvent() with 
   the AdComplete event. 
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete);
   ```

7. If ad playback did not complete because the user chose to skip the ad, track the AdSkip event. 
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdSkip);
   ```

8. When the ad break is complete, use the AdBreakComplete event to track. 
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete);
   ```

   The following sample code utilizes our JavaScript 2.x SDK for an HTML5 video player.
    
   ``` javascript
    /* Call on ad break start */
    
    if (e.type == "ad break start") {
        var adBreakObject = MediaHeartbeat.createAdBreakObject("mid-roll", 2, 500);
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakObject);
    };
    
    /* Call on ad start */
    if (e.type == "ad start") {
        var adObject = MediaHeartbeat.createAdObject("PepsiOne", "123456ab", 1, 30);
        /* Set custom context data */
        var adCustomMetadata = {
            affiliate:"Sample affiliate",
            campaign:"Sample ad campaign",
            creative:"Sample creative"
        }
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adObject, adCustomMetadata);
    };
    
    /* Call on ad complete */
    if (e.type == "ad complete") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete);
    };
    
    /* Call on ad skip */
    if (e.type == "ad skip") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdSkip);
    };
        
    /* Call on ad break complete */
    if (e.type == "ad break complete") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete);
    };
   ```

## Code

|**Video Analytics 2.x SDKs**|**Developer Guides**|
|---|---|
|Android/FireTV| [Track Ads for Android](track-ads_android.md)|
|iOS/AppleTV| [Track Ads for iOS](track-ads_ios.md)|
|JavaScript| [Track Ads for JavaScript](track-ads_js.md)|
|Roku| [Track Ads for Roku](conf-med-hrbts.md)|
|Chromecast| [Track Ads for Chromecast](conf-med-hrbts-chromecast.md)|

|**Video Analytics 1.x SDKs\* **|**Developer Guides**|
|---|---|
|Android| [Track Ads for Android](vhl-dev-guide-v15_android.pdf)|
|AppleTV| [Track Ads for AppleTV](vhl-dev-guide-v1x_appletv.pdf)|
|Chromecast| [Track Ads for Chromecast](chromecast_1.x_sdk.pdf)|
|iOS| [Track Ads for iOS](vhl-dev-guide-v15_ios.pdf)|
|JavaScript| [Track Ads for JavaScript](vhl-dev-guide-v15_js.pdf)|
|Primetime| **Android**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/android/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_) **DHLS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/dhls/index.html#PSDKs-task-Initialize_and_configure_video_analytics_%20) **iOS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)|
|TVML| [Track Ads for TVML](vhl_tvml.pdf)|

\* For all 1.x SDKs, the links are for the full PDF download of the documentation. 

## Validate

##Ad Start

On start of an individual ad playback, three key calls are sent in the
following order:

1. Video ad analytics start\*
2. Heartbeat ad start\*
3. Heartbeat analytics start 

\* These calls contain additional metadata variables for both custom and standard. 

###Ad Play

During ad playback, Heartbeat ad play calls are sent to the Heartbeat server
every ten seconds.

###Ad Complete

At the 100% point on an ad, a Heartbeat ad complete call will be sent.

###Ad Skip

When an ad is skipped, no events are sent, so the tracking calls will not
include the ad information.

**Tip:** No unique calls are sent on ad break start and ad break complete.
