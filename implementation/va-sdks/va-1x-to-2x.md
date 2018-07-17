# VHL 1.x to 2.x API Conversion

## Migration Overview

The migration from VHL 1.x to VHL 2.x is straightforward, with the new version
featuring simplified APIs for initialization, configuration, and player
delegates.

Here are the primary differences between 1.x and 2.x:

  * **Plugins, Delegates** - You no longer need to implement plugins and delegates for Analytics, VideoPlayer, and Heartbeat. 
  * **Configuration** - You no longer need to instantiate configurations for the 1.x plugins. 

In versions 2.x, all of the public methods are consolidated into the
MediaHeartbeat class to make it easier on developers. Also, all configs are
now consolidated into the MediaHeartbeatConfig class. These new APIs are
described in detail here: [VHL 1.x to 2.x API Conversion](vhl-mig-1x-2x-api-
change-reference.html).

In version 2.x, you do not need to implement plugins or delegates for
Analytics, VideoPlayer, or Heartbeat. Also, you no longer need to instantiate
configs for all of these plugins. In the 2.x SDK you only need to instantiate
the MediaHeartbeat class with MediaHeartbeatDelegate and MediaHeartbeatConfig
instances. This is the only implementation that is required to initialize
Video Analytics.

With the initialization of MediaHeartbeat, you can safely delete all of the
implementation for Analytics Plugin, VideoPlayer Plugin and Heartbeat Plugin.
Also, remove all the existing implementation for VideoHeartbeat initialization
that takes in an array of plugins as an input. You can see side-by-side
comparisons of the 1.x and 2.x implementations here: [VHL Code Comparison: 1.x
to 2.x](vhl-mig-1x-2x-comp-table.html)

## VHL Code Comparison: 1.x to 2.x

All of the VHL configuration parameters and tracking APIs are now consolidated
into the MediaHeartbeats and MediaHeartbeatConfig classes.

**Configuration API changes:**

  * AdobeHeartbeatPluginConfig.sdk - Renamed to MediaConfig.appVersion

  * MediaHeartbeatConfig.playerName - Now set through MediaHeartbeatConfig instead of VideoPlayerPluginDelegate

  * (For JavaScript only): The AppMeasurement instance - Now sent through the MediaHeartbeat constructor.

**Configuration properties changes:**

  * sdk - Renamed to appVersion
  * publisher - Removed; Experience Cloud Org ID is used instead as a publisher
  * quiteMode - Removed

The following tables provide side-by-side code comparisons between VHL 1.x and
VHL 2.x, covering Initialization, Core Playback, Ad Playback, Chapter
Playback, and some additional events.

Table 1. VHL Code Comparison: INITIALIZATION

VHL 1.x API  VHL 2.x API

_**Object Initialization**_

**1.x:**

  * Heartbeat()
  * VideoPlayerPlugin() 
  * AdobeAnalyticsPlugin() 
  * HeartbeatPlugin()

...

**2.x:**

  * MediaHeartbeat()
  * MediaHeartbeatConfig()

**Set up the video player plugin: **
    
    this._playerPlugin = 
     new VideoPlayerPlugin(
        new SampleVideoPlayerPluginDelegate(this._player));
    var playerPluginConfig = 
      new VideoPlayerPluginConfig();
    playerPluginConfig.debugLogging = true; 
    
    // Set up the AppMeasurement plugin
    this._aaPlugin = 
     new AdobeAnalyticsPlugin(
        appMeasurement, 
        new SampleAdobeAnalyticsPluginDelegate());
    var aaPluginConfig = new AdobeAnalyticsPluginConfig();
    
    aaPluginConfig.channel = 
      Configuration.HEARTBEAT.CHANNEL;
    
    aaPluginConfig.debuglogging = true; 
    this._aaPlugin.configure(aaPluginConfig); 
    
    // Set up the AdobeHeartbeat plugin
    var ahPlugin = 
      new AdobeHeartbeatPlugin(
        new SampleAdobeHeartbeatPluginDelegate());
    var ahPluginConfig = new AdobeHeartbeatPluginConfig(
        configuration.HEARTBEAT.TRACKING_SERVER,
        configuration.HEARTBEAT.PUBLISHER);
    ahPluginConfig.ovp = configuration.HEARTBEAT.OVP;
    ahPluginConfig.sdk = configuration.HEARTBEAT.SDK;
    ahPluginConfig.debugLogging = true; 
    ahPlugin.configure(ahPluginConfig);
    
    var plugins = 
      [this._playerPlugin, this._aaPlugin, ahPlugin];
    
    // Set up and configure the heartbeat library
    this._heartbeat = 
     new Heartbeat(new SampleHeartbeatDelegate(), 
                   plugins);
    var configData = new HeartbeatConfig();
    configData.debugLogging = true; 
    this._heartbeat.configure(configData);

