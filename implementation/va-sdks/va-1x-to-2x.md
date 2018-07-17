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

<table cellpadding="4" cellspacing="0" summary="" frame="border" border="1" rules="all"><caption><span>Table 1. VHL Code Comparison: INITIALIZATION</span></caption>
  <thead  align="left">
    <tr>
      <th  align="center" valign="top">VHL 1.x API </th>
      <th  align="center" valign="top">VHL 2.x API</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td  align="left" valign="top" >
        <p><em><strong>Object Initialization</strong></em></p>
        <p><strong>1.x:</strong></p>
          <ul>
            <li><code>Heartbeat()</code></li>
            <li><code>VideoPlayerPlugin() </code></li>
            <li><code>AdobeAnalyticsPlugin() </code></li>
            <li><code>HeartbeatPlugin()</code></li>
          </ul>
      </td>
      <td  align="left" valign="top" >
        <p>... </p>
        <p><strong>2.x:</strong></p>
          <ul>
            <li><code>MediaHeartbeat()</code></li>
            <li><code>MediaHeartbeatConfig()</code></li>
          </ul>
      </td>
    </tr>
    <tr>
      <td  align="left" valign="top" >
        <strong>Set up the video player plugin:
            </strong>
            <pre>this._playerPlugin = 
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
this._heartbeat.configure(configData);</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L58" >1.x Sample Player</a>
        <p>...</p>
      </td>
      <td  align="left" valign="top" >
        <strong>Media Heartbeat initialization:
            </strong><pre>
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
 appMeasurement);</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L47" >2.x Sample Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td  align="left" valign="top" >
        <p><em><strong>Delegates</strong></em></p>
        <p><strong>1.x:</strong></p>
          <ul>
            <li><code>VideoPlayerPluginDelegate()</code></li>
            <li><code>VideoPlayerPluginDelegate().getVideoInfo</code></li>
            <li><code>VideoPlayerPluginDelegate().getAdBreakInfo</code></li>
            <li><code>VideoPlayerPluginDelegate().getAdInfo</code></li>
            <li><code>VideoPlayerPluginDelegate().getChapterInfo</code></li>
            <li><code>VideoPlayerPluginDelegate().getQoSInfo</code></li>
            <li><code>VideoPlayerPluginDelegate().get.onError</code></li>
            <li><code>AdobeAnalyticsPluginDelegate()</code></li>
            <li><code>AdobeHeartbeatPluginDelegate()</code></li>
          </ul>
      </td>
      <td  align="left" valign="top" >
        <p>... </p>
        <p><strong>2.x:</strong></p>
          <ul>
            <li><code>MediaHeartbeatDelegate()</code></li>
            <li><code>MediaHeartbeatDelegate().getCurrentPlaybackTime</code></li>
            <li><code>MediaHeartbeatDelegate().getQoSObject</code></li>
          </ul>
      </td>
    </tr>
    <tr>
      <td  align="left" valign="top" >
        <strong>VideoPlayerPluginDelegate:
            </strong><pre>
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
  };</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L17" >Sample 1.x Player</a>
        <p>...</p>
        <strong>AdobeAnalyticsPluginDelegate:
            </strong><pre>
$.extend(SampleAdobeAnalyticsPluginDelegate.prototype, 
 AdobeAnalyticsPluginDelegate.prototype);
function SampleAdobeAnalyticsPluginDelegate() {}
SampleAdobeAnalyticsPluginDelegate.prototype.onError = 
  function(errorInfo) {
  console.log("AdobeAnalyticsPlugin error: " + 
           errorInfo.getMessage() + 
           " | " + 
           errorInfo.getDetails());
  };</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.adobe.analytics.plugin.delegate.js#L17" >Sample 1.x Player</a>
        <p>...</p>
        <strong>HeartbeatDelegate:
            </strong><pre>
$.extend(SampleHeartbeatDelegate.prototype, 
 HeartbeatDelegate.prototype);
