# Turn Your HTML Table into a Mess

## Because your SSG can't handle HTML tables or even MD tables with formatting in the cells.

1. Get rid of your `<table>` tags.
2. 




<table cellpadding="4" cellspacing="0" summary="" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__table_t4x_th2_k1b" class="table" frame="border" border="1" rules="all">
						
						
						
						
						<thead class="thead" align="left">
							<tr class="row">
								<th class="entry" align="center" valign="middle" width="10%" id="d8318e204">
									<p class="p">Label </p>

								</th>

								<th class="entry" align="center" valign="middle" width="30%" id="d8318e210">
									<p class="p">Implementation </p>

								</th>

								<th class="entry" align="center" valign="middle" width="30%" id="d8318e216">
									<p class="p">Network Parameters </p>

								</th>

								<th class="entry" align="center" valign="middle" width="30%" id="d8318e222">
									<p class="p">Reporting</p>

								</th>

							</tr>

						</thead>

						<tbody class="tbody">
							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Stream Type</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_dt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b"/></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.streamType</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"video" </samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_et3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.streamType</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:meta:a.media.streamType</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ft3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On VISIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content</li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.streamType</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videostreamtype</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.streamType</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p"><strong class="ph b">Release Date: 09/13/18</strong></p>

									<div class="note note"><span class="notetitle">Note:</span> Available only through the <a class="xref" href="media-collection-api.html">Media Collection API (RESTful)</a>.</div>

									<p class="p">Identifies the stream type. Valid values are "audio",
										"video", and "".</p>

									<p class="p"><strong class="ph b"><a class="xref" href="segments.html">Segments</a>:</strong></p>

									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xzh_mff_ffb">
											<li class="li">StreamType "All" - Segment all media stream data.
												<strong class="ph b">Rule:</strong> Content (ID) exists</li>

											<li class="li">StreamType "Audio" - Segment all audio stream data.
												<strong class="ph b">Rule:</strong> Content (ID) exists AND Stream Type =
												audio</li>

											<li class="li">StreamType "Video" - Segment all video stream data.
												<strong class="ph b">Rule:</strong> Content (ID) exists AND Stream Type =
												video</li>

										</ul>

									</div>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content ID</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_pjx_1ts_1fb">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">mediaId*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.id</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"4586695ABC"
												</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_qjx_1ts_1fb">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.name</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:asset:video_id</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_rjx_1ts_1fb">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On VISIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content</li>

										<li class="li"><strong class="ph b">Context Data:</strong> <samp class="ph codeph">a.media.name</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">video</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.name</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">Content ID of the content, which can be used to tie back to
										other industry / CMS IDs, equal to the last value of
											<samp class="ph codeph">s:asset:video_id</samp>. Any integer and/or
										letter combination.</p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name,
												<strong class="ph b"><em class="ph i">mediaId</em></strong>, length,
										streamType)</samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Length (variable)</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_gt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">length*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.length</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes</li>

											<li class="li"><strong class="ph b">Type:</strong> number</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any**</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ljx_yr1_41b">
												<li class="li">VOD: 128</li>

												<li class="li">Live: 86400</li>

												<li class="li">Linear: 1800</li>

												</ul>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ht3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.length</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">l:asset:length</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_it3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Length (variable)</li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.length</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videolength</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.length</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p"><strong class="ph b">Release Date: 09/13/18</strong></p>

									<p class="p">Clip Length/Runtime - This is the maximum length (or
										duration) of the content being consumed (in seconds). It
										equals the last value of <samp class="ph codeph">l:asset:length</samp>
										from events of type Main. If <samp class="ph codeph">l:asset:length</samp>
										is not set, then the last value of
											<samp class="ph codeph">l:asset:duration</samp> is used.</p>

									<p class="p">In reporting, Video Length is the classification, and Content
										Length (variable) is the eVAR.</p>

									<div class="p">
										<div class="note important"><span class="importanttitle">Important:</span> This property is used to compute
											several metrics, such as progress tracking metrics and
											Average Minute Audience. If this is not set, or not
											greater than zero, then these metrics are not
											available.</div>

									</div>

									<p class="p">For Live media with an unknown duration, the value of 86400 is the default. </p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId,
												<strong class="ph b"><em class="ph i">length</em></strong>, streamType)</samp></p>

									<p class="p"><strong class="ph b">**</strong> Pre Version 1.5.1, this was
											<samp class="ph codeph">l:asset:duration</samp>; after 1.5.1, this is
											<samp class="ph codeph">l:asset:length</samp>.</p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Video Length</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_kgk_qrk_hfb">
											<li class="li"><strong class="ph b">SDK Key:</strong>
												<samp class="ph codeph"><strong class="ph b">length*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.length</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes</li>

											<li class="li"><strong class="ph b">Type:</strong> number</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any**</li>

											<li class="li"><strong class="ph b">Sample value:</strong>
												<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_lgk_qrk_hfb">
												<li class="li">VOD: 128</li>

												<li class="li">Live: 86400</li>

												<li class="li">Linear: 1800</li>

												</ul>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_mgk_qrk_hfb">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong>
												<p class="p"><samp class="ph codeph">a.media.length</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">l:asset:length</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ngk_qrk_hfb">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> classification</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Video Length</li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.length</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong>
											<samp class="ph codeph">videoclassificationlength</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.length</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p"><strong class="ph b">Release Date: 09/27/18</strong></p>

									<p class="p">Clip Length/Runtime - This is the maximum length (or
										duration) of the content being consumed (in seconds). It
										equals the last value of <samp class="ph codeph">l:asset:length</samp>
										from events of type Main. If <samp class="ph codeph">l:asset:length</samp>
										is not set, then the last value of
											<samp class="ph codeph">l:asset:duration</samp> is used.</p>

									<p class="p">In reporting, Video Length is the classification, and Content
										Length (variable) is the eVAR.</p>

									<div class="p">
										<div class="note important"><span class="importanttitle">Important:</span> This property is used to compute
											several metrics, such as progress tracking metrics and
											Average Minute Audience. If this is not set, or not
											greater than zero, then these metrics are not
											available.</div>

									</div>

									<p class="p">For Live media with an unknown duration, the value of 86400
										is the default. </p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId,
												<strong class="ph b"><em class="ph i">length</em></strong>, streamType)</samp></p>

									<p class="p"><strong class="ph b">**</strong> Pre Version 1.5.1, this was
											<samp class="ph codeph">l:asset:duration</samp>; after 1.5.1, this is
											<samp class="ph codeph">l:asset:length</samp>.</p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Type</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_jt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">streamType*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.contentType</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes </li>

											<li class="li"><strong class="ph b">Type:</strong> restricted string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"vod"</samp>
											</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_kt3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.contentType</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:stream:type</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_lt3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Type </li>

										<li class="li"><strong class="ph b">Context Data:</strong> <samp class="ph codeph">a.contentType</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videocontenttype</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.contentType</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<div class="p">Available values per <strong class="ph b">Stream Type</strong>:<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_n2w_vxs_1fb">
											<li class="li"><strong class="ph b">Audio:</strong> "song", "podcast", "audiobook",
												"radio"</li>

											<li class="li"><strong class="ph b">Video:</strong> "VoD", "Live", "Linear", "UGC",
												"DVoD"</li>

										</ul>