[1.x Sample Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L58)

...

**Media Heartbeat initialization: **
    
    
    var mediaConfig = 
      new MediaHeartbeatConfig();
    mediaConfig.trackingServer = 
      Configuration.HEARTBEAT.TRACKING_SERVER; 
    mediaConfig.playerName = 
      Configuration.PLAYER.NAME;
    mediaConfig.debugLogging = true;
    mediaConfig.channel = 
      Configuration.HEARTBEAT.CHANNEL;
    mediaConfig.ssl = false;
    mediaConfig.ovp = 
      Configuration.HEARTBEAT.OVP;
    mediaConfig.appVersion = 
      Configuration.HEARTBEAT.SDK;
    
    this._mediaHeartbeat = new MediaHeartbeat(
         new SampleMediaHeartbeatDelegate(this._player),
         mediaConfig, 
         appMeasurement);

[2.x Sample Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L47)

...

_**Delegates**_

**1.x:**

  * VideoPlayerPluginDelegate()
  * VideoPlayerPluginDelegate().getVideoInfo
  * VideoPlayerPluginDelegate().getAdBreakInfo
  * VideoPlayerPluginDelegate().getAdInfo
  * VideoPlayerPluginDelegate().getChapterInfo
  * VideoPlayerPluginDelegate().getQoSInfo
  * VideoPlayerPluginDelegate().get.onError
  * AdobeAnalyticsPluginDelegate()
  * AdobeHeartbeatPluginDelegate()

...

**2.x:**

  * MediaHeartbeatDelegate()
  * MediaHeartbeatDelegate().getCurrentPlaybackTime
  * MediaHeartbeatDelegate().getQoSObject

**VideoPlayerPluginDelegate: **
    
    
    $.extend(SampleVideoPlayerPluginDelegate.prototype, 
             VideoPlayerPluginDelegate.prototype);
    
    function SampleVideoPlayerPluginDelegate(player) {
        this._player = player;
    }
    
    SampleVideoPlayerPluginDelegate.prototype.getVideoInfo = 
      function() { 
          return this._player.getVideoInfo(); 
      };
    
    SampleVideoPlayerPluginDelegate.prototype.getAdBreakInfo = 
      function() { 
          return this._player.getAdBreakInfo(); 
      };
    
    SampleVideoPlayerPluginDelegate.prototype.getAdInfo = 
      function() { 
          return this._player.getAdInfo(); 
      };
    
    SampleVideoPlayerPluginDelegate.prototype.getChapterInfo = 
      function() { 
          return this._player.getChapterInfo(); 
      };
    
    SampleVideoPlayerPluginDelegate.prototype.getQoSInfo = 
      function() { 
          return this._player.getQoSInfo(); 
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video
.player.plugin.delegate.js#L17)

...

**AdobeAnalyticsPluginDelegate: **
    
    
    $.extend(SampleAdobeAnalyticsPluginDelegate.prototype, 
             AdobeAnalyticsPluginDelegate.prototype);
    
    function SampleAdobeAnalyticsPluginDelegate() {}
    
    SampleAdobeAnalyticsPluginDelegate.prototype.onError = 
      function(errorInfo) {
          console.log("AdobeAnalyticsPlugin error: " + 
                       errorInfo.getMessage() + 
                       " | " + 
                       errorInfo.getDetails());
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.adobe
.analytics.plugin.delegate.js#L17)

...

**HeartbeatDelegate: **
    
    
    $.extend(SampleHeartbeatDelegate.prototype, 
             HeartbeatDelegate.prototype);
    
    function SampleHeartbeatDelegate() {}
    
    SampleHeartbeatDelegate.prototype.onError = 
      function(errorInfo) {
          console.log("Heartbeat error: " + 
                      errorInfo.getMessage() + 
                      " | " + 
                      errorInfo.getDetails());
    };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.heart
beat.delegate.js#L17)

**MediaHeartbeatDelegate: **
    
    
    ADB.core.extend(SampleMediaHeartbeatDelegate.prototype, 
      MediaHeartbeatDelegate.prototype);
    
    function SampleMediaHeartbeatDelegate(player) {
       this._player = player;
    }
    
    SampleMediaHeartbeatDelegate.prototype.getCurrentPlaybackTime = 
      function() {
          return this._player.getCurrentPlaybackTime();
      };
    
    SampleMediaHeartbeatDelegate.prototype.getQoSObject = 
      function() {
          return this._player.getQoSInfo();
      };
    
    this._mediaHeartbeat = 
      new MediaHeartbeat(new 
            SampleMediaHeartbeatDelegate(this._player), 
            mediaConfig, 
            appMeasurement);

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L57)

...

Table 2. VHL Code Comparison: CORE PLAYBACK

VHL 1.x VHL 2.x

_**Session Start**_

**1.x:**

  * VideoPlayerPluginDelegate.trackVideoLoad()
  * VideoPlayerPluginDelegate.getVideoInfo()

...

**2.x:**

  * MediaHeartbeat.createMediaObject()
  * MediaHeartbeat.trackSessionStart()
    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        this._playerPlugin.trackVideoLoad();
    };
    
    SampleVideoPlayerPluginDelegate.prototype.getVideoInfo
      = function() {
        return this._player.getVideoInfo();
    };
    
    VideoPlayer.prototype.getVideoInfo = function() {
        this._videoInfo.playhead = vTime;
        return this._videoInfo;
    };

