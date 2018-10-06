# Test File This fantastic file was created to be used for trying out various merging scenarios.

| Label | Implementation | Network Parameters | Reporting |
| --- | --- | --- | --- |
| **Stream Type** | * **SDK Key:** * **API Key:** `**media.streamType**` * **Required:** Yes * **Type:** string * **Sent with:** Initiate, Close * **Min. SDK Version:** 1.5 * **Sample value:** `"video"` | * **Adobe Analytics:** `a.media.streamType` * **Heartbeats:** `s:meta:a.media.streamType` | * **Available:** Yes * **Reserved Variable:** eVar * **Expiration:** On VISIT * **Report Name:** Content * **Context Data:** `a.media.streamType` * **Data Feed:** `videostreamtype` * **Audience Manager:** `c_contextdata.a.media.streamType` |
|| **Release Date: 09/13/18** Note: Available only through the <a class="xref" href="media-collection-api.html"> Media Collection API (RESTful)</a>.  Identifies the stream type. Valid values are "audio", "video", and "".  **<a class="xref" href="segments.html"> Segments</a> :** * StreamType "All" - Segment all media stream data.  **Rule:** Content (ID) exists * StreamType "Audio" - Segment all audio stream data.  **Rule:** Content (ID) exists AND Stream Type = audio * StreamType "Video" - Segment all video stream data.  **Rule:** Content (ID) exists AND Stream Type = video |||

<!--
**Content ID**


|


* **SDK Key:** `**mediaId\***`

* **API Key:** `**media.id**`

* **Required:** Yes 
* **Type:** string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any
* **Sample value:** `"4586695ABC"`




|


* **Adobe Analytics:** `a.media.name`


* **Heartbeats:** `s:asset:video_id`





|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On VISIT
* **Report Name:** Content
* **Context Data:** `a.media.name`

* **Data Feed:** `video`

* **Audience Manager:** `c_contextdata.a.media.name`



|

|
Content ID of the content, which can be used to tie back to other industry / CMS IDs, equal to the last value of `s:asset:video_id`. Any integer and/or letter combination.

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a> (name,**_mediaId_**, length, streamType)`

|

|

**Content Length (variable)**


|


* **SDK Key:** `**length\***`

* **API Key:** `**media.length**`

* **Required:** Yes
* **Type:** number
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any\** * 
**Sample value:** * VOD: 128
* Live: 86400
* Linear: 1800





|


* **Adobe Analytics:** `a.media.length`


* **Heartbeats:** `l:asset:length`





|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On HIT
* **Report Name:** Content Length (variable)
* **Context Data:** `a.media.length`

* **Data Feed:** `videolength`

* **Audience Manager:** `c_contextdata.a.media.length`



|

|

**Release Date: 09/13/18**

Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of 
`l:asset:length` from events of type Main. If 
`l:asset:length` is not set, then the last value of 
`l:asset:duration` is used.
In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.


<span class="importanttitle"> Important:</span> This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.

For Live media with an unknown duration, the value of 86400 is the default. 

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a>
(name, mediaId,**
_length_**, streamType)`

**\**** Pre Version 1.5.1, this was 
`l:asset:duration`
; after 1.5.1, this is 
`l:asset:length`
.

|

|

**Video Length**


|


* **SDK Key:** `**length\***`

* **API Key:** `**media.length**`

* **Required:** Yes
* **Type:** number
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any\** * **Sample value:** * VOD: 128
* Live: 86400
* Linear: 1800





|


* **Adobe Analytics:** `a.media.length`


* **Heartbeats:** `l:asset:length`





|

* **Available:** Yes
* **Reserved Variable:** classification
* **Expiration:** On HIT
* **Report Name:** Video Length
* **Context Data:** `a.media.length`

* **Data Feed:** `videoclassificationlength`

* **Audience Manager:** `c_contextdata.a.media.length`



|

|

**Release Date: 09/27/18**

Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of 
`l:asset:length` from events of type Main. If 
`l:asset:length` is not set, then the last value of 
`l:asset:duration` is used.
In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.


<span class="importanttitle"> Important:</span> This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available.

