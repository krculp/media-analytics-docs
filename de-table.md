# Turn Your HTML Table into a Mess

## Because your SSG can't handle HTML tables or even MD tables with formatting in the cells.

1. Shove everything far left.
1. Get rid of your `<table>` tags.
1. Get rid of your `<thead>` tags.
1. Get rid of your `<tbody>` tags.
1. Turn the table header row into the template for what each row will become.
    1. Turn the `<th>` tags into MD headers.
    1. Put the header tags on their own lines.
    1. Delete remaining tags
    1. Join header title to header tags.
    1. Adjust header level to your liking
1. For each row of the table, insert the appropriate header before its cell content
    1. Put your headers into buffers
    2. Make sure your `<td>` tags are on their own row.
    2. Create a recording that searches for each `<td>` tag in a row, and paste the
       appropriate header in a line above that tag.
    1. Put the remaining tags on their own lines.
    3. Delete tags you don't need at this point (`<tr> </tr> <td> </td> <div> </div> <ul> </ul> <p> </p>`)
    4. Turn remaining tags into MD. 
        1. Get your font formatting opening and closing tags on the same line.
        2. Clean up spacing


## **Stream Type**

### Implementation 
* **SDK Key:**  
* **API Key:** `**media.streamType**`  
* **Required:** Yes  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** 1.5  
* **Sample value:** `"video"`  

### Network Parameters 
* **Adobe Analytics:** `a.media.streamType`  
* **Heartbeats:** `s:meta:a.media.streamType`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On VISIT  
* **Report Name:** Content  
* **Context Data:** `a.media.streamType`  
* **Data Feed:** `videostreamtype`  
* **Audience Manager:** `c_contextdata.a.media.streamType`  

#### Notes
**Release Date: 09/13/18**

Identifies the stream type. Valid values are "audio", "video", and "".

<a href="segments.html"> Segments:</a>
* StreamType "All" - Segment all media stream data.  **Rule:** Content (ID) exists  
* StreamType "Audio" - Segment all audio stream data.  **Rule:** Content (ID) exists AND Stream Type = audio  
* StreamType "Video" - Segment all video stream data.  **Rule:** Content (ID) exists AND Stream Type = video  

## **Content ID**

### Implementation 
* **SDK Key:** `**mediaId\***`  
* **API Key:** `**media.id**`  
* **Required:** Yes  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any  
* **Sample value:** `"4586695ABC"`  

### Network Parameters 
* **Adobe Analytics:** `a.media.name`  
* **Heartbeats:** `s:asset:video_id`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On VISIT  
* **Report Name:** Content  
* **Context Data:** `a.media.name`  
* **Data Feed:** `video`  
* **Audience Manager:** `c_contextdata.a.media.name`  

#### Notes
Content ID of the content, which can be used to tie back to
other industry / CMS IDs, equal to the last value of `s:asset:video_id`. 

Any integer and/or letter combination.

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> (name, <strong> <em> mediaId </em> </strong> , length, streamType)

## **Content Length (variable)**

### Implementation 
* **SDK Key:** `**length\***`  
* **API Key:** `**media.length**`  
* **Required:** Yes  
* **Type:** number  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any+  
* **Sample value:** <li> VOD: 128  <li> Live: 86400 </li> <li> Linear: 1800 </li> </li> 

### Network Parameters 
* **Adobe Analytics:** `a.media.length`  
* **Heartbeats:** `l:asset:length`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Length (variable)  
* **Context Data:** `a.media.length`  
* **Data Feed:** `videolength`  
* **Audience Manager:** `c_contextdata.a.media.length`  

#### Notes
**Release Date: 09/13/18**

Clip Length/Runtime - This is the maximum length (or
duration) of the content being consumed (in seconds). 

It equals the last value of `l:asset:length`
from events of type Main. If `l:asset:length`
is not set, then the last value of
`l:asset:duration` is used.

In reporting, Video Length is the classification, and Content
Length (variable) is the eVAR.

This property is used to compute several metrics, such as progress tracking metrics and
Average Minute Audience. If this is not set, or not
greater than zero, then these metrics are not available.

For Live media with an unknown duration, the value of 86400 is the default. 

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> (name, mediaId, **<em> length </em>** , streamType)

**+** Pre Version 1.5.1, this was `l:asset:duration` ; after 1.5.1, this is `l:asset:length`
.

## **Video Length**

### Implementation 
* **SDK Key:** `**length\***`  
* **API Key:** `**media.length**`  
* **Required:** Yes  
* **Type:** number  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any+  
* **Sample value:** <li> VOD: 128  <li> Live: 86400 </li> <li> Linear: 1800 </li> </li> 