[1.x Sample Player - trackVideoLoad()](https://github.com/Adobe-Marketing-
Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app
/analytics/video.analytics.provider.js#L107)

[1.x Sample Player - getVideoInfo()](https://github.com/Adobe-Marketing-Cloud
/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/anal
ytics/sample.video.player.plugin.delegate.js#L23)

...

    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        var contextData = {};
        var videoInfo = this._player.getVideoInfo();
        var mediaInfo = 
          MediaHeartbeat.createMediaObject(
            videoInfo.name, 
            videoInfo.id, 
            videoInfo.length,
            videoInfo.streamType);
    
        this._mediaHeartbeat.trackSessionStart(
          mediaInfo, 
          contextData);
    };

[2.x Sample Player - createMediaObject()](https://github.com/Adobe-Marketing-
Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/
app/analytics/video.analytics.provider.js#L88)

...

_**Standard Video Metadata**_

**1.x:**

  * VideoMetadataKeys()
  * AdobeAnalyticsPlugin.setVideoMetadata90

...

**2.x:**

  * MediaHeartbeat.createMediaObject()
  * MediaHeartbeat.trackSessionStart()
    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        console.log('Player event: VIDEO_LOAD');
    
        var contextData = {};
        // Setting Standard Video Metadata
        contextData[VideoMetadataKeys.SEASON] = 
          "sample season";
        contextData[VideoMetadataKeys.SHOW] = 
          "sample show";
        contextData[VideoMetadataKeys.EPISODE] = 
          "sample episode";
        contextData[VideoMetadataKeys.ASSET_ID] = 
          "sample asset id";
        contextData[VideoMetadataKeys.GENRE] = 
          "sample genre";
        contextData[VideoMetadataKeys.FIRST_AIR_DATE] = 
          "sample air date";
        // Etc.
    
        this._aaPlugin.setVideoMetadata(contextData);
        this._playerPlugin.trackVideoLoad();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L107)

...

    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        console.log('Player event: VIDEO_LOAD');
        var contextData = {};
    
        var mediaInfo = 
          MediaHeartbeat.createMediaObject(videoInfo.name, 
                                           videoInfo.id, 
                                           videoInfo.length,
                                           videoInfo.streamType);
    
        // Set standard Video Metadata
        var standardVideoMetadata = {};
        standardVideoMetadata[VideoMetadataKeys.SEASON] = 
          "sample season";
        standardVideoMetadata[VideoMetadataKeys.SHOW] = 
          "sample show";
        standardVideoMetadata[VideoMetadataKeys.EPISODE] = 
          "sample episode";
        standardVideoMetadata[VideoMetadataKeys.ASSET_ID] = 
          "sample asset id";
        standardVideoMetadata[VideoMetadataKeys.GENRE] = 
          "sample genre";
        standardVideoMetadata[VideoMetadataKeys.FIRST_AIR_DATE] = 
          "sample air date";
        // Etc.
    
        mediaInfo.setValue(MediaHeartbeat.MediaObjectKey.StandardVideoMetadata, 
                           standardVideoMetadata);
    
        this._mediaHeartbeat.trackSessionStart(mediaInfo, contextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L88)

...

Note: Insetad of setting the Standard Video Metadata through the
AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the Standard Video
Metadata is set through the MediaObject key
MediaObject.MediaObjectKey.StandardVideoMetadata().

_**Custom Video Metadata**_

**1.x:**

  * VideoMetadataKeys()
  * AdobeAnalyticsPlugin.setVideoMetadata()

...

**2.x:**

  * MediaHeartbeat.createMediaObject()
  * MediaHeartbeat.trackSessionStart()
    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        var contextData = {
            isUserLoggedIn: "false",
            tvStation: "Sample TV station",
            programmer: "Sample programmer"
        };
    
        this._aaPlugin.setVideoMetadata(contextData);
        this._playerPlugin.trackVideoLoad();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L107)