For Live media with an unknown duration, the value of 86400 is the default. 

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a>
(name, mediaId,**
_length_**, streamType)`


**\**** Pre Version 1.5.1, this was 
`l:asset:duration`
; after 1.5.1, this is 
`l:asset:length`
.

|

|

**Content Type**


|


* **SDK Key:** `**streamType\***`

* **API Key:** `**media.contentType**`

* **Required:** Yes 
* **Type:** restricted string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any
* **Sample value:** `"vod"`




|


* **Adobe Analytics:** `a.contentType`


* **Heartbeats:** `s:stream:type`





|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On HIT
* **Report Name:** Content Type 
* **Context Data:** `a.contentType`

* **Data Feed:** `videocontenttype`

* **Audience Manager:** `c_contextdata.a.contentType`



|

|
Available values per** Stream Type**
:
* **Audio:** "song", "podcast", "audiobook", "radio"
* **Video:** "VoD", "Live", "Linear", "UGC", "DVoD"
Customers can provide custom values for this parameter.
This equals 
`s:stream:type`
. If that is unset, this equals 
`missing_content_type`
.

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a>
(name, mediaId, length,**
_streamType_**)`


|

|

**Video Session ID**


|


* **SDK Key:** Automatically set
* **API Key:** Obtained from backend
* **Required:** Yes 
* **Type:** number
* **Sent with:** Initiate, Close
* **Min. SDK Version:** 1.5.8
* **Sample value:** `1482236761294786918253`




|


* **Adobe Analytics:** `a.media.vsid`


* **Heartbeat:** `s:event:sid`




|

* **Available:** Use processing rule
* **Reserved Variable:** N/A
* **Report Name:** Custom 
* **Context Data:** `a.media.vsid`

* **Data Feed:** `vsid`

* **Audience Manager:** `c_contextdata.a.media.vsid`



|

|
This identifies an instance of a content stream unique to an individual playback. 

|

|

**Content Player Name**


|


* **SDK Key:** `**playerName\***`

* **API Key:** `**media.playerName**`

* **Required:** Yes
* **Type:** string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any
* **Sample value:** `"Brightcove"`
, 
`"Primetime"`
, etc. 



|


* **Adobe Analytics:** `a.media.playerName`


* **Heartbeats:** `s:sp:player_name`





|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On HIT
* **Report Name:** Content Player Name 
* **Context Data:** `a.media.playerName`

* **Data Feed:** `videoplayername`

* **Audience Manager:** `c_contextdata.a.media.playerName`



|

|
Name of the player. 

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a>
.**
_playerName_**`


|

|

**Content Channel**


|


* **SDK Key:** `**channel\***`

* **API Key:** `**media.channel**`

* **Required:** Yes
* **Type:** string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** Any
* **Sample value:** `"Sports"`




|


* **Adobe Analytics:** `a.media.channel`


* **Heartbeats:** `s:sp:channel`





|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On HIT
* **Report Name:** Content Channel 
* **Context Data:** `a.media.channel`

* **Data Feed:** `videochannel`

* **Audience Manager:** `c_contextdata.a.media.channel`



|

|
Distribution Station/Channels or where the content is played.  Any string value is accepted here.

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a>
.**
_channel_**`


|

|

**Content Segment**


|


* **SDK Key:** Automatically set 
* **API Key:** N/A
* **Required:** Yes 
* **Type:** string
* **Sent with:** Close
* **Min. SDK Version:** Any
* **Sample value:** `"[0-10]"`
(minutes) 




|


* **Adobe Analytics:** N/A 
* **Heartbeats:** N/A



|

* **Available:** Yes
* **Reserved Variable:** eVar
* **Expiration:** On HIT
* **Report Name:** Content Segment 
* **Context Data:** `a.media.segment`

* **Data Feed:** `videosegment`

* **Audience Manager:** `c_contextdata.a.media.segment`



|

|
The interval that describes the part of the content that has been viewed (in minutes). The segment is computed as min and max of the playhead values during a playback session. 

|

|

**Content Name (variable)**


|


* **SDK Key:** `**name\***`

* **API Key:** `**media.name**`

* **Required:** No 
* **Type:** string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** 1.5.1
* **Sample value:** `"The Big Bang Theory"`




