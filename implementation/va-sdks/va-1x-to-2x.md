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

## stripped of classes, ids, divs, etc.
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L58" target="_blank">1.x Sample Player</a>
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L47" target="_blank">2.x Sample Player</a>
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.video.player.plugin.delegate.js#L17" target="_blank">Sample 1.x Player</a>
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.adobe.analytics.plugin.delegate.js#L17" target="_blank">Sample 1.x Player</a>
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/sample.heartbeat.delegate.js#L17" target="_blank">Sample 1.x Player</a>
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
<a  href="https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/blob/master/sdks/js/samples/BasicPlayerSample/script/app/analytics/video.analytics.provider.js#L57" target="_blank">Sample 2.x Player</a>
        <p>...</p>
      </td>
    </tr>
  </tbody>
</table>