...

    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        var contextData = {
            isUserLoggedIn: "false",
            tvStation: "Sample TV station",
            programmer: "Sample programmer"
        };
    
        var videoInfo = this._player.getVideoInfo();
        var mediaInfo = 
          MediaHeartbeat.createMediaObject(videoInfo.name, 
                                           videoInfo.id, 
                                           videoInfo.length,
                                           videoInfo.streamType);
    
        mediaInfo.setValue(MediaHeartbeat.MediaObjectKey.StandardVideoMetadata, 
                           standardVideoMetadata);
    
        this._mediaHeartbeat.trackSessionStart(mediaInfo, contextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L88)

...

Note: Instead of setting the Custom Video Metadata through the
AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the Standard Video
Metadata is set through the MediaHeartbeat.trackSessionStart() API.

_**Playback**_

**1.x:**

  * VideoPlayerPlugin.trackPlay()

...

**2.x:**

  * MediaHeartbeat.trackPlay()
    
    VideoAnalyticsProvider.prototype._onSeekStart = 
      function() {
        console.log('Player event: SEEK_START');
        this._playerPlugin.trackSeekStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L149)

...

    
    VideoAnalyticsProvider.prototype._onSeekStart = 
      function() {
        console.log('Player event: SEEK_START');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekStart);
    };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L127)

...

_**Pause**_

**1.x:**

  * VideoPlayerPlugin.trackPause()

...

**2.x:**

  * MediaHeartbeat.trackPausel()
    
    VideoAnalyticsProvider.prototype._onPause = 
      function() { 
        console.log('Player event:X PAUSE'); 
        this._playerPlugin.trackPause(); 
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L144)

...

    
    VideoAnalyticsProvider.prototype._onBufferComplete = 
      function() { 
        console.log('Player event: BUFFER_COMPLETE'); 
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete); 
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L142)

...

_**Seek Complete**_

**1.x:**

  * VideoPlayerPlugin.trackSeekComplete()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete) 
    
    VideoAnalyticsProvider.prototype._onSeekComplete = 
      function() {
        console.log('Player event: SEEK_COMPLETE');
        this._playerPlugin.trackSeekComplete();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L154)

...

    
    VideoAnalyticsProvider.prototype._onSeekComplete = 
      function() {
        console.log('Player event: SEEK_COMPLETE');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete);
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L132)

...

_**Buffer Start **_

**1.x:**

  * VideoPlayerPlugin.trackBufferStart()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferStart) 
    
    VideoAnalyticsProvider.prototype._onBufferStart = 
      function() {
        console.log('Player event: BUFFER_START');
        this._playerPlugin.trackBufferStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L159)

...

    
    VideoAnalyticsProvider.prototype._onBufferStart = 
      function() {
        console.log('Player event: BUFFER_START');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferStart);
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L137)

...

_**Buffer Complete **_

**1.x:**

  * VideoPlayerPlugin.trackBufferComplete()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete) 
    
    VideoAnalyticsProvider.prototype._onBufferComplete = 
      function() {
        console.log('Player event: BUFFER_COMPLETE');
        this._playerPlugin.trackBufferComplete();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L164)

...

    
    VideoAnalyticsProvider.prototype._onBufferComplete = 
      function() {
        console.log('Player event: BUFFER_COMPLETE');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete);
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L142)

...

_**Playback Complete **_

**1.x:**

  * VideoPlayerPlugin.trackComplete()

...

