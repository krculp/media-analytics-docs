# Test File
This fantastic file was created to be used for trying out various merging scenarios.
Here's a chunk of HTML table code:

<table cellpadding="4" cellspacing="0" summary="" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__table_t4x_th2_k1b" frame="border" border="1" rules="all">
    <thead align="left">
        <tr>
    <th align="center" valign="middle" width="10%" id="d8318e204">
    <p>Label </p>
    </th>
    <th align="center" valign="middle" width="30%" id="d8318e210">
    <p>Implementation </p>
    </th>
    <th align="center" valign="middle" width="30%" id="d8318e216">
    <p>Network Parameters </p>
    </th>
    <th align="center" valign="middle" width="30%" id="d8318e222">
    <p>Reporting</p>
    </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
    <p><strong>Stream Type</strong>
    </p>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e210 ">
                <div>
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_dt3_htw_41b">
                <li><strong>SDK Key:</strong> <samp><strong /></samp>
                </li>
                <li><strong>API Key:
                </strong><samp><strong>media.streamType</strong></samp></li>
                <li><strong>Required:</strong> Yes </li>
                <li><strong>Type:</strong> string</li>
                <li><strong>Sent with:</strong> Initiate, Close</li>
                <li><strong>Min. SDK Version:</strong> 1.5</li>
                <li><strong>Sample value:</strong> <samp>"video" </samp></li>
                </ul>
                </div>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e216 ">
                <div>
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_et3_htw_41b">
                <li><strong>Adobe Analytics:</strong> 
                <p><samp>a.media.streamType</samp></p>
                </li>
                <li><strong>Heartbeats:
                </strong><p><samp>s:meta:a.media.streamType</samp></p>
                </li>
                </ul>
                </div>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e222 ">
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ft3_htw_41b">
                <li><strong>Available:</strong> Yes</li>
                <li><strong>Reserved Variable:</strong> eVar</li>
                <li><strong>Expiration:</strong> On VISIT</li>
                <li><strong>Report Name:</strong> Content</li>
                <li><strong>Context Data:
                </strong><samp>a.media.streamType</samp></li>
                <li><strong>Data Feed:</strong> <samp>videostreamtype</samp></li>
                <li><strong>Audience Manager:
                </strong><samp>c_contextdata.a.media.streamType</samp></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td colspan="4" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
                <p><strong>Release Date: 09/13/18</strong></p>
                <div><span>Note:</span> Available only through the <a href="media-collection-api.html">Media Collection API (RESTful)</a>.</div>
                <p>Identifies the stream type. Valid values are "audio",
                "video", and "".</p>
                <p><strong><a href="segments.html">Segments</a>:</strong></p>
                <div>
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xzh_mff_ffb">
                <li>StreamType "All" - Segment all media stream data.
                <strong>Rule:</strong> Content (ID) exists</li>
                <li>StreamType "Audio" - Segment all audio stream data.
                <strong>Rule:</strong> Content (ID) exists AND Stream Type =
                audio</li>
                <li>StreamType "Video" - Segment all video stream data.
                <strong>Rule:</strong> Content (ID) exists AND Stream Type =
                video</li>
                </ul>
                </div>
            </td>
        </tr>
        <tr>
            <td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
                <p><strong>Content ID</strong> </p>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e210 ">
                <div>
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_pjx_1ts_1fb">
                <li><strong>SDK Key:</strong> <samp><strong>mediaId*</strong></samp>
                </li>
                <li><strong>API Key:
                </strong><samp><strong>media.id</strong></samp></li>
                <li><strong>Required:</strong> Yes </li>
                <li><strong>Type:</strong> string</li>
                <li><strong>Sent with:</strong> Initiate, Close</li>
                <li><strong>Min. SDK Version:</strong> Any</li>
                <li><strong>Sample value:</strong> <samp>"4586695ABC"
                </samp></li>
                </ul>
                </div>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e216 ">
                <div>
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_qjx_1ts_1fb">
                <li><strong>Adobe Analytics:</strong> 
                <p><samp>a.media.name</samp></p>
                </li>
                <li><strong>Heartbeats:
                </strong><p><samp>s:asset:video_id</samp></p>
                </li>
                </ul>
                </div>
            </td>
            <td align="left" valign="top" width="30%" headers="d8318e222 ">
                <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_rjx_1ts_1fb">
                <li><strong>Available:</strong> Yes</li>
                <li><strong>Reserved Variable:</strong> eVar</li>
                <li><strong>Expiration:</strong> On VISIT</li>
                <li><strong>Report Name:</strong> Content</li>
                <li><strong>Context Data:</strong> <samp>a.media.name</samp></li>
                <li><strong>Data Feed:</strong> <samp>video</samp></li>
                <li><strong>Audience Manager:
                </strong><samp>c_contextdata.a.media.name</samp></li>
                </ul>
            </td>
        </tr>
        <tr>
            <td colspan="4" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
                <p>Content ID of the content, which can be used to tie back to
                other industry / CMS IDs, equal to the last value of
                <samp>s:asset:video_id</samp>. Any integer and/or
                letter combination.</p>
                <p><strong>*</strong>
                <samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name,
                <strong><em>mediaId</em></strong>, length,
                streamType)</samp></p>
            </td>
        </tr>
    </tbody>
</table>
