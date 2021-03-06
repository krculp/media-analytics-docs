# Table Transforming: HTML to MD

There are auto-magical converters online that do this conversion in a jiffy. 
But if you're offline (is that even possible), or you don't like the jiffy 
results, or you just like this sort of thing...

## Using `vi` to transform an HTML table to (mostly) Markdown

1. Copy your HTML table into a MD text file.
2. Combine all of the table lines into one line.
    `[Number of table lines]J` 
3. Put all tags on to their own lines. (Sub '<' char with '<[return]') 
    `:%s/</<ctrl-v[return]/g`
4. Delete all `<table>`, `<thead>`, and `<tbody>` tags. 
    (You are left with rows tags, cell tags, formatting tags, and cell content.) 
    `:%s/<\*.table.\*>//`, etc.
5. Substitute all `<th>` and `<td>` tags with the '|' char. 
    `:%s/<t[dh].\*>/|`
6. Substitute all `</tr>` tags with the '|' char. 
    (You now have your MD cell separators in the right places, albeit still on 
    their own lines.)

    **Note:** If your table uses row spans and column spans, you'll have to improvise 
    to get your MD table to behave. E.g., say you have an info block row spanning 3 
    columns, the second row of a 2 row span? I am pulling it out, and putting it below 
    each row.  Yes, a bunch of one-row tables with one cell turned into a header. 
    No really, it'll look great! ;-P
7. Delete all `<tr>` tags. 
    :%s/<tr.\*>//
8. Delete all `</th>` and `</td>` tags 
    `:%s/<\/t[dh]>//`
9. Delete all "spanny" kinds of tags that you can't or don't want to turn into MD 
    formatting, e.g. `<div>` tags, `<p>` tags, ...  You're now left with (mostly) 
    font formatting tags and list tags.
10. If you're using single asterisks for anything, say, footnotes, escape them. 
    `:%s\*/\\\\*/`
11. Turn your "simple" font formatting HTML tags into their MD counterparts.
    1. Get rid of any empty code font or bold font tag pairs, e.g. `<strong class="bleh"/>`. 
        `:%s/<strong.*\/>//`
    2. Optionally, get rid of parameters in tags. It's easier to see what's going on, 
        and they're extraneous to MD.
    3. Move your formatting tag pairs onto the same line, around the content.
        1. Determine how many of a tag there are ( :!grep "`<tag>`" [filename] | wc -l )
        2. Record to buffer 'q': Find opening tag; join the next line(s) with current one; 
            stop recording; repeat x times using your buffer: E.g., `15@q`

            To record: `qq; /<strong>;J;J;x;q` (the first 'q' starts recording, the second 'q' 
            is just a convenient name for a buffer to record into, the '/' is to find the 
            strong tag, then there are two joins, the 'x' after the 2 joins is to get rid 
            of a space, the last 'q' quits recording.
        3. Find examples where you join more or fewer lines, etc., then you clean up what 
            you must manually.
        4. Repeat with additional formatting tags.
    4. Clean up spacing around formatting tags and their enclosed content. (`Good: "Content <code>code text</code>"; Bad: "Content<code> code text</code>"`)
    5. Turn `<samp>` or `<code>` tags into '\`' chars.  
    6. Turn  `</samp>` or `</code>` tags into '\`' chars.  
    7. Repeat with `<strong>`/`<bold>`, `<em>/<i>`, etc., using their respective MD chars.  
12. **Lists:** I think your best bet is to stick with HTML list tags within table cells. 
    (Depends upon the SSG being used. GitBook doesn't like this idea at all. GitBook doesn't like you doing much at all in tables.)
13. Put everything into MD table rows:
    1. Join all table lines into one long one
    1. If you have a uniform number of cells in your rows, start recording, find (`f`) the correct number of '|' symbols, and add a carriage return. Repeat for n rows.
    1. If you don't have a uniform number of cells (e.g., column spans), your recording is slightly more complicated. (Find n '|' chars, add a return, find x, add a return...)
14. Create your MD table header ( `| --- | --- |` ) etc.
15. Done.
16. Hah hah hah hah!  Not likely. Render it and take a look.
17. Do some semi-manual, custom cleanup. ( See Step 6 above ) - 
    * Get rid of "Label" column; 
    * Adjust table header; 
    * Grab every second row (the col spanning row) and plant it under the row as a paragraph; 
    * Turn the "Label" into a ## Header above each row; 
    * Copy the table header rows to each individual table row. 
18. In conclusion: You could do all of 1-16 above very quickly if the table is simple. The above is in no way refined, just a slap-dashery of lower-intermediate vi messing-about.
    
    *Note:* This looks alright on GitHub. GitBook? Not so much. GB does not support a LOT of what GitHub renders correctly. If you have to use GitBook, you might just need to De-Table.

 
## Stream Type
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** </li> <li> **API Key:** `media.streamType` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5 </li> <li> **Sample value:** `"video"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.streamType` </li> <li> **Heartbeats:** `s:meta:a.media.streamType` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** `a.media.streamType` </li> <li> **Data Feed:** `videostreamtype` </li> <li> **Audience Manager:** `c_contextdata.a.media.streamType` </li> </ul> |

**Release Date: 09/13/18** 

Note: Available only through the <a href="media-collection-api.html">Media Collection API (RESTful) </a>.  

Identifies the stream type. Valid values are "audio", "video", and "".  

<a href="segments.html"><br/>Segments:</a> 
* StreamType "All" - Segment all media stream data.  **Rule:** Content (ID) exists  
* StreamType "Audio" - Segment all audio stream data.  **Rule:** Content (ID) exists AND Stream Type = audio  
* StreamType "Video" - Segment all video stream data.  **Rule:** Content (ID) exists AND Stream Type = video 

## Content ID
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `mediaId*` </li> <li> **API Key:** `media.id` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"4586695ABC"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.name` </li> <li> **Heartbeats:** `s:asset:video_id` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On VISIT </li> <li> **Report Name:** Content </li> <li> **Context Data:** `a.media.name` </li> <li> **Data Feed:** `video` </li> <li> **Audience Manager:** `c_contextdata.a.media.name` </li> </ul> |


Content ID of the content, which can be used to tie back to other industry / CMS IDs, equal to the last value of `s:asset:video_id`. Any integer and/or letter combination.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, **mediaId**, length, streamType) 

## Content Length (variable)
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `length*` </li> <li> **API Key:** `media.length` </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any+ </li> <li> **Sample value:** <ul> <li>VOD: 128 </li> <li>Live: 86400 </li> <li>Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.length` </li> <li> **Heartbeats:** `l:asset:length` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Length (variable) </li> <li> **Context Data:** `a.media.length` </li> <li> **Data Feed:** `videolength` </li> <li> **Audience Manager:** `c_contextdata.a.media.length` </li> </ul> |

**Release Date: 09/13/18** 

Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). 
It equals the last value of `l:asset:length` from events of type Main. 
If `l:asset:length` is not set, then the last value of `l:asset:duration` is used.  
In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  