**2.x:**

  * MediaHeartbeat.trackComplete()
    
    VideoAnalyticsProvider.prototype._onComplete = 
      function() {
        console.log('Player event: COMPLETE');
        this._playerPlugin.trackComplete(function() {
            console.log(
              "The completion of the content has been tracked.");
        });
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L203)

...

    
    VideoAnalyticsProvider.prototype._onComplete = 
      function() {
        console.log('Player event: COMPLETE');
        this._mediaHeartbeat.trackComplete();
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L197)

...

Table 3. VHL Code Comparison: AD PLAYBACK

VHL 1.x VHL 2.x

_**Ad Start**_

**1.x:**

  * VideoPlayerPlugin.trackAdStart()
  * VideoPlayerPluginDelegate.getAdBreakInfo()
  * VideoPlayerPluginDelegate.getAdInfo()

...

**2.x:**

  * MediaHeartbeat.createAdBreakObject()
  * MediaHeartbeat.createAdObject()
  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart) 
  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart) 
    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
        this._playerPlugin.trackAdStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L169)

...

    
    SampleVideoPlayerPluginDelegate.prototype.getAdInfo = 
      function() {
        return this._player.getAdInfo();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video
.player.plugin.delegate.js#L31)

...

    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
        var adContextData = {};
    
        // AdBreak Info - getting the adBreakInfo from player and creating 
        // AdBreakInfo Object from MediaHeartbeat
        var _adBreakInfo = this._player.getAdBreakInfo();
        var adBreakInfo = 
          MediaHeartbeat.createAdBreakObject(_adBreakInfo.name, 
                                             _adBreakInfo.position, 
                                             _adBreakInfo.startTime);
    
        // Ad Info - getting the adInfo from player and creating 
        // AdInfo Object from MediaHeartbeat
        var _adInfo = this._player.getAdInfo();
        var adInfo = MediaHeartbeat.createAdObject(_adInfo.name, 
                                                   _adInfo.id, 
                                                   _adInfo.position, 
                                                   _adInfo.length);
    
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, 
                                        adBreakInfo);
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, 
                                        adInfo, 
                                        adContextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L147)

...

_**Standard Ad Metadata**_

**1.x:**

  * AdMetadataKeys()
  * AdobeAnalyticsPlugin.setAdMetadata()

...

**2.x:**

  * MediaHeartbeat.createAdObject()
  * MediaHeartbeat.trackAdStart()
    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
    
        var contextData = {};
        // setting Standard Ad Metadata
        contextData[AdMetadataKeys.ADVERTISER] = 
          "sample advertiser";
        contextData[AdMetadataKeys.CAMPAIGN_ID] = 
          "sample campaign";
        contextData[AdMetadataKeys.CREATIVE_ID] = 
          "sample creative";
        contextData[AdMetadataKeys.CREATIVE_URL] = 
          "sample url";
        contextData[AdMetadataKeys.SITE_ID] = 
          "sample site";
        contextData[AdMetadataKeys.PLACEMENT_ID] = 
          "sample placement";
    
        this._aaPlugin.setAdMetadata(contextData);
        this._playerPlugin.trackAdStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L169)

...

    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
        var adContextData = { };
    
        // AdBreak Info - getting the adBreakInfo from player and creating 
        // AdBreakInfo Object from MediaHeartbeat
        var _adBreakInfo = this._player.getAdBreakInfo();
        var adBreakInfo = 
          MediaHeartbeat.createAdBreakObject(_adBreakInfo.name, 
                                             _adBreakInfo.position, 
                                             _adBreakInfo.startTime);
    
        // Ad Info - getting the adInfo from player and creating 
        // AdInfo Object from MediaHeartbeat
        var _adInfo = this._player.getAdInfo();
        var adInfo = 
          MediaHeartbeat.createAdObject(_adInfo.name, 
                                        _adInfo.id, 
                                        _adInfo.position, 
                                        _adInfo.length);
    
        // Set standard Ad Metadata
        var standardAdMetadata = {};
        standardAdMetadata[MediaHeartbeat.AdMetadataKeys.ADVERTISER] = 
          "Sample Advertiser";
        standardAdMetadata[MediaHeartbeat.AdMetadataKeys.CAMPAIGN_ID] = 
          "Sample Campaign";
    
        adInfo.setValue(MediaHeartbeat.MediaObjectKey.StandardAdMetadata, 
                        standardAdMetadata);
    
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, 
                                        adBreakInfo);
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, 
                                        adInfo, 
                                        adContextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L147)