### Network Parameters 
* **Adobe Analytics:** `a.media.length`  
* **Heartbeats:** `l:asset:length`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** classification  
* **Expiration:** On HIT  
* **Report Name:** Video Length  
* **Context Data:** `a.media.length`  
* **Data Feed:** `videoclassificationlength`  
* **Audience Manager:** `c_contextdata.a.media.length`  

#### Notes
**Release Date: 09/27/18**

Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). 
It equals the last value of `l:asset:length` from events of type Main. 
If `l:asset:length` is not set, then the last value of `l:asset:duration` is used.

In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.
This property is used to compute several metrics, such as progress tracking metrics and
Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not
available.  

For Live media with an unknown duration, the value of 86400
is the default. 

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> (name, mediaId, **<em> length </em>** , streamType)
**+**
Pre Version 1.5.1, this was
`l:asset:duration`
; after 1.5.1, this is
`l:asset:length`
.

## **Content Type**

### Implementation 
* **SDK Key:** `**streamType\***`  
* **API Key:** `**media.contentType**`  
* **Required:** Yes  
* **Type:** restricted string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any  
* **Sample value:** `"vod"`  

### Network Parameters 
* **Adobe Analytics:** `a.contentType`  
* **Heartbeats:** `s:stream:type`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Type  
* **Context Data:** `a.contentType`  
* **Data Feed:** `videocontenttype`  
* **Audience Manager:** `c_contextdata.a.contentType`  

#### Notes
* **Audio:** "song", "podcast", "audiobook", "radio"  
* **Video:** "VoD", "Live", "Linear", "UGC", "DVoD"  

Customers can provide custom values for this parameter.
This equals `s:stream:type` . If that is unset, this equals `missing_content_type`.

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> (name, mediaId, length, **<em> streamType </em>**)

## **Video Session ID**

### Implementation 
* **SDK Key:** Automatically set  
* **API Key:** Obtained from backend  
* **Required:** Yes  
* **Type:** number  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** 1.5.8  
* **Sample value:** `1482236761294786918253`  

### Network Parameters 
* **Adobe Analytics:** `a.media.vsid`  
* 
**Heartbeat:**
`s:event:sid`  

### Reporting
* **Available:** Use processing rule  
* **Reserved Variable:** N/A  
* **Report Name:** Custom  
* **Context Data:** `a.media.vsid`  
* **Data Feed:** `vsid`  
* **Audience Manager:** `c_contextdata.a.media.vsid`  

#### Notes
This identifies an instance of a content stream unique to an
individual playback. 

## **Content Player Name**

### Implementation 
* **SDK Key:** `**playerName\***`  
* **API Key:** `**media.playerName**`  
* **Required:** Yes  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any  
* **Sample value:** `"Brightcove"` , `"Primetime"` , etc.   

### Network Parameters 
* **Adobe Analytics:** `a.media.playerName`  
* **Heartbeats:** `s:sp:player_name`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Player Name  
* **Context Data:** `a.media.playerName`  
* **Data Feed:** `videoplayername`  
* **Audience Manager:** `c_contextdata.a.media.playerName`  

#### Notes
Name of the player. 

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig </a>.  

## **Content Channel**

### Implementation 
* **SDK Key:** `**channel\***`  
* **API Key:** `**media.channel**`  
* **Required:** Yes  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** Any  
* **Sample value:** `"Sports"`  

### Network Parameters 
* **Adobe Analytics:** `a.media.channel`  
* **Heartbeats:** `s:sp:channel`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Channel  
* **Context Data:** `a.media.channel`  
* **Data Feed:** `videochannel`  
* **Audience Manager:** `c_contextdata.a.media.channel`  

#### Notes
Distribution Station/Channels or where the content is played.
Any string value is accepted here.

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig </a>.

## **Content Segment**

### Implementation 
* **SDK Key:** Automatically set  
* **API Key:** N/A  
* **Required:** Yes  
* **Type:** string  
* **Sent with:** Close  
* **Min. SDK Version:** Any  
* **Sample value:** `"[0-10]"` (minutes)  

### Network Parameters 
* **Adobe Analytics:** N/A  <li> **Heartbeats:** N/A </li> 

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Segment  
* **Context Data:** `a.media.segment`  
* **Data Feed:** `videosegment`  
* **Audience Manager:** `c_contextdata.a.media.segment`  

#### Notes
The interval that describes the part of the content that has
been viewed (in minutes). The segment is computed as min and
max of the playhead values during a playback session. 

## **Content Name (variable)**

