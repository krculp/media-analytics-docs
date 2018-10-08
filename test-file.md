## **Stream Type** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** </li> <li> **API Key:** **`media.streamType`** </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5 </li> <li> **Sample value:** `"video"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.streamType` </li> <li> **Heartbeats:** `s:meta:a.media.streamType` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** `a.media.streamType` </li> <li> **Data Feed:** `videostreamtype` </li> <li> **Audience Manager:** `c_contextdata.a.media.streamType` </li> </ul> |

**Notes:**  
**Release Date:** **09/13/18** 
Available only through the <a href="media-collection-api.html"> Media Collection API (RESTful)</a>. Identifies the stream type. Valid values are "audio", "video", and "".  <a  href="segments.html"> Segments</a>: <ul> <li> StreamType "All" - Segment all media stream data.  **Rule:** Content (ID) exists </li> <li> StreamType "Audio" - Segment all audio stream data.  **Rule:** Content (ID) exists AND Stream Type = audio </li> <li> StreamType "Video" - Segment all video stream data.  **Rule:** Content (ID) exists AND Stream Type = video </li> </ul>

## **Content ID** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`mediaId\*`** </li> <li> **API Key:** `**media.id**` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"4586695ABC"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.name` </li> <li> **Heartbeats:** `s:asset:video_id` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** `a.media.name` </li> <li> **Data Feed:** `video` </li> <li> **Audience Manager:** `c_contextdata.a.media.name` </li> </ul> |

**Notes:**  
Content ID of the content, which can be used to tie back to other industry / CMS IDs, equal to the last value of `s:asset:video_id` . Any integer and/or letter combination.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (name, **_mediaId_**, length, streamType)` 

## **Content Length (variable)** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`length\*`** </li> <li> **API Key:** `**media.length**` </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any\*\* </li> <li> **Sample value:** <ul> <li> VOD: 128 </li> <li> Live: 86400 </li> <li> Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.length` </li> <li> **Heartbeats:** `l:asset:length` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Length (variable) </li> <li> **Context Data:** `a.media.length` </li> <li> **Data Feed:** `videolength` </li> <li> **Audience Manager:** `c_contextdata.a.media.length` </li> </ul>|

**Notes:**  
**Release Date:** **09/13/18** 
Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of `l:asset:length` from events of type Main. If `l:asset:length` is not set, then the last value of `l:asset:duration` is used.  In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  <span class="importanttitle"> Important:</span> This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.  For Live media with an unknown duration, the value of 86400 is the default.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (name, mediaId, **_length_**, streamType)` **\*\*** Pre Version 1.5.1, this was `l:asset:duration` ; after 1.5.1, this is `l:asset:length` .  

## **Video Length** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`length\*`** </li> <li> **API Key:** `**media.length**` </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any\*\* </li> <li> **Sample value:** <ul> <li> VOD: 128 </li> <li> Live: 86400 </li> <li> Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.length` </li> <li> **Heartbeats:** `l:asset:length` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Length </li> <li> **Context Data:** `a.media.length` </li> <li> **Data Feed:** `videoclassificationlength` </li> <li> **Audience Manager:** `c_contextdata.a.media.length` </li> </ul> |

#### Notes
**Release Date:** **09/27/18** 
Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of `l:asset:length` from events of type Main. If `l:asset:length` is not set, then the last value of `l:asset:duration` is used.  In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  <span class="importanttitle"> Important:</span> This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.  For Live media with an unknown duration, the value of 86400 is the default.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (name, mediaId, **_length_**, streamType)` **\*\*** Pre Version 1.5.1, this was `l:asset:duration` ; after 1.5.1, this is `l:asset:length` .  

## **Content Type** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`streamType\*`** </li> <li> **API Key:** `**media.contentType**` </li> <li> **Required:** Yes </li> <li> **Type:** restricted string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"vod"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.contentType` </li> <li> **Heartbeats:** `s:stream:type` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Type </li> <li> **Context Data:** `a.contentType` </li> <li> **Data Feed:** `videocontenttype` </li> <li> **Audience Manager:** `c_contextdata.a.contentType` </li> </ul> |