...

Note: Instead of setting the Standard Ad Metadata through the
AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the Standard Ad
Metadata is set through the AdMetadata key
MediaObject.MediaObjectKey.StandardVideoMetadata

_**Custom Ad Metadata**_

**1.x:**

  * AdobeAnalyticsPlugin.setAdMetadata()

...

**2.x:**

  * MediaHeartbeat.createAdObject()
  * MediaHeartbeat.trackAdStart()
    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
    
        var contextData = {};
        // setting Standard Ad Metadata
        contextData[AdMetadataKeys.ADVERTISER] = 
          "sample advertiser";
        contextData[AdMetadataKeys.CAMPAIGN_ID] = 
          "sample campaign";
        contextData[AdMetadataKeys.CREATIVE_ID] = 
          "sample creative";
        contextData[AdMetadataKeys.CREATIVE_URL] = 
          "sample url";
        contextData[AdMetadataKeys.SITE_ID] = 
          "sample site";
        contextData[AdMetadataKeys.PLACEMENT_ID] = 
          "sample placement";
    
        this._aaPlugin.setAdMetadata(contextData);
        this._playerPlugin.trackAdStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L169)

...

    
    VideoAnalyticsProvider.prototype._onAdStart = 
      function() {
        console.log('Player event: AD_START');
        var adContextData = {
            affiliate: "Sample affiliate",
            campaign: "Sample ad campaign"
        };
    
        // AdBreak Info - getting the adBreakInfo from player and creating 
        // AdBreakInfo Object from MediaHeartbeat
        var _adBreakInfo = this._player.getAdBreakInfo();
        var adBreakInfo = 
          MediaHeartbeat.createAdBreakObject(_adBreakInfo.name, 
                                             _adBreakInfo.position, 
                                             _adBreakInfo.startTime);
    
        // Ad Info - getting the adInfo from player and creating 
        // AdInfo Object from MediaHeartbeat
        var _adInfo = this._player.getAdInfo();
        var adInfo = 
          MediaHeartbeat.createAdObject(_adInfo.name, 
                                        _adInfo.id, 
                                        _adInfo.position, 
                                        _adInfo.length);
    
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, 
                                        adBreakInfo);
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, 
                                        adInfo, 
                                        adContextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L147)

...

Note: Instead of setting the Custom Ad Metadata through the
AdobeAnalyticsPlugin.setVideoMetadata API, in VHL 2.0, the Standard Ad
Metadata is set through the MediaHeartbeat.trackAdStart() API.

_**Ad Skip**_

**1.x:**

  * AdobeAnalyticsPlugin.setAdMetadata()

...

**2.x:**

  * MediaHeartbeat.createAdObject()
  * MediaHeartbeat.trackAdStart()
    
    SampleVideoPlayerPluginDelegate.prototype.getAdInfo = 
      function() {
        return this._player.getAdInfo();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video
.player.plugin.delegate.js#L31)

...

    
    VideoAnalyticsProvider.prototype._onAdSkip = 
      function() {
        console.log('Player event: AD_SKIP');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdSkip);
      };

Note: In VHL 1.5.X APIs; getAdinfo() and getAdBreakInfo() must return null if
the player is outside the Ad break boundaries.

_**Ad Complete**_

**1.x:**

  * VideoPlayerPlugin.trackAdComplete()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete)
  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete)
    
    VideoAnalyticsProvider.prototype._onAdComplete = 
      function() {
        console.log('Player event: AD_COMPLETE');
        this._playerPlugin.trackAdComplete();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L185)

...

    
    VideoAnalyticsProvider.prototype._onAdComplete = 
      function() {
        console.log('Player event: AD_COMPLETE');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete);
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L173)

...

Table 4. VHL Code Comparison: CHAPTER PLAYBACK

VHL 1.x VHL 2.x

_**Chapter Start**_

**1.x:**

  * VideoPlayerPluginDelegate.getChapterInfo()
  * VideoPlayerPlugin.trackChapterStart()

...

**2.x:**

  * MediaHeartbeat.createChapterObject 
  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart) 
    
    VideoAnalyticsProvider.prototype._onChapterStart = 
      function() {
        console.log('Player event: CHAPTER_START');
        this._playerPlugin.trackChapterStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L190%20)

