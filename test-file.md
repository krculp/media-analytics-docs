# Test File

This fantastic file was created to be used for trying out various merging scenarios.

Here's a chunk of HTML table code:

<div><table cellpadding="4" cellspacing="0" summary="" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__table_t4x_th2_k1b" frame="border" border="1" rules="all">
						
						
						
						
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
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
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
									<p><strong>Content ID</strong>
									</p>

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
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
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

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Length (variable)</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_gt3_htw_41b">
											<li><strong>SDK Key:</strong> <samp><strong>length*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.length</strong></samp></li>

											<li><strong>Required:</strong> Yes</li>

											<li><strong>Type:</strong> number</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> Any**</li>

											<li><strong>Sample value:</strong> <ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ljx_yr1_41b">
												<li>VOD: 128</li>

												<li>Live: 86400</li>

												<li>Linear: 1800</li>

												</ul>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ht3_htw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.length</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>l:asset:length</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_it3_htw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Length (variable)</li>

										<li><strong>Context Data:
											</strong><samp>a.media.length</samp></li>

										<li><strong>Data Feed:</strong> <samp>videolength</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.length</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p><strong>Release Date: 09/13/18</strong></p>

									<p>Clip Length/Runtime - This is the maximum length (or
										duration) of the content being consumed (in seconds). It
										equals the last value of <samp>l:asset:length</samp>
										from events of type Main. If <samp>l:asset:length</samp>
										is not set, then the last value of
											<samp>l:asset:duration</samp> is used.</p>

									<p>In reporting, Video Length is the classification, and Content
										Length (variable) is the eVAR.</p>

									<div>
										<div><span>Important:</span> This property is used to compute
											several metrics, such as progress tracking metrics and
											Average Minute Audience. If this is not set, or not
											greater than zero, then these metrics are not
											available.</div>

									</div>

									<p>For Live media with an unknown duration, the value of 86400 is the default. </p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId,
												<strong><em>length</em></strong>, streamType)</samp></p>

									<p><strong>**</strong> Pre Version 1.5.1, this was
											<samp>l:asset:duration</samp>; after 1.5.1, this is
											<samp>l:asset:length</samp>.</p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Video Length</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_kgk_qrk_hfb">
											<li><strong>SDK Key:</strong>
												<samp><strong>length*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.length</strong></samp></li>

											<li><strong>Required:</strong> Yes</li>

											<li><strong>Type:</strong> number</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> Any**</li>

											<li><strong>Sample value:</strong>
												<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_lgk_qrk_hfb">
												<li>VOD: 128</li>

												<li>Live: 86400</li>

												<li>Linear: 1800</li>

												</ul>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_mgk_qrk_hfb">
											<li><strong>Adobe Analytics:</strong>
												<p><samp>a.media.length</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>l:asset:length</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ngk_qrk_hfb">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> classification</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Video Length</li>

										<li><strong>Context Data:
											</strong><samp>a.media.length</samp></li>

										<li><strong>Data Feed:</strong>
											<samp>videoclassificationlength</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.length</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p><strong>Release Date: 09/27/18</strong></p>

									<p>Clip Length/Runtime - This is the maximum length (or
										duration) of the content being consumed (in seconds). It
										equals the last value of <samp>l:asset:length</samp>
										from events of type Main. If <samp>l:asset:length</samp>
										is not set, then the last value of
											<samp>l:asset:duration</samp> is used.</p>

									<p>In reporting, Video Length is the classification, and Content
										Length (variable) is the eVAR.</p>

									<div>
										<div><span>Important:</span> This property is used to compute
											several metrics, such as progress tracking metrics and
											Average Minute Audience. If this is not set, or not
											greater than zero, then these metrics are not
											available.</div>

									</div>

									<p>For Live media with an unknown duration, the value of 86400
										is the default. </p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId,
												<strong><em>length</em></strong>, streamType)</samp></p>

									<p><strong>**</strong> Pre Version 1.5.1, this was
											<samp>l:asset:duration</samp>; after 1.5.1, this is
											<samp>l:asset:length</samp>.</p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Type</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_jt3_htw_41b">
											<li><strong>SDK Key:</strong> <samp><strong>streamType*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.contentType</strong></samp></li>

											<li><strong>Required:</strong> Yes </li>

											<li><strong>Type:</strong> restricted string</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> Any</li>

											<li><strong>Sample value:</strong> <samp>"vod"</samp>
											</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_kt3_htw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.contentType</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:stream:type</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_lt3_htw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Type </li>

										<li><strong>Context Data:</strong> <samp>a.contentType</samp></li>

										<li><strong>Data Feed:</strong> <samp>videocontenttype</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.contentType</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<div>Available values per <strong>Stream Type</strong>:<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_n2w_vxs_1fb">
											<li><strong>Audio:</strong> "song", "podcast", "audiobook",
												"radio"</li>

											<li><strong>Video:</strong> "VoD", "Live", "Linear", "UGC",
												"DVoD"</li>

										</ul>
