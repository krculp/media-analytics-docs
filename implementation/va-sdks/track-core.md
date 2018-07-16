# Track Core Video Playback

Important: If you are implementing a 1.x version of the SDK, you can download
the 1.x Developers Guide further down this page.

## Overview

Core video playback includes tracking video starts, video completes, pausing,
and scrubbing. Utilize the video player API to identify key player events and
to populate the required and optional video variables. The following are the
key elements of tracking video playback; details for each item are below:

**On video load:**

  * Create the media object 
  * Populate the metadata 
  * Call trackSessionStart(mediaObject, contextData)

**On video start**: 

  * Call trackPlay()

**On video complete:**

  * Call trackComplete()
  * Call trackSessionEnd()

**On video pause:**

  * Call trackPause()
  * Call trackPlay() when the video resumes 

**On video scrub: **

  * Call trackEvent(MediaHeartbeat.Event.SeekStart)
  * Call trackEvent(MediaHeartbeat.Event.SeekComplete)

**On video buffer: **

  * Call trackEvent(MediaHeartbeat.Event.BufferStart);
  * Call trackEvent(MediaHeartbeat.Event.BufferComplete);

Tip: The playhead position is set as part of the set-up and configuration
code. For more information about getCurrentPlayheadTime(), see [Set up and
Configure](c_vhl_setup-and-
config.html#concept_425EDB4E08BA47EABBCDE3F02742EBD8).

## Implement

To implement core video playback:

1. Identify when the user triggers the intention of playback (user clicks play and/or autoplay is on) and create a MediaObject instance using the video information for video name, video ID, video length, and stream type. 

Here is the MediaObject reference:

|Variable Name|  Description|  Required|
|---|---|---|
|name| Video name| Yes|
|mediaid| Video unique identifier| Yes|
|length| Video length| Yes|
|streamType| Stream type (see constants MediaHeartbeat.StreamType.VOD)| Yes|

Here is the MediaHeartbeat.StreamType.VOD constants reference:

Constant Name  Description

VOD

Stream type for Video on Demand.

LIVE

Stream type for LIVE content.

LINEAR

Stream type for LINEAR content.

The general format for the MediaObject is
MediaHeartbeat.createMediaObject(<VIDEO_NAME>, <VIDEO_ID>, <VIDEO_LENGTH>,
<STREAM_TYPE>.VOD);

    
    var mediaObject = 
      MediaHeartbeat.createMediaObject("Name", "ID", VIDEO_LENGTH, MediaHeartbeat.StreamType.VOD);

2. Attach all custom video metadata and standard video metadata to the video tracking session through context data variables. 

For custom metadata, create a variable object for the custom variables and
populate with the data for this video. For example:

    
    /* Set custom context data */
    var customVideoMetadata = {
        isUserLoggedIn: "false",
        tvStation: "Sample TV station",
        programmer: "Sample programmer"
    };
    

For standard metadata, instantiate the standardVideoMetdata object and
populate the desired variables. For a complete list of standard metadata
variables, see [Metrics and Metadata](c_vhl_metrics-and-metadata.html). For
example:

    
    var standardVideoMetadata = {};
    standardVideoMetadata[MediaHeartbeat.VideoMetadataKeys.EPISODE] = "Sample Episode";
    standardVideoMetadata[MediaHeartbeat.VideoMetadataKeys.SHOW] = "Sample Show";
    mediaObject.setValue(MediaHeartbeat.MediaObjectKey.StandardVideoMetadata, standardVideoMetadata);   
    

Tip: Attaching standardVideoMetadata to mediaObject is optional.

3. To begin tracking a video session, call trackSessionStart in the MediaHeartbeat instance. 

Tip: The second value is the custom video metadata object name that you
created in step 2.

    
    mediaHeartbeat.trackSessionStart(mediaObject, customVideoMetadata);

Important: trackSessionStart() tracks the user intention of playback, not the
beginning of the playback. This API is used to load the video data/metadata
and to estimate the time-to-start QoS metric (the time duration between
trackSessionStart() and trackPlay()).

Tip: If you are not using custom video metadata, simply send an empty object
for the data argument in trackSessionStart(). For example:

mediaHeartbeat.trackSessionStart(mediaObject, data)

4. Identify the event from the video player for the beginning of the video playback, where the first frame of the video is rendered on the screen, and call trackPlay(): 
    
    mediaHeartbeat.trackPlay();

5. Identify the event from the video player for the completion of the video playback, where the user has watched the content until the end, and call trackComplete(): 
    
    mediaHeartbeat.trackComplete();

6. Identify the event from the video player for the unloading/closing of the video playback, where the user closes the video and/or the video is completed and has been unloaded, and call trackSessionEnd(): 
    
    mediaHeartbeat.trackSessionEnd();

Important: trackSessionEnd() marks the end of a video tracking session. If the
session was successfully watched to completion, where the user watched the
content until the end, ensure that trackComplete() is called before
trackSessionEnd(). Any other track*() API call is ignored after
trackSessionEnd(), except for trackSessionStart() for a new video tracking
session.

7. Identify the event from the video player for video pause and call trackPause(). 
    
    mediaHeartbeat.trackPause();

Tip: Identify any scenario in which the Video Player will pause and make sure
that trackPause() is properly called. Sample scenarios include when an
application goes to the background or the player automatically pauses because
of a mobile interrupt.

8. Identify the event from the video player for video play and/or video resume from pause and call trackPlay(). 
    
    mediaHeartbeat.trackPlay();

9. Identify the event from the video player for scrubbing/seeking and utilize a custom MediaHeartbeat event to capture the action. 
    
    mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekStart);

10. Identify the event from the video player for video play and/or video resume from scrubbing/seeking and use a second custom MediaHeartbeat event. 
    
    mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete)