...

    
    SampleVideoPlayerPluginDelegate.prototype.getChapterInfo = 
      function() {
        return this._player.getChapterInfo();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video
.player.plugin.delegate.js#L35)

...

    
    VideoAnalyticsProvider.prototype._onChapterStart = 
      function() {
        console.log('Player event: CHAPTER_START');
        var chapterContextData = { };
    
        // Chapter Info - getting the chapterInfo from player and creating 
        // ChapterInfo Object from MediaHeartbeat
        var _chapterInfo = this._player.getChapterInfo();
        var chapterInfo = 
          MediaHeartbeat.createChapterObject(_chapterInfo.name, 
                                             _chapterInfo.position, 
                                             _chapterInfo.length, 
                                             _chapterInfo.startTime);
    
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart, 
                                        chapterInfo, 
                                        chapterContextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L179)

...

_**Chapter Skip**_

**1.x:**

  * VideoPlayerPluginDelegate.getChapterInfo()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip)
    
    SampleVideoPlayerPluginDelegate.prototype.getChapterInfo = 
      function() {
        return this._player.getChapterInfo();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video
.player.plugin.delegate.js#L35)

...

    
    VideoAnalyticsProvider.prototype._onChapterSkip = 
      function() {
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);
      };

Note: In VHL 1.5.X APIs; getChapterinfo() must return null if the player is
outside the Chapter boundaries.

_**Chapter Custom Metadata**_

**1.x:**

  * VideoPlayerPlugin.trackChapterStart()
  * AdobeAnalyticsPlugin.setChapterMetadata()

...

**2.x:**

  * MediaHeartbeat.createChapterObject()
  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart)
    
    VideoAnalyticsProvider.prototype._onChapterStart = 
      function() {
        console.log('Player event: CHAPTER_START');
        this._aaPlugin.setChapterMetadata({
            segmentType: "Sample segment type"
        });
        this._playerPlugin.trackChapterStart();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L190)

...

    
    VideoAnalyticsProvider.prototype._onChapterStart = 
      function() {
        console.log('Player event: CHAPTER_START');
        var chapterContextData = {
            segmentType: "Sample segment type"
        };
    
        // Chapter Info - getting the chapterInfo from player and creating 
        // ChapterInfo Object from MediaHeartbeat
        var _chapterInfo = this._player.getChapterInfo();
        var chapterInfo = 
          MediaHeartbeat.createChapterObject(_chapterInfo.name, 
                                             _chapterInfo.position, 
                                             _chapterInfo.length, 
                                             _chapterInfo.startTime);
    
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart, 
                                        chapterInfo, 
                                        chapterContextData);
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L179)

...

Note:

_**Chapter Complete**_

**1.x:**

  * trackChapterComplete()

...

**2.x:**

  * trackEvent(MediaHeartbeat.Event.ChapterComplete)
    
    VideoAnalyticsProvider.prototype._onChapterComplete = 
      function() {
        console.log('Player event: CHAPTER_COMPLETE');
        this._playerPlugin.trackChapterComplete();
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L198)

...

    
    VideoAnalyticsProvider.prototype._onChapterComplete = 
      function() {
        console.log('Player event: CHAPTER_COMPLETE');
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);
      };

[Sample Player 2.x](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L192)

...

Table 5. VHL Code Comparison: OTHER EVENTS

VHL 1.x VHL 2.x

_**Bitrate Change**_

**1.x:**

  * VideoPlayerPlugin.trackBitrateChange()

...