**Important:** This property is used to compute several metrics, such as progress tracking 
metrics and Average Minute Audience. If this is not set, or not greater than zero, then 
these metrics are not available. For Live media with an unknown duration, the value of 86400 is the default.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, **length**, streamType) `

+ Pre Version 1.5.1, this was `l:asset:duration`; after 1.5.1, this is `l:asset:length`.  

## Video Length
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `length*` </li> <li> **API Key:** `media.length` </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any+ </li> <li> **Sample value:** <ul> <li>VOD: 128 </li> <li>Live: 86400 </li> <li>Linear: 1800 </li> </ul> </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.length` </li> <li> **Heartbeats:** `l:asset:length` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Length </li> <li> **Context Data:** `a.media.length` </li> <li> **Data Feed:** `videoclassificationlength` </li> <li> **Audience Manager:** `c_contextdata.a.media.length` </li> </ul> |

**Release Date: 09/27/18** 

Clip Length/Runtime - This is the maximum length (or duration) of the content being consumed (in seconds). It equals the last value of `l:asset:length` from events of type Main. If `l:asset:length` is not set, then the last value of `l:asset:duration` is used.  In reporting, Video Length is the classification, and Content Length (variable) is the eVAR.  

**Important:** This property is used to compute several metrics, such as progress tracking metrics and Average Minute Audience. If this is not set, or not greater than zero, then these metrics are not available. For Live media with an unknown duration, the value of 86400 is the default.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, **length**, streamType) 

+ Pre Version 1.5.1, this was `l:asset:duration`; after 1.5.1, this is `l:asset:length`.  

## Content Type
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `streamType*` </li> <li> **API Key:** `media.contentType` </li> <li> **Required:** Yes </li> <li> **Type:** restricted string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"vod"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.contentType` </li> <li> **Heartbeats:** `s:stream:type` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Type </li> <li> **Context Data:** `a.contentType` </li> <li> **Data Feed:** `videocontenttype` </li> <li> **Audience Manager:** `c_contextdata.a.contentType` </li> </ul> |

Available values per **Stream Type**: <ul> <li> **Audio:** "song", "podcast", "audiobook", "radio" </li> <li> **Video:** "VoD", "Live", "Linear", "UGC", "DVoD" </li> </ul> Customers can provide custom values for this parameter.  This equals `s:stream:type`. If that is unset, this equals `missing_content_type`.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>(name, mediaId, length, **streamType**) 

## Video Session ID
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** Obtained from backend </li> <li> **Required:** Yes </li> <li> **Type:** number </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.8 </li> <li> **Sample value:** `1482236761294786918253` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.vsid` </li> <li> **Heartbeat:** `s:event:sid` </li> </ul> | <ul> <li> **Available:** Use processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** `a.media.vsid` </li> <li> **Data Feed:** `vsid` </li> <li> **Audience Manager:** `c_contextdata.a.media.vsid` </li> </ul> |

This identifies an instance of a content stream unique to an individual playback.  

