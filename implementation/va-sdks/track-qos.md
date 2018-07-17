#  Track Quality of Experience

**Important:** The following instructions provide guidance for implementation
across all 2.x SDKs. If you are implementing a 1.x version of the SDK, you can
download the Developers Guide further down this page.

## Overview

Quality of experience tracking includes quality of service (QoS) and error
tracking, both are optional elements and are **not** required for core video
heartbeat implementations. You can use the video player API to identify the
variables related to QoS and error tracking. Here are the key elements of
tracking quality of experience:

* On all bitrate change events: 
  * Create/update the QoS object instance for the playback, qosObject
  * Call `trackEvent(Media.Heartbeat.Event.BitrateChange, qosObject)`

* On player errors: 
  * Call `trackError(“video error id”)`

## Implement

To implement quality of experience and error tracking:

1. Identify when the bitrate changes during video playback and create the MediaObject instance using the QoS information. 

   QoSObject reference:
   
   |**Variable Name**|**Description**|**Required**|
   |---|---|---|
   |bitrate|Current bitrate|Yes|
   |startupTime|Startup time|Yes|
   |fps|FPS value|Yes|
   |droppedFrames|Number of dropped frames|Yes|
   
   **Tip:** These variables are only required if you are planning to track QoS.
   
   The general format of the QoS object is:
       
   ``` javascript
   var qosObject = 
     MediaHeartbeat.createQoSObject(<bitrate>, 
                                    <startuptime>, 
                                    <fps>, 
                                    <droppedFrames>);
   ```

2. When playback switches bitrates, call the BitrateChange event in the MediaHeartbeat instance. 
    
   ``` javascript
   mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange, qosObject);
   ```

   **Important:** Update the QoS object and call the bitrate change event on every
   bitrate change. This provides the most accurate QoS data.

3. Make sure the MediaHeartbeatDelegate.getQoSObject() method returns the most updated QoS information. 

4. When the video player encounters an error, and the error event is available to the player API, use the `trackError()` `MediaHeartbeat` event to capture the error information. 
    
   ``` javascript
   mediaHeartbeat.trackError("videoErrorId");
   ```

   **Tip:** Tracking video player errors will not stop the video tracking session. If
   the video player error prevents the playback from continuing, make sure that
   the video tracking session is closed by calling `trackSessionEnd()` after
   calling `trackError()`.
   
   The following sample code uses the JavaScript 2.x SDK for an HTML5 video
   player. You should use this code with the core video playback code.
    
   ``` javascript
   /* Call on bitrate change */
   if (e.type == "bitrate change") {
       var qosObject = MediaHeartbeat.createQoSObjectt(24,5,29,2);
       this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange, qosObject);
   };
   
   /*Call on player error*/
   if (e.type == "error") {
       this.mediaHeartbeat.trackError("video error 10345");
   };
   ```

## Code

|**Video Analytics 2.x SDKs**|**Developer Guides**|
|---|---|
|Android/FireTV| [Track Quality for Android](track-bitrate-changes_android.md)|
| iOS/AppleTV| [Track Quality for iOS](track-bitrate-changes_ios.md)|
| JavaScript| [Track Quality for JavaScript](track-bitrate-changes_js.md)|
| Roku| [Track Quality for Roku](conf-med-hrbts.md)|
| Chromecast| [Track Quality for Chromecast](conf-med-hrbts-chromecast.md)|

|**Video Analytics 1.x SDKs\* **|**Developer Guides**|
|---|---|
| Android| [Track Quality for Android](vhl-dev-guide-v15_android.pdf)|
| AppleTV| [Track Quality for AppleTV](vhl-dev-guide-v1x_appletv.pdf)|
| Chromecast| [Track Quality for Chromecast](chromecast_1.x_sdk.pdf)|
| iOS| [Track Quality for iOS](vhl-dev-guide-v15_ios.pdf)|
| JavaScript| [Track Quality for JavaScript](vhl-dev-guide-v15_js.pdf)|
| Primetime|\[**Android**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/android/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)\] \[**DHLS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/dhls/index.html#PSDKs-task-Initialize_and_configure_video_analytics_%20)\] \[**iOS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)\]|
| TVML| [Track Quality for TVML](vhl_tvml.pdf)|

\* For all 1.x SDKs, the links are for the full PDF download of the documentation. 

## Validate

###Bitrate change

On each bitrate change, a Heartbeat bitrate_change call will be sent, which
includes the QoS variables.

###Error

On player error, a Heartbeat error call will be sent with the error value
included.

