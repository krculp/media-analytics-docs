## Stream Type
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:**  </li> <li> **API Key:** <samp>**media.streamType**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5 </li> <li> **Sample value:** <samp>"video"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.streamType</samp> </li> <li> **Heartbeats:** <samp>s:meta:a.media.streamType</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** <samp>a.media.streamType</samp> </li> <li> **Data Feed:** <samp>videostreamtype</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.streamType</samp> </li> </ul> |


**Release Date: 09/13/18** 

Note: Available only through the <a href="media-collection-api.html">Media Collection API (RESTful) </a>.  Identifies the stream type. Valid values are "audio", "video", and "".  ** <a href="segments.html">Segments </a>:** <ul> <li>StreamType "All" - Segment all media stream data.  **Rule:** Content (ID) exists </li> <li>StreamType "Audio" - Segment all audio stream data.  **Rule:** Content (ID) exists AND Stream Type = audio </li> <li>StreamType "Video" - Segment all video stream data.  **Rule:** Content (ID) exists AND Stream Type = video </li> </ul> 

## Content ID
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**mediaId\***</samp> </li> <li> **API Key:** <samp>**media.id**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"4586695ABC"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.name</samp> </li> <li> **Heartbeats:** <samp>s:asset:video_id</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** <samp>a.media.name</samp> </li> <li> **Data Feed:** <samp>video</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.name</samp> </li> </ul> |


Content ID of the content, which can be used to tie back to other industry / CMS IDs, equal to the last value of <samp>s:asset:video_id</samp>. Any integer and/or letter combination.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, ** <em>mediaId </em>**, length, streamType)</samp> 

## Content Length (variable)
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**length\***</samp> </li> <li> **API Key:** <samp>**media.length**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any+ </li> <li> **Sample value:** <ul> <li>VOD: 128 </li> <li>Live: 86400 </li> <li>Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.length</samp> </li> <li> **Heartbeats:** <samp>l:asset:length</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Length (variable) </li> <li> **Context Data:** <samp>a.media.length</samp> </li> <li> **Data Feed:** <samp>videolength</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.length</samp> </li> </ul> |


**Release Date: 09/13/18** Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of <samp>l:asset:length</samp> from events of type Main. If <samp>l:asset:length</samp> is not set, then the last value of <samp>l:asset:duration</samp> is used.  In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  Important: This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.  For Live media with an unknown duration, the value of 86400 is the default.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, ** <em>length </em>**, streamType)</samp> **+** Pre Version 1.5.1, this was <samp>l:asset:duration</samp>; after 1.5.1, this is <samp>l:asset:length</samp>.  

## Video Length
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**length\***</samp> </li> <li> **API Key:** <samp>**media.length**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any+ </li> <li> **Sample value:** <ul> <li>VOD: 128 </li> <li>Live: 86400 </li> <li>Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.length</samp> </li> <li> **Heartbeats:** <samp>l:asset:length</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Length </li> <li> **Context Data:** <samp>a.media.length</samp> </li> <li> **Data Feed:** <samp>videoclassificationlength</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.length</samp> </li> </ul> |


**Release Date: 09/27/18** Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of <samp>l:asset:length</samp> from events of type Main. If <samp>l:asset:length</samp> is not set, then the last value of <samp>l:asset:duration</samp> is used.  In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  Important: This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.  For Live media with an unknown duration, the value of 86400 is the default.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, ** <em>length </em>**, streamType)</samp> **+** Pre Version 1.5.1, this was <samp>l:asset:duration</samp>; after 1.5.1, this is <samp>l:asset:length</samp>.  

## Content Type
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**streamType\***</samp> </li> <li> **API Key:** <samp>**media.contentType**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** restricted string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"vod"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.contentType</samp> </li> <li> **Heartbeats:** <samp>s:stream:type</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Type </li> <li> **Context Data:** <samp>a.contentType</samp> </li> <li> **Data Feed:** <samp>videocontenttype</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.contentType</samp> </li> </ul> |


Available values per **Stream Type**: <ul> <li> **Audio:** "song", "podcast", "audiobook", "radio" </li> <li> **Video:** "VoD", "Live", "Linear", "UGC", "DVoD" </li> </ul> Customers can provide custom values for this parameter.  This equals <samp>s:stream:type</samp>. If that is unset, this equals <samp>missing_content_type</samp>.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, length, ** <em>streamType </em>**)</samp> 

## Video Session ID
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** Obtained from backend </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.8 </li> <li> **Sample value:** <samp>1482236761294786918253</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.vsid</samp> </li> <li> **Heartbeat:** <samp>s:event:sid</samp> </li> </ul> | <ul> <li> **Available:** Use processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** <samp>a.media.vsid</samp> </li> <li> **Data Feed:** <samp>vsid</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.vsid</samp> </li> </ul> |