### Implementation 
* **SDK Key:** `**name\***`  
* **API Key:** `**media.name**`  
* **Required:** No  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** 1.5.1  
* **Sample value:** `"The Big Bang Theory"`  

### Network Parameters 
* **Adobe Analytics:** `a.media.friendlyName`  
* **Heartbeats:** `s:asset:name`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** eVar  
* **Expiration:** On HIT  
* **Report Name:** Content Name (variable)  
* **Context Data:** `a.media.friendlyName`  
* **Data Feed:** `videoname`  
* **Audience Manager:** `c_contextdata.a.media.friendlyName`  

#### Notes
**Release Date: 09/13/18**

In reporting, Video Name is the classification, and Content
Name (variable) is the eVAR.

This is the "friendly" (human-readable) name of the content,
equal to the last value of `s:asset:name`.

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> ( **<em> name </em>** , mediaId, length, streamType)

## **Video Name**

### Implementation 
* **SDK Key:** `**name\***`  
* **API Key:** `**media.name**`  
* **Required:** No  
* **Type:** string  
* **Sent with:** Initiate, Close  
* **Min. SDK Version:** 1.5.1  
* **Sample value:** `"The Big Bang Theory"`  

### Network Parameters 
* **Adobe Analytics:** `a.media.friendlyName`  
* **Heartbeats:** `s:asset:name`  

### Reporting
* **Available:** Yes  
* **Reserved Variable:** classification  
* **Expiration:** On HIT  
* **Report Name:** Video Name  
* **Context Data:** `a.media.friendlyName`  
* **Data Feed:** `videoclassificationname`  
* **Audience Manager:** `c_contextdata.a.media.friendlyName`  

#### Notes
**Release Date: 09/27/18**

This is the "friendly" (human-readable) name of the content,
equal to the last value of `s:asset:name`.

In reporting, Video Name is the classification, and Content
Name (variable) is the eVAR.

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank"> createMediaObject </a> ( **<em> name </em>** , mediaId, length, streamType)

## **Video Path**

### Implementation 
* **SDK Key:** Automatically set  
* **API Key:** N/A 
* **Required:** No 
* **Type:** string 
* **Sent with:** Initiate 
* **Min. SDK Version:** Any 
* **Sample value:** `"4586695ABC"` 

### Network Parameters 
* **Adobe Analytics:** `a.media.name` 
* **Heartbeats:** `s:asset:video_id` 

### Reporting
* **Available:** Yes 
* **Reserved Variable:** prop 
* **Report Name:** Video Path 
* **Context Data:** `a.media.name` 
* **Data Feed:** `videopath` 
* **Audience Manager:** `c_contextdata.a.media.name` 

#### Notes
Ability to track path of viewer across site and/or App to see
path they took to view a particular video. Any integer
and/or letter combination.

## **SDK Version**

### Implementation 
* **SDK Key:** `**appVersion\***` 
* **API Key:** `**media.sdkVersion**` 
* **Required:** No 
* **Type:** string 
* **Sent with:** Close 
* **Min. SDK Version:** 1.5.7 
* **Sample value:** `"2.62.0_release"` 

### Network Parameters 
* **Adobe Analytics:** `a.media.sdkVersion` 
* **Heartbeats:** `s:sp:sdk` 

### Reporting
* **Available:** Use custom processing rule 
* **Reserved Variable:** N/A 
* **Report Name:** 
* **Context Data:** `a.media.sdkVersion` ` 
* **Data Feed:** `N/A` 
* **Audience Manager:** `c_contextdata.a.media.sdkVersion` 

#### Notes
The SDK version used by the player. This could have any
custom value that makes sense for your player. Customers
will have to create their own processing rules to have the
value available for reporting. 

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank"> MediaHeartbeatConfig </a>.  

## **VHL Version**

### Implementation 
* **SDK Key:** Automatically set\* 
* **API Key:** N/A 
* **Required:** No 
* **Type:** string 
* **Sent with:** Close 
* **Min. SDK Version:** 1.5.7 
* **Sample value:** `"js-2.0.1.88-c8c0b1"` 

### Network Parameters 
* **Adobe Analytics:** `a.media.vhlVersion` 
* **Heartbeats:** `s:sp:hb_version` 

### Reporting
* **Available:** Use custom processing rule 
* **Reserved Variable:** N/A 
* **Report Name:** Custom 
* **Context Data:** `a.media.vhlVersion` 
* **Data Feed:** `N/A` 
* **Audience Manager:** `c_contextdata.a.media.vhlVersion` 

#### Notes
The heartbeat SDK version used for the tracking session.
Customers will have to create their own processing rules to
have the value available for reporting. 

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank"> MediaHeartbeat </a> .version();