function SampleHeartbeatDelegate() {}
SampleHeartbeatDelegate.prototype.onError = 
  function(errorInfo) {
  console.log("Heartbeat error: " + 
          errorInfo.getMessage() + 
          " | " + 
          errorInfo.getDetails());
};</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.heartbeat.delegate.js#L17" >Sample 1.x Player</a>
      </td>
      <td  align="left" valign="top" >
        <strong>MediaHeartbeatDelegate:
            </strong><pre>
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
appMeasurement);</pre>
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L57" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
</hr>
<table cellpadding="4" cellspacing="0" frame="border" border="1" rules="all"><caption><span >Table 2. VHL Code Comparison: CORE PLAYBACK</span></caption>
  <thead align="left">
    <tr>
      <th align="center" valign="top">VHL 1.x</th>
      <th align="center" valign="top">VHL 2.x</th>
    </tr>
  </thead>
  <tbody >
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Session Start</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPluginDelegate.trackVideoLoad()</li>
          <li >VideoPlayerPluginDelegate.getVideoInfo()
          </li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createMediaObject()</li>
          <li >MediaHeartbeat.trackSessionStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
};</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L107" >1.x Sample Player - trackVideoLoad()</a>
                <p><a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L23" >1.x Sample Player - getVideoInfo()</a></p>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
};</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L88" >2.x Sample Player -
                  createMediaObject()</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Standard Video Metadata</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoMetadataKeys()</li>
          <li >AdobeAnalyticsPlugin.setVideoMetadata90</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createMediaObject()</li>
          <li >MediaHeartbeat.trackSessionStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L107" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L88" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note:Insetad of setting the Standard Video Metadata through the
            AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the
          Standard Video Metadata is set through the MediaObject key
            MediaObject.MediaObjectKey.StandardVideoMetadata().
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Custom Video Metadata</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoMetadataKeys()</li>
          <li >AdobeAnalyticsPlugin.setVideoMetadata()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createMediaObject()</li>
          <li >MediaHeartbeat.trackSessionStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onLoad = 
  function() {
    var contextData = {
        isUserLoggedIn: "false",
        tvStation: "Sample TV station",
        programmer: "Sample programmer"
    };
    this._aaPlugin.setVideoMetadata(contextData);
    this._playerPlugin.trackVideoLoad();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L107" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L88" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: Instead of setting the Custom Video Metadata through the
            AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the
          Standard Video Metadata is set through the
            MediaHeartbeat.trackSessionStart() API.
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Playback</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPlugin.trackPlay()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>...  </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li > MediaHeartbeat.trackPlay()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onSeekStart = 
  function() {
    console.log('Player event: SEEK_START');
    this._playerPlugin.trackSeekStart();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L149" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onSeekStart = 
  function() {
    console.log('Player event: SEEK_START');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekStart);
};</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L127" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Pause</strong></em></p>
        <strong >1.x:</strong><ul>
            <li >VideoPlayerPlugin.trackPause()</li>
          </ul>
      </td>
      <td align="left" valign="top" >
        <p>...</p>
        <strong >2.x:</strong><ul>
            <li >MediaHeartbeat.trackPausel()</li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onPause = 
  function() { 
    console.log('Player event:X PAUSE'); 
    this._playerPlugin.trackPause(); 
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L144" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onBufferComplete = 
  function() { 
    console.log('Player event: BUFFER_COMPLETE'); 
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete); 
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L142" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Seek Complete</strong></em></p>
        <strong >1.x:</strong><ul>
            <li >VideoPlayerPlugin.trackSeekComplete()</li>
          </ul>
      </td>
      <td align="left" valign="top" >
        <p>...</p>
        <strong >2.x:</strong><ul>
            <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete)
              </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onSeekComplete = 
  function() {
    console.log('Player event: SEEK_COMPLETE');
    this._playerPlugin.trackSeekComplete();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L154" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onSeekComplete = 
  function() {
    console.log('Player event: SEEK_COMPLETE');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L132" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Buffer Start </strong></em></p>
        <strong >1.x:</strong><ul>
            <li >VideoPlayerPlugin.trackBufferStart()</li>
          </ul>
      </td>
      <td align="left" valign="top" >
        <p>...</p>
        <strong >2.x:</strong><ul>
            <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferStart)
              </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onBufferStart = 
  function() {
    console.log('Player event: BUFFER_START');
    this._playerPlugin.trackBufferStart();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L159" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onBufferStart = 
  function() {
    console.log('Player event: BUFFER_START');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferStart);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L137" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Buffer Complete </strong></em></p>
        <strong >1.x:</strong><ul>
            <li >VideoPlayerPlugin.trackBufferComplete()</li>
          </ul>
      </td>
      <td align="left" valign="top" >
        <p>...</p>
        <strong >2.x:</strong><ul>
            <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete)
              </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onBufferComplete = 
  function() {
    console.log('Player event: BUFFER_COMPLETE');
    this._playerPlugin.trackBufferComplete();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L164" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onBufferComplete = 
  function() {
    console.log('Player event: BUFFER_COMPLETE');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L142" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Playback Complete </strong></em></p>
        <strong >1.x:</strong><ul>
            <li >VideoPlayerPlugin.trackComplete()</li>
          </ul>
      </td>
      <td align="left" valign="top" >
        <p>...</p>
        <strong >2.x:</strong><ul>
            <li >MediaHeartbeat.trackComplete()</li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onComplete = 
  function() {
    console.log('Player event: COMPLETE');
    this._playerPlugin.trackComplete(function() {
        console.log(
          "The completion of the content has been tracked.");
    });
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L203" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onComplete = 
  function() {
    console.log('Player event: COMPLETE');
    this._mediaHeartbeat.trackComplete();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L197" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
</hr>
<table cellpadding="4" cellspacing="0" frame="border" border="1" rules="all"><caption><span >Table 3. VHL Code Comparison: AD PLAYBACK</span></caption>
  <thead align="left">
    <tr>
      <th align="center" valign="top">VHL 1.x</th>
      <th align="center" valign="top">VHL 2.x</th>
    </tr>
  </thead>
  <tbody >
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Ad Start</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPlugin.trackAdStart()</li>
          <li >VideoPlayerPluginDelegate.getAdBreakInfo()</li>
          <li >VideoPlayerPluginDelegate.getAdInfo()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createAdBreakObject()</li>
          <li >MediaHeartbeat.createAdObject()</li>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart)
            </li>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart) </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
  function() {
    console.log('Player event: AD_START');
    this._playerPlugin.trackAdStart();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L169" >Sample 1.x Player</a>
        <p>...</p>
        <pre>SampleVideoPlayerPluginDelegate.prototype.getAdInfo = 
  function() {
    return this._player.getAdInfo();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L31" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L147" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Standard Ad Metadata</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >AdMetadataKeys()</li>
          <li >AdobeAnalyticsPlugin.setAdMetadata()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createAdObject()</li>
          <li >MediaHeartbeat.trackAdStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L169" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L147" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: Instead of setting the Standard Ad Metadata through the
            AdobeAnalyticsPlugin.setVideoMetadata() API, in VHL 2.0, the
          Standard Ad Metadata is set through the AdMetadata key
            MediaObject.MediaObjectKey.StandardVideoMetadata
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Custom Ad Metadata</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >AdobeAnalyticsPlugin.setAdMetadata()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createAdObject()</li>
          <li >MediaHeartbeat.trackAdStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L169" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L147" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: Instead of setting the Custom Ad Metadata through the
            AdobeAnalyticsPlugin.setVideoMetadata API, in VHL 2.0, the
          Standard Ad Metadata is set through the
            MediaHeartbeat.trackAdStart() API.
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Ad Skip</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >AdobeAnalyticsPlugin.setAdMetadata()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createAdObject()</li>
          <li >MediaHeartbeat.trackAdStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>SampleVideoPlayerPluginDelegate.prototype.getAdInfo = 
  function() {
    return this._player.getAdInfo();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L31" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        
          <pre>VideoAnalyticsProvider.prototype._onAdSkip = 
  function() {
    console.log('Player event: AD_SKIP');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdSkip);
  };</pre>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: In VHL 1.5.X APIs; getAdinfo() and
            getAdBreakInfo() must return null if the player is outside the
          Ad break boundaries.
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Ad Complete</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPlugin.trackAdComplete()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete)</li>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdComplete = 
  function() {
    console.log('Player event: AD_COMPLETE');
    this._playerPlugin.trackAdComplete();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L185" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onAdComplete = 
  function() {
    console.log('Player event: AD_COMPLETE');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete);
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L173" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
</hr>
<table cellpadding="4" cellspacing="0" frame="border" border="1" rules="all"><caption><span >Table 4. VHL Code Comparison: CHAPTER PLAYBACK</span></caption>
  <thead align="left">
    <tr>
      <th align="center" valign="top">VHL 1.x</th>
      <th align="center" valign="top">VHL 2.x</th>
    </tr>
  </thead>
  <tbody >
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Chapter Start</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPluginDelegate.getChapterInfo()</li>
          <li >VideoPlayerPlugin.trackChapterStart()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createChapterObject </li>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart)
            </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onChapterStart = 
  function() {
    console.log('Player event: CHAPTER_START');
    this._playerPlugin.trackChapterStart();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L190%20" >Sample 1.x Player</a>
                <p>...</p>
                <pre>SampleVideoPlayerPluginDelegate.prototype.getChapterInfo = 
  function() {
    return this._player.getChapterInfo();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L35" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onChapterStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L179" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Chapter Skip</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPluginDelegate.getChapterInfo()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>SampleVideoPlayerPluginDelegate.prototype.getChapterInfo = 
  function() {
    return this._player.getChapterInfo();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L35" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        
          <pre>VideoAnalyticsProvider.prototype._onChapterSkip = 
  function() {
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);
  };</pre>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: In VHL 1.5.X APIs; getChapterinfo() must return null if the
          player is outside the Chapter boundaries.
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Chapter Custom Metadata</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPlugin.trackChapterStart()</li>
          <li >AdobeAnalyticsPlugin.setChapterMetadata()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.createChapterObject()</li>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onChapterStart = 
  function() {
    console.log('Player event: CHAPTER_START');
    this._aaPlugin.setChapterMetadata({
        segmentType: "Sample segment type"
    });
    this._playerPlugin.trackChapterStart();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L190" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onChapterStart = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L179" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td colspan="2" align="left" valign="top" >
        Note: 
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Chapter Complete</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >trackChapterComplete()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >trackEvent(MediaHeartbeat.Event.ChapterComplete)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onChapterComplete = 
  function() {
    console.log('Player event: CHAPTER_COMPLETE');
    this._playerPlugin.trackChapterComplete();
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L198" >Sample 1.x Player</a>
                <p>...</p>
              </td>
              <td align="left" valign="top" >
                <pre>VideoAnalyticsProvider.prototype._onChapterComplete = 
  function() {
    console.log('Player event: CHAPTER_COMPLETE');
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L192" >Sample Player 2.x</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
<hr/>
<table cellpadding="4" cellspacing="0" frame="border" border="1" rules="all"><caption><span >Table 5. VHL Code Comparison: OTHER EVENTS</span></caption>
  <thead align="left">
    <tr>
      <th align="center" valign="top">VHL 1.x</th>
      <th align="center" valign="top">VHL 2.x</th>
    </tr>
  </thead>
  <tbody >
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Bitrate Change</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoPlayerPlugin.trackBitrateChange()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange)
            </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
          <pre>VideoAnalyticsProvider.prototype._onBitrateChange = 
  function() {
    console.log('Player event: BITRATE_CHANGE');
    // Update getQosInfo to return the updated bitrate
    this._playerPlugin.trackBitrateChange();
  };</pre>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onBitrateChange = 
  function() {
    console.log('Player event: BITRATE_CHANGE');
    // Update getQosObject to return the updated bitrate
    this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange);
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L198" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <p><em ><strong >Video Resume</strong></em></p>
        <p><strong >1.x:</strong></p>
        <ul>
          <li >VideoInfo.resumed()</li>
          <li >VideoPlayerPluginDelegate.getVideoInfo()</li>
          <li >VideoPlayerPlugin.trackVideoLoad()</li>
        </ul>
      </td>
      <td align="left" valign="top" >
        <p>... </p>
        <p><strong >2.x:</strong></p>
        <ul>
          <li >MediaObject()</li>
          <li >MediaHeartbeat.trackSessionStart()</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="left" valign="top" >
        <pre>this._videoInfo.resumed = true;</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/player/video.player.js#L207" >Sample 1.x Player</a>
        <p>...</p>
        <pre>VideoPlayer.prototype.getVideoInfo = 
  function() {
    this._videoInfo.playhead = vTime;
    return this._videoInfo;
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/player/video.player.js#L96" >Sample 1.x Player</a>
        <p>...</p>
      </td>
      <td align="left" valign="top" >
        <pre>VideoAnalyticsProvider.prototype._onLoad = 
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
  };</pre>
<a href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L100" >Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