This identifies an instance of a content stream unique to an individual playback.  

## Content Player Name
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**playerName\***</samp> </li> <li> **API Key:** <samp>**media.playerName**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"Brightcove"</samp>, <samp>"Primetime"</samp>, etc.  </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.playerName</samp> </li> <li> **Heartbeats:** <samp>s:sp:player_name</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Player Name </li> <li> **Context Data:** <samp>a.media.playerName</samp> </li> <li> **Data Feed:** <samp>videoplayername</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.playerName</samp> </li> </ul> |


Name of the player.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>.  ** <em>playerName </em>**</samp> 

## Content Channel
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**channel\***</samp> </li> <li> **API Key:** <samp>**media.channel**</samp> </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"Sports"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.channel</samp> </li> <li> **Heartbeats:** <samp>s:sp:channel</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Channel </li> <li> **Context Data:** <samp>a.media.channel</samp> </li> <li> **Data Feed:** <samp>videochannel</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.channel</samp> </li> </ul> |


Distribution Station/Channels or where the content is played.  Any string value is accepted here.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>.  ** <em>channel </em>**</samp> 

## Content Segment
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"[0-10]"</samp> (minutes) </li> </ul> | <ul> <li> **Adobe Analytics:** N/A </li> <li> **Heartbeats:** N/A </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Segment </li> <li> **Context Data:** <samp>a.media.segment</samp> </li> <li> **Data Feed:** <samp>videosegment</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.segment</samp> </li> </ul> |


The interval that describes the part of the content that has been viewed (in minutes). The segment is computed as min and max of the playhead values during a playback session.  

## Content Name (variable)
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**name\***</samp> </li> <li> **API Key:** <samp>**media.name**</samp> </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** <samp>"The Big Bang Theory"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.friendlyName</samp> </li> <li> **Heartbeats:** <samp>s:asset:name</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Name (variable) </li> <li> **Context Data:** <samp>a.media.friendlyName</samp> </li> <li> **Data Feed:** <samp>videoname</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.friendlyName</samp> </li> </ul> |


**Release Date: 09/13/18** In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  This is the "friendly" (human-readable) name of the content, equal to the last value of <samp>s:asset:name</samp>.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>( ** <em>name </em>**, mediaId, length, streamType)</samp> 

## Video Name
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**name\***</samp> </li> <li> **API Key:** <samp>**media.name**</samp> </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** <samp>"The Big Bang Theory"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.friendlyName</samp> </li> <li> **Heartbeats:** <samp>s:asset:name</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Name </li> <li> **Context Data:** <samp>a.media.friendlyName</samp> </li> <li> **Data Feed:** <samp>videoclassificationname</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.friendlyName</samp> </li> </ul> |


**Release Date: 09/27/18** This is the "friendly" (human-readable) name of the content, equal to the last value of <samp>s:asset:name</samp>.  In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>( ** <em>name </em>**, mediaId, length, streamType)</samp> 

## Video Path
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** <samp>"4586695ABC"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.name</samp> </li> <li> **Heartbeats:** <samp>s:asset:video_id</samp> </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** prop </li> <li> **Report Name:** Video Path </li> <li> **Context Data:** <samp>a.media.name</samp> </li> <li> **Data Feed:** <samp>videopath</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.name</samp> </li> </ul> |


Ability to track path of viewer across site and/or App to see path they took to view a particular video. Any integer and/or letter combination.  

## SDK Version
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** <samp>**appVersion\***</samp> </li> <li> **API Key:** <samp>**media.sdkVersion**</samp> </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** <samp>"2.62.0_release"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.sdkVersion</samp> </li> <li> **Heartbeats:** <samp>s:sp:sdk</samp> </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** <em> </li> <li> **Context Data:** <samp>a.media.sdkVersion</samp> </li> <li> **Data Feed:** <samp>N/A</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.sdkVersion</samp> </li> </ul> |


The SDK version used by the player. This could have any custom value that makes sense for your player. Customers will have to create their own processing rules to have the value available for reporting.  **\*** <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>.  ** <em>appVersion </em>**</samp> 

## VHL Version
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set\* </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** <samp>"js-2.0.1.88-c8c0b1"</samp> </li> </ul> | <ul> <li> **Adobe Analytics:** <samp>a.media.vhlVersion</samp> </li> <li> **Heartbeats:** <samp>s:sp:hb_version</samp> </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** <samp>a.media.vhlVersion</samp> </li> <li> **Data Feed:** <samp>N/A</samp> </li> <li> **Audience Manager:** <samp>c_contextdata.a.media.vhlVersion</samp> </li> </ul> |


The heartbeat SDK version used for the tracking session.  Customers will have to create their own processing rules to have the value available for reporting.  \* <samp> <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank">MediaHeartbeat </a>.version();</samp> 