#### Notes
Available values per **Stream Type** :<ul> <li> **Audio:** "song", "podcast", "audiobook", "radio" </li> <li> **Video:** "VoD", "Live", "Linear", "UGC", "DVoD" </li> </ul> Customers can provide custom values for this parameter.  This equals `s:stream:type` . If that is unset, this equals `missing_content_type` .  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (name, mediaId, length, **_streamType_`** 

## **Video Session ID** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** Obtained from backend </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.8 </li> <li> **Sample value:** `1482236761294786918253` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.vsid` </li> <li> **Heartbeat:** `s:event:sid` </li> </ul> | <ul> <li> **Available:** Use processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** `a.media.vsid` </li> <li> **Data Feed:** `vsid` </li> <li> **Audience Manager:** `c_contextdata.a.media.vsid` </li> </ul> |

#### Notes
This identifies an instance of a content stream unique to an individual playback.  

## **Content Player Name** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`playerName\*`** </li> <li> **API Key:** `**media.playerName**` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"Brightcove"` , `"Primetime"` , etc.  </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.playerName` </li> <li> **Heartbeats:** `s:sp:player_name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Player Name </li> <li> **Context Data:** `a.media.playerName` </li> <li> **Data Feed:** `videoplayername` </li> <li> **Audience Manager:** `c_contextdata.a.media.playerName` </li> </ul> |

#### Notes
Name of the player.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a> .** _ playerName_`** 

## **Content Channel** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`channel\*`** </li> <li> **API Key:** `**media.channel**` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"Sports"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.channel` </li> <li> **Heartbeats:** `s:sp:channel` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Channel </li> <li> **Context Data:** `a.media.channel` </li> <li> **Data Feed:** `videochannel` </li> <li> **Audience Manager:** `c_contextdata.a.media.channel` </li> </ul> |

#### Notes
Distribution Station/Channels or where the content is played.  Any string value is accepted here.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a> .** _ channel_`** 

## **Content Segment** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"[0-10]"` (minutes) </li> </ul> | <ul> <li> **Adobe Analytics:** N/A </li> <li> **Heartbeats:** N/A </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Segment </li> <li> **Context Data:** `a.media.segment` </li> <li> **Data Feed:** `videosegment` </li> <li> **Audience Manager:** `c_contextdata.a.media.segment` </li> </ul> |

#### Notes
The interval that describes the part of the content that has been viewed (in minutes). The segment is computed as min and max of the playhead values during a playback session.  

## **Content Name (variable)** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`name\*`** </li> <li> **API Key:** `**media.name**` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** `"The Big Bang Theory"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.friendlyName` </li> <li> **Heartbeats:** `s:asset:name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Name (variable) </li> <li> **Context Data:** `a.media.friendlyName` </li> <li> **Data Feed:** `videoname` </li> <li> **Audience Manager:** `c_contextdata.a.media.friendlyName` </li> </ul> |

#### Notes
**Release Date:** **09/13/18** 
In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  This is the "friendly" (human-readable) name of the content, equal to the last value of `s:asset:name` .  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (** _ name_**, mediaId, length, streamType)` 

## **Video Name** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`name\*`** </li> <li> **API Key:** `**media.name**` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** `"The Big Bang Theory"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.friendlyName` </li> <li> **Heartbeats:** `s:asset:name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Name </li> <li> **Context Data:** `a.media.friendlyName` </li> <li> **Data Feed:** `videoclassificationname` </li> <li> **Audience Manager:** `c_contextdata.a.media.friendlyName` </li> </ul> |

#### Notes
**Release Date:** **09/27/18** 
This is the "friendly" (human-readable) name of the content, equal to the last value of `s:asset:name` .  In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (** _ name_**, mediaId, length, streamType)` 

## **Video Path** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"4586695ABC"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.name` </li> <li> **Heartbeats:** `s:asset:video_id` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** prop </li> <li> **Report Name:** Video Path </li> <li> **Context Data:** `a.media.name` </li> <li> **Data Feed:** `videopath` </li> <li> **Audience Manager:** `c_contextdata.a.media.name` </li> </ul> |

#### Notes
Ability to track path of viewer across site and/or App to see path they took to view a particular video. Any integer and/or letter combination.  

## **SDK Version** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** **`appVersion\*`** </li> <li> **API Key:** `**media.sdkVersion**` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** `"2.62.0_release"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.sdkVersion` </li> <li> **Heartbeats:** `s:sp:sdk` </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** _ </li> <li> **Context Data:** `a.media.sdkVersion` </li> <li> **Data Feed:** N/A </li> <li> **Audience Manager:** `c_contextdata.a.media.sdkVersion` </li> </ul> |

#### Notes
The SDK version used by the player. This could have any custom value that makes sense for your player. Customers will have to create their own processing rules to have the value available for reporting.  **\*** 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a> .** _ appVersion_`** 

## **VHL Version** 
| Implementation | Network Parameters | Reporting | 
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set\* </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** `"js-2.0.1.88-c8c0b1"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.vhlVersion` </li> <li> **Heartbeats:** `s:sp:hb_version` </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** `a.media.vhlVersion` </li> <li> **Data Feed:** N/A </li> <li> **Audience Manager:** `c_contextdata.a.media.vhlVersion` </li> </ul> | 

#### Notes
 The heartbeat SDK version used for the tracking session.  Customers will have to create their own processing rules to have the value available for reporting.  \* 

`<a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank"> MediaHeartbeat</a> .version();` 
