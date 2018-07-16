# Track Chapters and Segments

Important: The following instructions provide guidance for implementation
across all 2.x SDKs. If you are implementing a 1.x version of the SDK, you can
download the Developers Guide further down this page.

## Overview

Chapter and segment tracking is available for custom-defined video chapters or
segments. Some common uses for chapter tracking are to define custom segments
based on video content, such as baseball innings, or to define content
segments between ad breaks. Chapter tracking is **not** required for core
video heartbeat implementations.

Chapter tracking includes chapter starts, chapter completes, and chapter
skips. You can use the video player API with customized segmentation logic to
identify chapter events and to populate the required and optional chapter
variables. Here are the key elements of tracking chapter playback:

Tip: Additional details for each section is available in the [Implement
](c_vhl_track-chap-segments.html#concept_8B95F957C85C4B23A1E934A094471998__sec
tion_52221B3A9BFD46B3A22DA6BCE97CCD75) section.

**On chapter start**: 

  * Create the chapter object instance for the chapter, chapterObject 
  * Populate the chapter metadata, chapterCustomMetadata
  * Call trackEvent(MediaHeartbeat.Event.ChapterStart, chapterObject, chapterCustomMetadata);

**On chapter complete**: 

  * Call trackEvent(MediaHeartbeat.Event.ChapterComplete); 

**On chapter skip**: 

  * Call trackEvent(MediaHeartbeat.Event.ChapterSkip);

## Implement

To implement custom video chapters:

1. Identify when the chapter start event occurs and create the ChapterObject instance by using the chapter information. 

Here is the ChapterObject chapter tracking reference:

|Variable Name|  Description|  Required|
|---|---|---|
|name| Chapter name| Yes|
|position| Chapter position| Yes|
|length| Chapter length| Yes|
|startTime| Chapter start time| Yes|

Tip: These variables are only required if you are planning to track chapters.

The general format of the chapter object is:

    
    var chapterObject = 
      MediaHeartbeat.createChapterObject(<CHAPTER_NAME>, <POSITION>, <LENGTH>, <START_TIME>);

2. If you include custom metadata for the chapter, create the context data variables for the metadata. 
    
    /* Set custom context data */
    var chapterCustomMetadata = {
        segmentType: "Sample segment type",
        segmentName: "Sample segment name",
        segmentInfo: "Sample segment info"
    };
    

3. To begin tracking the chapter playback, call the ChapterStart event in the MediaHeartbeat instance. 
    
    mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart, 
                                          chapterObject,
                                          chapterCustomMetadata);

4. When playback reaches the chapter end boundary, as defined by your custom code, call the ChapterComplete event in the MediaHeartbeat instance. 
    
    mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);

5. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the ChapterSkip event in the MediaHeartbeat instance. 
    
    mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);

The following sample code uses the JavaScript 2.x SDK for an HTML5 video
player. You should use this code with the core video playback code.

    
    /* Call on chapter start */
    if (e.type == "chapter start") {
        var chapterObject = MediaHeartbeat.createChapterObject("Inning 5",5,500,2500);
        /* Set custom context data*/
        var chapterCustomMetadata = {
            segmentType:"Baseball Innings",
            segmentName:"Inning 5",
            segmentInfo:"Game Six"
        }
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart, 
                                       chapterObject, 
                                       chapterCustomMetadata);
    };
    
    /* Call on chapter complete */
    if (e.type == "chapter complete") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);
    };
    
    /* Call on chapter skip */
    if (e.type == "chapter skip") {
        this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);
    };
    

## Code

|Video Analytics 2.x SDKs  |Developer Guides|
|---|---|
|Android/FireTV| [Track Chapters for Android](https://marketing.adobe.com/resources/help/en_US/
sc/appmeasurement/hbvideo/android_2.0/t_vhl_track-chap_android.html)|
| iOS/AppleTV| [Track Chapers for iOS](https://marketing.adobe.com/resources/help/en_US/sc/ap
pmeasurement/hbvideo/ios_2.0/t_vhl_track-chap_ios.html)|
| JavaScript| [Track Chapters for JavaScript](https://marketing.adobe.com/resources/help/en_
US/sc/appmeasurement/hbvideo/js_2.0/t_vhl_track-chap_js.html)|
| Roku| [Track Chapters for Roku](https://marketing.adobe.com/resources/help/en_US/sc/
appmeasurement/hbvideo/roku/c_vhl_conf-med-hrbts.html)|
| Chromecast| [Track Chapters for Chromecast](https://marketing.adobe.com/resources/help/en_
US/sc/appmeasurement/hbvideo/chromecast/c_vhl_conf-med-hrbts-chromecast.html)|

|Video Analytics 1.x SDKs*  |Developer Guides|
| Android| [Track Chapters for Android](vhl-dev-guide-v15_android.pdf)|
| AppleTV| [Track Chapters for AppleTV](vhl-dev-guide-v1x_appletv.pdf)|
| Chromecast| [Track Chapters for Chromecast](chromecast_1.x_sdk.pdf)|
| iOS| [Track Chapters for iOS](vhl-dev-guide-v15_ios.pdf)|
| JavaScript| [Track Chapters for JavaScript](vhl-dev-guide-v15_js.pdf)|

Primetime

  * **Android**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/android/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)
  * **DHLS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/dhls/index.html#PSDKs-task-Initialize_and_configure_video_analytics_%20)
  * **iOS**: [Configure Video Analytics](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-task-Initialize_and_configure_video_analytics_)

TVML

[Track Chapters for TVML](vhl_tvml.pdf)

***** For all 1.x SDKs, the links are for the full PDF download of the documentation. 

## Validate

**Chapter Start **

On start of an individual chapter playback, one key calls are sent:

  * Heartbeat chapter start*****

*****This call contains additional chapter metadata variables. 

**Chapter Complete**

At the chapter boundary end, a Heartbeat chapter complete call will be sent.

**Chapter Skip**

When a chapter is skipped, a Heartbeat chapter skip call will be sent.