Customers can provide custom values for this
										parameter.</div>

									<p>This equals <samp>s:stream:type</samp>. If that is unset,
										this equals <samp>missing_content_type</samp>.</p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId, length,
												<strong><em>streamType</em></strong>)</samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Video Session ID</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_mt3_htw_41b">
											<li><strong>SDK Key:</strong> Automatically set</li>

											<li><strong>API Key:</strong> Obtained from backend</li>

											<li><strong>Required:</strong> Yes </li>

											<li><strong>Type:</strong> number</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> 1.5.8</li>

											<li><strong>Sample value:
												</strong><samp>1482236761294786918253</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_nt3_htw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.vsid</samp></p>
</li>

											<li><strong>Heartbeat:</strong> <samp>s:event:sid</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ot3_htw_41b">
										<li><strong>Available:</strong> Use processing rule</li>

										<li><strong>Reserved Variable:</strong> N/A</li>

										<li><strong>Report Name:</strong> Custom </li>

										<li><strong>Context Data:</strong> <samp>a.media.vsid</samp></li>

										<li><strong>Data Feed:</strong> <samp>vsid</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.vsid</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>This identifies an instance of a content stream unique to an
										individual playback. </p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Player Name</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_pt3_htw_41b">
											<li><strong>SDK Key:</strong> <samp><strong>playerName*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.playerName</strong></samp></li>

											<li><strong>Required:</strong> Yes</li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> Any</li>

											<li><strong>Sample value:</strong> <samp>"Brightcove"</samp>,
												<samp>"Primetime"</samp>, etc. </li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_qt3_htw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.playerName</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:sp:player_name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_rt3_htw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Player Name </li>

										<li><strong>Context Data:
											</strong><samp>a.media.playerName</samp></li>

										<li><strong>Data Feed:</strong> <samp>videoplayername</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.playerName</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>Name of the player. </p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong><em>playerName</em></strong></samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Channel</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_st3_htw_41b">
											<li><strong>SDK Key:</strong> <samp><strong>channel*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.channel</strong></samp></li>

											<li><strong>Required:</strong> Yes</li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> Any</li>

											<li><strong>Sample value:</strong> <samp>"Sports"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_tt3_htw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.channel </samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:sp:channel</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ut3_htw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Channel </li>

										<li><strong>Context Data:</strong> <samp>a.media.channel
											</samp></li>

										<li><strong>Data Feed:</strong> <samp>videochannel</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.channel
											</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>Distribution Station/Channels or where the content is played.
										Any string value is accepted here.</p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong><em>channel</em></strong></samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Segment</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vt3_htw_41b">
											<li><strong>SDK Key:</strong> Automatically set </li>

											<li><strong>API Key:</strong> N/A</li>

											<li><strong>Required:</strong> Yes </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Close</li>

											<li><strong>Min. SDK Version:</strong> Any</li>

											<li><strong>Sample value:</strong> <p><samp>"[0-10]"</samp>
												(minutes) </p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wt3_htw_41b">
											<li><strong>Adobe Analytics:</strong> N/A </li>

											<li><strong>Heartbeats:</strong> N/A</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xt3_htw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar</li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Segment </li>

										<li><strong>Context Data:
											</strong><samp>a.media.segment</samp></li>

										<li><strong>Data Feed:</strong> <samp>videosegment</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.segment</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>The interval that describes the part of the content that has
										been viewed (in minutes). The segment is computed as min and
										max of the playhead values during a playback session. </p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Content Name (variable)</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_fd2_5bm_n1b">
											<li><strong>SDK Key:</strong> <samp><strong>name*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.name</strong></samp></li>

											<li><strong>Required:</strong> No </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> 1.5.1</li>

											<li><strong>Sample value:</strong> <samp>"The Big Bang
												Theory"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_epx_th2_k1b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.friendlyName</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:asset:name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_fpx_th2_k1b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> eVar </li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Content Name (variable)</li>

										<li><strong>Context Data:
												</strong><samp>a.media.friendlyName</samp></li>

										<li><strong>Data Feed:</strong> <samp>videoname</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.friendlyName</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p><strong>Release Date: 09/13/18</strong></p>

									<p>In reporting, Video Name is the classification, and Content
										Name (variable) is the eVAR.</p>

									<p>This is the "friendly" (human-readable) name of the content,
										equal to the last value of
										<samp>s:asset:name</samp>.</p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(<strong><em>name</em></strong>,
											mediaId, length, streamType)</samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Video Name</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vqq_frk_hfb">
											<li><strong>SDK Key:</strong>
												<samp><strong>name*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.name</strong></samp></li>

											<li><strong>Required:</strong> No </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Initiate, Close</li>

											<li><strong>Min. SDK Version:</strong> 1.5.1</li>

											<li><strong>Sample value:</strong>
												<samp>"The Big Bang Theory"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wqq_frk_hfb">
											<li><strong>Adobe Analytics:</strong>
												<p><samp>a.media.friendlyName</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:asset:name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xqq_frk_hfb">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> classification </li>

										<li><strong>Expiration:</strong> On HIT</li>

										<li><strong>Report Name:</strong> Video Name</li>

										<li><strong>Context Data:
												</strong><samp>a.media.friendlyName</samp></li>

										<li><strong>Data Feed:</strong>
											<samp>videoclassificationname</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.friendlyName</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p><strong>Release Date: 09/27/18</strong></p>

									<p>This is the "friendly" (human-readable) name of the content,
										equal to the last value of
										<samp>s:asset:name</samp>.</p>

									<p>In reporting, Video Name is the classification, and Content
										Name (variable) is the eVAR.</p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(<strong><em>name</em></strong>,
											mediaId, length, streamType)</samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>Video Path</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_twm_jtw_41b">
											<li><strong>SDK Key:</strong> Automatically set </li>

											<li><strong>API Key:</strong> N/A</li>

											<li><strong>Required:</strong> No </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Initiate</li>

											<li><strong>Min. SDK Version:</strong> Any</li>

											<li><strong>Sample value:
												</strong><samp>"4586695ABC"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_uwm_jtw_41b">
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
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vwm_jtw_41b">
										<li><strong>Available:</strong> Yes</li>

										<li><strong>Reserved Variable:</strong> prop</li>

										<li><strong>Report Name:</strong> Video Path </li>

										<li><strong>Context Data:</strong> <samp>a.media.name</samp></li>

										<li><strong>Data Feed:</strong> <samp>videopath</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.name</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>Ability to track path of viewer across site and/or App to see
										path they took to view a particular video. Any integer
										and/or letter combination.</p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>SDK Version</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wwm_jtw_41b">
											<li><strong>SDK Key:</strong> <samp><strong>appVersion*</strong></samp>
											</li>

											<li><strong>API Key:
												</strong><samp><strong>media.sdkVersion</strong></samp></li>

											<li><strong>Required:</strong> No </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Close</li>

											<li><strong>Min. SDK Version:</strong> 1.5.7</li>

											<li><strong>Sample value:
												</strong><samp>"2.62.0_release"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xwm_jtw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.sdkVersion</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:sp:sdk</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ywm_jtw_41b">
										<li><strong>Available:</strong> Use custom processing rule</li>

										<li><strong>Reserved Variable:</strong> N/A</li>

										<li><strong>Report Name:</strong> />
										</li>

										<li><strong>Context Data:
											</strong><samp>a.media.sdkVersion</samp>`</li>

										<li><strong>Data Feed:</strong> <samp>N/A</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.sdkVersion</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>The SDK version used by the player. This could have any
										custom value that makes sense for your player. Customers
										will have to create their own processing rules to have the
										value available for reporting. </p>

									<p><strong>*</strong>
										<samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong><em>appVersion</em></strong></samp></p>

								</td>

							</tr>

							<tr>
								<td rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p><strong>VHL Version</strong>
									</p>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e210 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_zwm_jtw_41b">
											<li><strong>SDK Key:</strong> Automatically set* </li>

											<li><strong>API Key:</strong> N/A</li>

											<li><strong>Required:</strong> No </li>

											<li><strong>Type:</strong> string</li>

											<li><strong>Sent with:</strong> Close</li>

											<li><strong>Min. SDK Version:</strong> 1.5.7</li>

											<li><strong>Sample value:
												</strong><samp>"js-2.0.1.88-c8c0b1"</samp></li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e216 ">
									<div>
										<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_axm_jtw_41b">
											<li><strong>Adobe Analytics:</strong> 
												<p><samp>a.media.vhlVersion</samp></p>
</li>

											<li><strong>Heartbeats:
												</strong><p><samp>s:sp:hb_version</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_bxm_jtw_41b">
										<li><strong>Available:</strong> Use custom processing rule</li>

										<li><strong>Reserved Variable:</strong> N/A</li>

										<li><strong>Report Name:</strong> Custom </li>

										<li><strong>Context Data:
											</strong><samp>a.media.vhlVersion</samp></li>

										<li><strong>Data Feed:</strong> <samp>N/A</samp></li>

										<li><strong>Audience Manager:
												</strong><samp>c_contextdata.a.media.vhlVersion</samp></li>

									</ul>

								</td>

							</tr>

							<tr>
								<td colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p>The heartbeat SDK version used for the tracking session.
										Customers will have to create their own processing rules to
										have the value available for reporting. </p>

									<p>* <samp><a href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank">MediaHeartbeat</a>.version();</samp></p>

								</td>

							</tr>

						</tbody>

					</table>
</div>