Customers can provide custom values for this
										parameter.</div>

									<p class="p">This equals <samp class="ph codeph">s:stream:type</samp>. If that is unset,
										this equals <samp class="ph codeph">missing_content_type</samp>.</p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(name, mediaId, length,
												<strong class="ph b"><em class="ph i">streamType</em></strong>)</samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Video Session ID</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_mt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> Automatically set</li>

											<li class="li"><strong class="ph b">API Key:</strong> Obtained from backend</li>

											<li class="li"><strong class="ph b">Required:</strong> Yes </li>

											<li class="li"><strong class="ph b">Type:</strong> number</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5.8</li>

											<li class="li"><strong class="ph b">Sample value:
												</strong><samp class="ph codeph">1482236761294786918253</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_nt3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.vsid</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeat:</strong> <samp class="ph codeph">s:event:sid</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ot3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Use processing rule</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> N/A</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Custom </li>

										<li class="li"><strong class="ph b">Context Data:</strong> <samp class="ph codeph">a.media.vsid</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">vsid</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.vsid</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">This identifies an instance of a content stream unique to an
										individual playback. </p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Player Name</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_pt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">playerName*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.playerName</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes</li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"Brightcove"</samp>,
												<samp class="ph codeph">"Primetime"</samp>, etc. </li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_qt3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.playerName</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:sp:player_name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_rt3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Player Name </li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.playerName</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videoplayername</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.playerName</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">Name of the player. </p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong class="ph b"><em class="ph i">playerName</em></strong></samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Channel</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_st3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">channel*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.channel</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> Yes</li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"Sports"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_tt3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.channel </samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:sp:channel</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ut3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Channel </li>

										<li class="li"><strong class="ph b">Context Data:</strong> <samp class="ph codeph">a.media.channel
											</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videochannel</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.channel
											</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">Distribution Station/Channels or where the content is played.
										Any string value is accepted here.</p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong class="ph b"><em class="ph i">channel</em></strong></samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Segment</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vt3_htw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> Automatically set </li>

											<li class="li"><strong class="ph b">API Key:</strong> N/A</li>

											<li class="li"><strong class="ph b">Required:</strong> Yes </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <p class="p"><samp class="ph codeph">"[0-10]"</samp>
												(minutes) </p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wt3_htw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> N/A </li>

											<li class="li"><strong class="ph b">Heartbeats:</strong> N/A</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xt3_htw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar</li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Segment </li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.segment</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videosegment</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.segment</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">The interval that describes the part of the content that has
										been viewed (in minutes). The segment is computed as min and
										max of the playhead values during a playback session. </p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Content Name (variable)</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_fd2_5bm_n1b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">name*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.name</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> No </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5.1</li>

											<li class="li"><strong class="ph b">Sample value:</strong> <samp class="ph codeph">"The Big Bang
												Theory"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_epx_th2_k1b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.friendlyName</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:asset:name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_fpx_th2_k1b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> eVar </li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Content Name (variable)</li>

										<li class="li"><strong class="ph b">Context Data:
												</strong><samp class="ph codeph">a.media.friendlyName</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videoname</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.friendlyName</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p"><strong class="ph b">Release Date: 09/13/18</strong></p>

									<p class="p">In reporting, Video Name is the classification, and Content
										Name (variable) is the eVAR.</p>

									<p class="p">This is the "friendly" (human-readable) name of the content,
										equal to the last value of
										<samp class="ph codeph">s:asset:name</samp>.</p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(<strong class="ph b"><em class="ph i">name</em></strong>,
											mediaId, length, streamType)</samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Video Name</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vqq_frk_hfb">
											<li class="li"><strong class="ph b">SDK Key:</strong>
												<samp class="ph codeph"><strong class="ph b">name*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.name</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> No </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate, Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5.1</li>

											<li class="li"><strong class="ph b">Sample value:</strong>
												<samp class="ph codeph">"The Big Bang Theory"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wqq_frk_hfb">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong>
												<p class="p"><samp class="ph codeph">a.media.friendlyName</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:asset:name</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xqq_frk_hfb">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> classification </li>

										<li class="li"><strong class="ph b">Expiration:</strong> On HIT</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Video Name</li>

										<li class="li"><strong class="ph b">Context Data:
												</strong><samp class="ph codeph">a.media.friendlyName</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong>
											<samp class="ph codeph">videoclassificationname</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.friendlyName</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p"><strong class="ph b">Release Date: 09/27/18</strong></p>

									<p class="p">This is the "friendly" (human-readable) name of the content,
										equal to the last value of
										<samp class="ph codeph">s:asset:name</samp>.</p>

									<p class="p">In reporting, Video Name is the classification, and Content
										Name (variable) is the eVAR.</p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html#-static-createMediaObject" target="_blank">createMediaObject</a>(<strong class="ph b"><em class="ph i">name</em></strong>,
											mediaId, length, streamType)</samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">Video Path</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_twm_jtw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> Automatically set </li>

											<li class="li"><strong class="ph b">API Key:</strong> N/A</li>

											<li class="li"><strong class="ph b">Required:</strong> No </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Initiate</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> Any</li>

											<li class="li"><strong class="ph b">Sample value:
												</strong><samp class="ph codeph">"4586695ABC"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_uwm_jtw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.name</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:asset:video_id</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_vwm_jtw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Yes</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> prop</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Video Path </li>

										<li class="li"><strong class="ph b">Context Data:</strong> <samp class="ph codeph">a.media.name</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">videopath</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.name</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">Ability to track path of viewer across site and/or App to see
										path they took to view a particular video. Any integer
										and/or letter combination.</p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">SDK Version</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_wwm_jtw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> <samp class="ph codeph"><strong class="ph b">appVersion*</strong></samp>
											</li>

											<li class="li"><strong class="ph b">API Key:
												</strong><samp class="ph codeph"><strong class="ph b">media.sdkVersion</strong></samp></li>

											<li class="li"><strong class="ph b">Required:</strong> No </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5.7</li>

											<li class="li"><strong class="ph b">Sample value:
												</strong><samp class="ph codeph">"2.62.0_release"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_xwm_jtw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.sdkVersion</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:sp:sdk</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_ywm_jtw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Use custom processing rule</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> N/A</li>

										<li class="li"><strong class="ph b">Report Name:</strong> <em class="ph i"/>
										</li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.sdkVersion</samp>`</li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">N/A</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.sdkVersion</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">The SDK version used by the player. This could have any
										custom value that makes sense for your player. Customers
										will have to create their own processing rules to have the
										value available for reporting. </p>

									<p class="p"><strong class="ph b">*</strong>
										<samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeatConfig.html#toc0" target="_blank">MediaHeartbeatConfig</a>.<strong class="ph b"><em class="ph i">appVersion</em></strong></samp></p>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" rowspan="2" align="left" valign="top" width="10%" headers="d8318e204 ">
									<p class="p"><strong class="ph b">VHL Version</strong>
									</p>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e210 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_zwm_jtw_41b">
											<li class="li"><strong class="ph b">SDK Key:</strong> Automatically set* </li>

											<li class="li"><strong class="ph b">API Key:</strong> N/A</li>

											<li class="li"><strong class="ph b">Required:</strong> No </li>

											<li class="li"><strong class="ph b">Type:</strong> string</li>

											<li class="li"><strong class="ph b">Sent with:</strong> Close</li>

											<li class="li"><strong class="ph b">Min. SDK Version:</strong> 1.5.7</li>

											<li class="li"><strong class="ph b">Sample value:
												</strong><samp class="ph codeph">"js-2.0.1.88-c8c0b1"</samp></li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e216 ">
									<div class="p">
										<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_axm_jtw_41b">
											<li class="li"><strong class="ph b">Adobe Analytics:</strong> 
												<p class="p"><samp class="ph codeph">a.media.vhlVersion</samp></p>
</li>

											<li class="li"><strong class="ph b">Heartbeats:
												</strong><p class="p"><samp class="ph codeph">s:sp:hb_version</samp></p>
</li>

										</ul>

									</div>

								</td>

								<td class="entry" align="left" valign="top" width="30%" headers="d8318e222 ">
									<ul class="ul" id="reference_0470E81636C8483DB2C79A1E0C51B5D0__ul_bxm_jtw_41b">
										<li class="li"><strong class="ph b">Available:</strong> Use custom processing rule</li>

										<li class="li"><strong class="ph b">Reserved Variable:</strong> N/A</li>

										<li class="li"><strong class="ph b">Report Name:</strong> Custom </li>

										<li class="li"><strong class="ph b">Context Data:
											</strong><samp class="ph codeph">a.media.vhlVersion</samp></li>

										<li class="li"><strong class="ph b">Data Feed:</strong> <samp class="ph codeph">N/A</samp></li>

										<li class="li"><strong class="ph b">Audience Manager:
												</strong><samp class="ph codeph">c_contextdata.a.media.vhlVersion</samp></li>

									</ul>

								</td>

							</tr>

							<tr class="row">
								<td class="entry" colspan="3" align="left" valign="top" headers="d8318e210 d8318e216 d8318e222 ">
									<p class="p">The heartbeat SDK version used for the tracking session.
										Customers will have to create their own processing rules to
										have the value available for reporting. </p>

									<p class="p">* <samp class="ph codeph"><a class="xref" href="https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html" target="_blank">MediaHeartbeat</a>.version();</samp></p>

								</td>

							</tr>

						</tbody>

					</table>