|


* **Adobe Analytics:** `a.media.friendlyName`


* **Heartbeats:** `s:asset:name`





|

* **Available:** Yes
* **Reserved Variable:** eVar 
* **Expiration:** On HIT
* **Report Name:** Content Name (variable)
* **Context Data:** `a.media.friendlyName`

* **Data Feed:** `videoname`

* **Audience Manager:** `c_contextdata.a.media.friendlyName`



|

|

**Release Date: 09/13/18**

In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.
This is the "friendly" (human-readable) name of the content, equal to the last value of 
`s:asset:name`
.

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a>
(**
_name_**, mediaId, length, streamType)`


|

|

**Video Name**


|


* **SDK Key:** `**name\***`

* **API Key:** `**media.name**`

* **Required:** No 
* **Type:** string
* **Sent with:** Initiate, Close
* **Min. SDK Version:** 1.5.1
* **Sample value:** `"The Big Bang Theory"`




|


* **Adobe Analytics:** `a.media.friendlyName`


* **Heartbeats:** `s:asset:name`





|

* **Available:** Yes
* **Reserved Variable:** classification 
* **Expiration:** On HIT
* **Report Name:** Video Name
* **Context Data:** `a.media.friendlyName`

* **Data Feed:** `videoclassificationname`

* **Audience Manager:** `c_contextdata.a.media.friendlyName`



|

|

**Release Date: 09/27/18**

This is the "friendly" (human-readable) name of the content, equal to the last value of 
`s:asset:name`
.
In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject</a>
(**
_name_**, mediaId, length, streamType)`


|

|

**Video Path**


|


* **SDK Key:** Automatically set 
* **API Key:** N/A
* **Required:** No 
* **Type:** string
* **Sent with:** Initiate
* **Min. SDK Version:** Any
* **Sample value:** `"4586695ABC"`




|


* **Adobe Analytics:** `a.media.name`


* **Heartbeats:** `s:asset:video_id`





|

* **Available:** Yes
* **Reserved Variable:** prop
* **Report Name:** Video Path 
* **Context Data:** `a.media.name`

* **Data Feed:** `videopath`

* **Audience Manager:** `c_contextdata.a.media.name`



|

|
Ability to track path of viewer across site and/or App to see path they took to view a particular video. Any integer and/or letter combination.

|

|

**SDK Version**


|


* **SDK Key:** `**appVersion\***`

* **API Key:** `**media.sdkVersion**`

* **Required:** No 
* **Type:** string
* **Sent with:** Close
* **Min. SDK Version:** 1.5.7
* **Sample value:** `"2.62.0_release"`




|


* **Adobe Analytics:** `a.media.sdkVersion`


* **Heartbeats:** `s:sp:sdk`





|

* **Available:** Use custom processing rule
* **Reserved Variable:** N/A
* **Report Name:** _* 
**Context Data:** `a.media.sdkVersion`

* **Data Feed:** N/A

* **Audience Manager:** `c_contextdata.a.media.sdkVersion`



|

|
The SDK version used by the player. This could have any custom value that makes sense for your player. Customers will have to create their own processing rules to have the value available for reporting. 

**\***

`<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig</a>
.**
_appVersion_**`


|

|

**VHL Version**


|


* **SDK Key:** Automatically set\* 
* **API Key:** N/A
* **Required:** No 
* **Type:** string
* **Sent with:** Close
* **Min. SDK Version:** 1.5.7
* **Sample value:** `"js-2.0.1.88-c8c0b1"`




|


* **Adobe Analytics:** `a.media.vhlVersion`


* **Heartbeats:** `s:sp:hb_version`





|

* **Available:** Use custom processing rule
* **Reserved Variable:** N/A
* **Report Name:** Custom 
* **Context Data:** `a.media.vhlVersion`

* **Data Feed:** N/A

* **Audience Manager:** `c_contextdata.a.media.vhlVersion`



|

|
The heartbeat SDK version used for the tracking session.  Customers will have to create their own processing rules to have the value available for reporting. 

\* `<a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank"> MediaHeartbeat</a>
.version();`


|

-->
