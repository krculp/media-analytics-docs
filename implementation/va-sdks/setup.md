# Set up and Configure

The following instructions provide guidance for implementation across all 2.x SDKs.

**Important:** The following instructions provide guidance for
implementation across all 2.x SDks. If you are implementing a 1.x version of
the SDK, you can download the Developers Guide further down the page.

## Implement

1. For mobile platforms, import the Heartbeat libraries. For JavaScript, create 
   local references to the classes. There are three classes/libraries to reference.  
   (For links to platforms and additional details, see the **Code** section below.)

   Libraries/Classes:

   * Media Heartbeat Config: The config contains the basic settings for reporting. 
   * Media Heartbeat Delegate: The delegate controls playback time and the QoS object. 
   * Media Heartbeat: The primary library containing members and methods. 

2. Create a MediaHeartbeatConfig Instance. 

   Set the config values on your `MediaHeartbeatConfig` instance for accurate tracking.

   |Variable Name|Description|Required|Default Value|
   |---|---|---|---|
   |`trackingServer`|Define the server for tracking media heartbeats. This is different from your analytics tracking server.|Yes|Empty String|
   |`channel`|Channel name property|Yes|Empty String|
   |`ovp`|Name of the online video platform through which content gets distributed.|No|Empty String|
   |`appVersion`|Version of the video player app/SDK.|Yes|unknown|
   |`playerName`|Name of the video player in use, i.e., "AVPlayer", "HTML5 Player", "My Custom VideoPlayer".|Yes|Empty String|
   |`ssl`|Property that indicates whether the heartbeat calls should be made over HTTPS.|Yes|false|
   |`debugLogging`|Gets the preference for debug log output.|Yes|false|

3. Implement the MediaHeartbeatDelegate: 

   |Method Name|Description|Required|
   |---|---|---|
   |`getQoSObject()`|Returns the MediaObject instance that contains the current QoS information. This method will be called multiple times during a playback session. Player implementation must always return the most recently available QoS data.|Yes|
   |`getCurrentPlaybackTime()`|Returns the current position of the playhead. For VOD tracking, the value is specified in seconds from the beginning of the media item. For LINEAR/LIVE tracking, the value is specified in seconds from the beginning of the program.|Yes|

   Tip: The QoS Object is not required. If the QoS data is available for your
   player, then the following variables are required to fully track Quality of
   Service.

   MediaObject (QoS Object) reference:

   |Variable name|Description|Required|
   |---|---|---|
   |`bitrate`|The bitrate of media in bits per second.|Yes|
   |`startupTime`|The start up time of media in milliseconds.|Yes|
   |`fps`|The frames displayed per second.|Yes|
   |`droppedFrames`|The number of dropped frames so far.|Yes|

  4. Create the MediaHeartbeat instance. 

   Use `MediaHeartbeatConfig` and `MediaHeartbeatDelegate` to create the
   `MediaHeartbeat` instance.
   
   **Important:** Make sure that your `MediaHeartbeat` instance is accessible and 
   does not get deallocated until the end of the video session. This instance will 
   be used for all the following video tracking events.
   
   **Tip:** `MediaHeartbeat` requires an instance of `AppMeasurement` to send 
   calls to Adobe Analytics.

  5. Combine all of the pieces. 

   The following sample code utilizes our JavaScript 2.x SDK for an HTML5 video
   player:

       ``` javascript
       // Create local references to the heartbeat classes
       var MediaHeartbeat = ADB.va.MediaHeartbeat;
       var MediaHeartbeatConfig = ADB.va.MediaHeartbeatConfig;
       var MediaHeartbeatDelegate = ADB.va.MediaHeartbeatDelegate;
       
       //Media Heartbeat Config
       var mediaConfig = new MediaHeartbeatConfig();
       mediaConfig.trackingServer = "namespace.hb.omtrdc.net";
       mediaConfig.playerName = "HTML5 Basic";
       mediaConfig.channel = "Video Channel";
       mediaConfig.debugLogging = true;
       mediaConfig.appVersion = "2.0";
       mediaConfig.ssl = false;
       mediaConfig.ovp = "";
       
       // Media Heartbeat Delegate
       var mediaDelegate = new MediaHeartbeatDelegate();
       
       // Set mediaDelegate CurrentPlaybackTime
       mediaDelegate.getCurrentPlaybackTime = function() {
           return video.currentTime;
       };
       
       // Set mediaDelegate QoSObject - OPTIONAL
       mediaDelegate.getQoSObject = function() {
           return MediaHeartbeat.createQoSObject(video.bitrate, 
                                                 video.startuptime, 
                                                 video.fps, 
                                                 video.droppedframes);
       }
       // Create mediaHeartbeat instance     
       this.mediaHeartbeat = 
         new MediaHeartbeat(mediaDelegate, mediaConfig, appMeasurementInstance); 
       ``` 