11. Listen for playback buffering to start and use a custom MediaHeartbeat event to capture the change. 
    
    mediaHeartbeat.trackEvent (MediaHeartbeat.Event.BufferStart);

12. Identify when buffering ends and call the MediaHeartbeat event to capture the change. 
    
    mediaHeartbeat.trackEvent (MediaHeartbeat.Event.BufferComplete);

The following sample code uses the JavaScript 2.x SDK for an HTML5 video
player:

    
    /* Call on video start */
    if (e.type == "play") {
    
        // Check for start of video
        if (mediaOffset == 0) {
            /* Set media info */    
            /* MediaHeartbeat.createMediaObject(<VIDEO_NAME>, 
                                                <VIDEO_ID>, 
                                                <VIDEO_LENGTH>,
                                                MediaHeartbeat.StreamType.VOD);*/
            var mediaInfo = MediaHeartbeat.createMediaObject(
              document.getElementsByTagName('video')[0].getAttribute("name"), 
              document.getElementsByTagName('video')[0].getAttribute("id"), 
              video.duration,
              MediaHeartbeat.StreamType.VOD);
    
            /* Set custom context data */
            var customVideoMetadata = {
                isUserLoggedIn: "false",
                tvStation: "Sample TV station",
                programmer: "Sample programmer"
            };
    
            /* Set standard video metadata */    
            var standardVideoMetadata = {};
            standardVideoMetadata[MediaHeartbeat.VideoMetadataKeys.EPISODE] = "Sample Episode";
            standardVideoMetadata[MediaHeartbeat.VideoMetadataKeys.SHOW] = "Sample Show";
            mediaInfo.setValue(MediaHeartbeat.MediaObjectKey.StandardVideoMetadata, 
                               standardVideoMetadata);    
    
            // Start Session
            this.mediaHeartbeat.trackSessionStart(mediaInfo, customVideoMetadata);   
    
            // Track play
            this.mediaHeartbeat.trackPlay();     
    
        } else {
            // Track play for resuming playack   
            this.mediaHeartbeat.trackPlay(); 
        }
    };
    
    /* Call on video complete */
    if (e.type == "ended") {
        console.log("video ended");
        this.mediaHeartbeat.trackComplete();
        this.mediaHeartbeat.trackSessionEnd();
        mediaOffset = 0;    
    };
    
    /* Call on pause */
    if (e.type == "pause") {
        this.mediaHeartbeat.trackPause();
    };
    
    /* Call on scrub start */
    if (e.type == "seeking") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekStart);
    };
        
    /* Call on scrub stop */
    if (e.type == "seeked") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete);
    };
    
    /* Call on buffer start */
    if (e.type == “buffering”) {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferStart);
    };
    
    /* Call on buffer complete */
    if (e.type == “buffering end”) {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete);
    };
    

## Code

|Video Analytics 2.x SDKs  |Developer Guides|
|---|---|
|Android/FireTV| [Track Core for Android](https://marketing.adobe.com/resources/help/en_US/sc/a
ppmeasurement/hbvideo/android_2.0/t_vhl_track-core-playback_android.html)|
| iOS/AppleTV| [Track Core for iOS](https://marketing.adobe.com/resources/help/en_US/sc/appme
asurement/hbvideo/ios_2.0/t_vhl_track-core-playback_ios.html)|
| JavaScript| [Track Core for JavaScript](https://marketing.adobe.com/resources/help/en_US/s
c/appmeasurement/hbvideo/js_2.0/t_vhl_track-core-playback_js.html)|
| Roku| [Track Core for Roku](https://marketing.adobe.com/resources/help/en_US/sc/appm
easurement/hbvideo/roku/c_vhl_conf-med-hrbts.html)|
| Chromecast| [Track Core for Chromecast](https://marketing.adobe.com/resources/help/en_US/s
c/appmeasurement/hbvideo/chromecast/c_vhl_conf-med-hrbts-chromecast.html)|

|Video Analytics 1.x SDKs*  |Developer Guides|
| Android| [Track Core for Android](vhl-dev-guide-v15_android.pdf)|
| AppleTV| [Track Core for AppleTV](vhl-dev-guide-v1x_appletv.pdf)|
| Chromecast| [Track Core for Chromecast](chromecast_1.x_sdk.pdf)|
| iOS| [Track Core for iOS](vhl-dev-guide-v15_ios.pdf)|
| JavaScript| [Track Core for JavaScript](vhl-dev-guide-v15_js.pdf)|

Primetime

  * **Android**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/android/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)
  * **DHLS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/dhls/index.html#PSDKs-task-Initialize_and_configure_video_analytics_%20)
  * **iOS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)

TVML

[Track Core for TVML](vhl_tvml.pdf)

***** For all 1.x SDKs, the links are for the full PDF download of the documentation. 

## Validate

**Video Start**

On start of a video player, these key calls are sent in the following order:

1. Video analytics start*****
2. Heartbeat start*****
3. Heartbeat analytics start 

*****These calls contain additional metadata variables for both custom and standard. 

**Content Play**

During regular main content playback, Heartbeat calls are sent to the
Heartbeat server every ten seconds.

**Video Complete**

At the 100% point, on a video or at a show boundary on a linear stream, a
Heartbeat complete call will be sent.

**Content Pause**

When the video player pauses, video player pause event calls will be sent
every 10 seconds. After pause ends, the play events should resume.

**Content Scrub/Seek**

On scrubbing of the video playhead, no special tracking calls are sent.
However, when video playback resumes after scrubbing, the playhead value
should reflect the new position in the main content.

**Content Buffer**

When the video player buffers, video player buffer event calls will be sent
every 10 seconds. After buffer ends, the play events should resume.