## Content Player Name
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `playerName*` </li> <li> **API Key:** `media.playerName` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"Brightcove"`, `"Primetime"`, etc.  </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.playerName` </li> <li> **Heartbeats:** `s:sp:player_name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Player Name </li> <li> **Context Data:** `a.media.playerName` </li> <li> **Data Feed:** `videoplayername` </li> <li> **Audience Manager:** `c_contextdata.a.media.playerName` </li> </ul> |

Name of the player.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>.  

## Content Channel
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `channel*` </li> <li> **API Key:** `media.channel` </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"Sports"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.channel` </li> <li> **Heartbeats:** `s:sp:channel` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Channel </li> <li> **Context Data:** `a.media.channel` </li> <li> **Data Feed:** `videochannel` </li> <li> **Audience Manager:** `c_contextdata.a.media.channel` </li> </ul> |

Distribution Station/Channels or where the content is played.  Any string value is accepted here.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>.

## Content Segment
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** Yes </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"[0-10]"` (minutes) </li> </ul> | <ul> <li> **Adobe Analytics:** N/A </li> <li> **Heartbeats:** N/A </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Segment </li> <li> **Context Data:** `a.media.segment` </li> <li> **Data Feed:** `videosegment` </li> <li> **Audience Manager:** `c_contextdata.a.media.segment` </li> </ul> |

The interval that describes the part of the content that has been viewed (in minutes). The segment is computed as min and max of the playhead values during a playback session.  

## Content Name (variable)
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `name*` </li> <li> **API Key:** `media.name` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** `"The Big Bang Theory"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.friendlyName` </li> <li> **Heartbeats:** `s:asset:name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** eVar </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Content Name (variable) </li> <li> **Context Data:** `a.media.friendlyName` </li> <li> **Data Feed:** `videoname` </li> <li> **Audience Manager:** `c_contextdata.a.media.friendlyName` </li> </ul> |

**Release Date: 09/13/18** 

In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  
This is the "friendly" (human-readable) name of the content, equal to the last value of `s:asset:name`.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>( **name**, mediaId, length, streamType) 

## Video Name
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `name*` </li> <li> **API Key:** `media.name` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate, Close </li> <li> **Min. SDK Version:** 1.5.1 </li> <li> **Sample value:** `"The Big Bang Theory"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.friendlyName` </li> <li> **Heartbeats:** `s:asset:name` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** classification </li> <li> **Expiration:** On HIT </li> <li> **Report Name:** Video Name </li> <li> **Context Data:** `a.media.friendlyName` </li> <li> **Data Feed:** `videoclassificationname` </li> <li> **Audience Manager:** `c_contextdata.a.media.friendlyName` </li> </ul> |

**Release Date: 09/27/18** 

This is the "friendly" (human-readable) name of the content, equal to the last value of `s:asset:name`.  
In reporting, Video Name is the classification, and Content Name (variable) is the eVAR.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject </a>( **name**, mediaId, length, streamType) 

## Video Path
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Initiate </li> <li> **Min. SDK Version:** Any </li> <li> **Sample value:** `"4586695ABC"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.name` </li> <li> **Heartbeats:** `s:asset:video_id` </li> </ul> | <ul> <li> **Available:** Yes </li> <li> **Reserved Variable:** prop </li> <li> **Report Name:** Video Path </li> <li> **Context Data:** `a.media.name` </li> <li> **Data Feed:** `videopath` </li> <li> **Audience Manager:** `c_contextdata.a.media.name` </li> </ul> |

Ability to track path of viewer across site and/or App to see path they took to view a particular video. Any integer and/or letter combination.  

## SDK Version
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** `appVersion\*` </li> <li> **API Key:** `media.sdkVersion` </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** `"2.62.0_release"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.sdkVersion` </li> <li> **Heartbeats:** `s:sp:sdk` </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** <em> </li> <li> **Context Data:** `a.media.sdkVersion` </li> <li> **Data Feed:** `N/A` </li> <li> **Audience Manager:** `c_contextdata.a.media.sdkVersion` </li> </ul> |

The SDK version used by the player. This could have any custom value that makes sense for your player. 
Customers will have to create their own processing rules to have the value available for reporting.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig </a>

## VHL Version
| Implementation | Network Parameters | Reporting |
| --- | --- | --- |
| <ul> <li> **SDK Key:** Automatically set\* </li> <li> **API Key:** N/A </li> <li> **Required:** No </li> <li> **Type:** string </li> <li> **Sent with:** Close </li> <li> **Min. SDK Version:** 1.5.7 </li> <li> **Sample value:** `"js-2.0.1.88-c8c0b1"` </li> </ul> | <ul> <li> **Adobe Analytics:** `a.media.vhlVersion` </li> <li> **Heartbeats:** `s:sp:hb_version` </li> </ul> | <ul> <li> **Available:** Use custom processing rule </li> <li> **Reserved Variable:** N/A </li> <li> **Report Name:** Custom </li> <li> **Context Data:** `a.media.vhlVersion` </li> <li> **Data Feed:** `N/A` </li> <li> **Audience Manager:** `c_contextdata.a.media.vhlVersion` </li> </ul> |

The heartbeat SDK version used for the tracking session.  
Customers will have to create their own processing rules to have the value available for reporting.  

\* <a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank">MediaHeartbeat </a>.version();