## Code

<table><title>Table 1. VA 2.x</title>
    <thead>
        <tr>
            <th>Video Analytics 2.x SDKs </th>
            <th>Developer Guides </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Android/FireTV </td>
            <td> [Configure for Android]() </td>
        </tr>
        <tr>
            <td>iOS/AppleTV </td>
            <td>[Configure for iOS]() </td>
        </tr>
        <tr>
            <td>JavaScript </td>
            <td> [Configure for JavaScript]() </td>
        </tr>
        <tr>
            <td>Roku </td>
            <td> [Configure for Roku]() </td>
        </tr>
        <tr>
            <td>Chromecast</td>
            <td>[Configure for Chromecast]() </td>
        </tr>
        <tr>
            <td>Primetime</td>
            <td>
                <ul>
                    <li>Android: [Configure Video Analytics]()</li>
                    <li>DHLS: [Configure Video Analytics]()</li>
                    <li>iOS: [Configure Video Analytics]()</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>
<table><title>Table 2. VA 1.x</title>
    <thead>
        <tr>
            <th>Video Analytics 1.x SDKs* </th>
            <th>Developer Guides </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Android </td>
            <td> [Configure for Android]() </td>
        </tr>
        <tr>
            <td>AppleTV </td>
            <td> [Configure for AppleTV]() </td>
        </tr>
        <tr>
            <td>Chromecast </td>
            <td> [Configure for Chromecast]() </td>
        </tr>
        <tr>
            <td>iOS </td>
            <td> [Configure for iOS]() </td>
        </tr>
        <tr>
            <td>JavaScript </td>
            <td> [Configure for JavaScript]() </td>
        </tr>
        <tr>
            <td>Primetime </td>
        <td>
            <ul>
                <li>Android: [Configure Video Analytics]()</li>
                <li>DHLS: [Configure Video Analytics]()</li>
                <li>iOS: [Configure Video Analytics]()</li>
            </ul>
        </td>
        </tr>
        <tr>
            <td>TVML </td>
            <td>[Configure for TVML]() </td>
        </tr>
    </tbody>
</table>

***** For all 1.x SDKs, the links are for the full PDF download of the documentation. 

## Validate

Video implementations are composed of two types of tracking calls:

* Video and Ad Start calls are sent directly to the AppMeasurement server. 
* Heartbeat calls are sent on start and every ten seconds to the Heartbeat tracking server. 

Video tracking will behave the same across all platforms, desktop and mobile.
Across all tracking calls there are a few key universal variables to be
validated:

* **AppMeasurement (Analytics)**

  For more information about tracking server options, see 
  [Correctly populate the trackingServer and trackingServerSecure variable](https://marketing.adobe.com/resources/help/kb/en_US/analytics/kb/determining-data-center.html).

  **Important:** An RDC tracking server or CNAME resolving to an RDC server is
  required for Experience Cloud Visitor ID service.

    The analytics tracking server should end in `.sc.omtrdc.net` or be a CNAME.

* **Video Heartbeat**

  Always has the format [namespace].hb.omtrdc.net, where [namespace] is defined
  by your login company and is provided by Adobe.