**2.x:**

  * MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange) 
    
    VideoAnalyticsProvider.prototype._onBitrateChange = 
      function() {
        console.log('Player event: BITRATE_CHANGE');
        // Update getQosInfo to return the updated bitrate
        this._playerPlugin.trackBitrateChange();
      };
    
    VideoAnalyticsProvider.prototype._onBitrateChange = 
      function() {
        console.log('Player event: BITRATE_CHANGE');
        // Update getQosObject to return the updated bitrate
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analyt
ics.provider.js#L198)

...

_**Video Resume**_

**1.x:**

  * VideoInfo.resumed()
  * VideoPlayerPluginDelegate.getVideoInfo()
  * VideoPlayerPlugin.trackVideoLoad()

...

**2.x:**

  * MediaObject()
  * MediaHeartbeat.trackSessionStart()
    
    this._videoInfo.resumed = true;

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/player/video.player.js
#L207)

...

    
    VideoPlayer.prototype.getVideoInfo = 
      function() {
        this._videoInfo.playhead = vTime;
        return this._videoInfo;
      };

[Sample 1.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat/b
lob/master/sdks/js/samples/BasicPlayerSample/script/app/player/video.player.js
#L96)

...

    
    VideoAnalyticsProvider.prototype._onLoad = 
      function() {
        console.log('Player event: VIDEO_LOAD');
        var contextData = {};
    
        var videoInfo = this._player.getVideoInfo();
        var mediaInfo = 
          MediaHeartbeat.createMediaObject(videoInfo.playerName, 
                                           videoInfo.id, 
                                           videoInfo.length,
                                           videoInfo.streamType);
        mediaInfo.setValue(MediaHeartbeat.MediaObjectKey.VideoResumed, 
                           true);
    
        this._mediaHeartbeat.trackSessionStart(mediaInfo, 
                                               contextData);
      };

[Sample 2.x Player](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v
2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.ana
lytics.provider.js#L100)

...

For more information on tracking video with 2.x, see [Track Core Video Playbac
k](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo
/c_vhl_track-core-vid-playback.html) in _Measuring Video in Adobe Analytics_.

## VHL 1.x to 2.x API Conversion

**VHL 2.x API References:**

  * [Android API Reference](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/android/index.html)
  * [iOS API Reference](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/ios/index.html)
  * [JS API Reference](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/index.html)

Table 1. Required Track APIs:

VHL 1.x VHL 2.x

videoPlayerPlugin.trackVideoLoad()

N/A

videoPlayerPlugin.trackSessionStart()

[mediaHeartbeat.trackSessionStart(mediaObject, mediaCustomMetadata)](https
://adobe-marketing-cloud.github.io/video-
heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackSessionStart)

videoPlayerPlugin.trackPlay()

[mediaHeartbeat.trackPlay()](https://adobe-marketing-cloud.github.io/video-
heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackPlay)

videoPlayerPlugin.trackPause()

[mediaHeartbeat.trackPause()](https://adobe-marketing-cloud.github.io/video-
heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackPause)

videoPlayerPlugin.trackComplete()

[mediaHeartbeat.trackComplete()](https://adobe-marketing-cloud.github.io
/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackComplete)

videoPlayerPlugin.trackVideoUnload()

[mediaHeartbeat.trackSessionEnd()](https://adobe-marketing-cloud.github.io
/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackSessionEnd)

videoPlayerPlugin.trackApplicationError()

N/A

videoPlayerPlugin.trackVideoPlayerError()

[mediaHeartbeat.trackError()](https://adobe-marketing-cloud.github.io/video-
heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackError)

All of the optional tracking APIs such as (Ads, Chapters, Bitrate change,
Seeking, and Buffering) are now part of a single trackEvent API. The
[trackEvent](https://adobe-marketing-cloud.github.io/video-
heartbeat-v2/reference/javascript/MediaHeartbeat.html#trackEvent) API receives
a constant parameter that represents the type of event that it is intended to
track:

Table 2. Optional trackEvent APIs:

VHL 1.x VHL 2.x

Return a valid AdBreakInfo in VideoPlayerPlugin.getAdBreakInfo()

trackEvent(Event.AdBreakStart)

Return null in VideoPlayerPlugin.getAdBreakInfo()

trackEvent(Event.AdBreakComplete)

playerPlugin.trackAdStart()

trackEvent(Event.AdStart, adObject, adCustomMetadata)

playerPlugin.trackAdComplete()

trackEvent(Event.AdComplete)

Return null in VideoPlayerPlugin.getAdInfo()

trackEvent(Event.AdSkip)

playerPlugin.trackChapterStart()

trackEvent(Event.ChapterStart, chapterObject, chapterCustomMetadata)

playerPlugin.trackChapterComplete()

trackEvent(Event.ChapterComplete)

Return null in VideoPlayerPlugin.getChapterInfo()

trackEvent(Event.ChapterSkip)

playerPlugin.trackSeekStart()

trackEvent(Event.SeekStart)

playerPlugin.trackSeekComplete()

trackEvent(Event.SeekComplete)

playerPlugin.trackBufferStart()

trackEvent(Event.BufferStart)

playerPlugin.trackBufferComplete()

trackEvent(Event.BufferComplete)

playerPlugin.trackBitrateChange()

trackEvent(Event.BitrateChange)

playerPlugin.trackTimedMetadata()

trackEvent(Event.TimedMetadataUpdate)

