# Measuring Video in Adobe Analytics

**Last Updated: July 20, 2017**

**Important:** The video documentation provided here is specific to clients
utilizing version 1.5 or higher of Adobe's video SDK for heartbeat
measurement, and does not include instructions around the legacy milestone
video implementation. We encourage all customers to move towards adopting the
latest video SDK to capitalize on the improvements and expanded measurement,
you can view the [benefits of transitioning to the SDK](video_overview.html#co
ncept_ADA4B5C612D24280955BD0B7E79B4271__section_cnj_5st_p1b) below. While we
will continue to support the milestone method of tracking videos, there will
not be any planned updates, fixes or feature improvements. Please reach out to
your Adobe Account Manager if you have any further questions.

## Overview

Adobe Analytics for Video is an add-on to the base Analytics offering that
provides clients with robust video measurement for content, audio and
advertisements. Video Analytics provides many benefits to customers to allow
for real-time monitoring, detailed analysis, actionable insights and
monetization opportunities. Video tracking is enabled through SDK integrations
with the most commonly used video players. The latest SDKs have the additional
capability of capturing audio related metrics.

Adobe Analytics for Video enables clients to track the full customer journey
across their site, which includes video consumption, and these measures are
easily integrated into Analytics reporting and other Experience Cloud
products. Video measurement allows you to slice and dice your data into
multiple dimensions and segments, capturing all of the metadata you need to do
a full detailed analysis, and to attribute success criteria to fully viewed
videos, average time spent and completed ads.

The video solution not only measures vital video delivery metrics related to
QoS, such as dropped frames, time spent buffering, and average bitrate, but it
can also be combined with your website or app data to visualize the flow of
the customer and their interests to better be able to make recommendations and
personalize their experiences through the Adobe Experience Cloud.

## Benefits

Some of the many benefits that Adobe's video solution provides include:

  * **Timely analysis** - Make real-time, actionable decisions utilizing key video performance metrics (e.g., duration) across multiple channels. Video events are measured in **10-second** intervals to capture all activity as it occurs. 
  * **Drive engagement** - Fully engage users through fewer buffering events and by understanding where and when ads should display within video content to provide a smooth, less intrusive viewing experience that brings users back and delivers repeat visits. 
  * **Holistic picture** - Combine multiple data points across all of your content distributors to get a full view of all your video activity, and measure engagement and views across all possible channels through [Federated Analytics](federated-analytics.html). 
  * **Increased granularity** - Evaluate viewing behavior at the most granular level, including individual visitor time of day, concurrent viewers by minute, and average duration the content was viewed. 
  * **Precise measurement** - Measure across the multiple devices used for video consumption, including OTT, smartphone, tablet, desktop, and more, to monitor user engagement patterns and habits. 
  * **Segmentation** - Apply classifications to your players, devices, genres, chapters, and shows to see how each has an impact on your overall views and customer engagement with content, audio, ads, and combined. 

## Heartbeat versus Milestone Benefits

Adobe Analytics for Video is able to be measured through two means: the legacy
Milestone method and the current Heartbeats method. The Heartbeats method is
the preferred method of measurement and we encourage all clients to move to
this version if they haven’t already, to take advantage of the benefits
described below.

The legacy Milestone method is based on individual server calls to the
Analytics server, for video starts, quartiles, duration, and completes. The
Heartbeats method provides a more robust video tracking solution that measures
video in 10 second intervals to provide enhanced, standardized video metrics.
In addition, Adobe has derived learnings from our Milestone method to provide
a smoother, streamlined implementation process through the video SDK utilized
by heartbeats.

Some of the many benefits of the Heartbeats method include:

  * **Streamlined implementation process** - Map variables more easily through your player API and validate implementations through the Adobe Debug Tool to ensure all the necessary variables are tracked accurately. 
  * **Automatic Adobe Experience Cloud Integration** - Take advantage of the automatic integration with the Adobe Experience Cloud through the Marketing Cloud ID, segment your video audiences, target them, and make video recommendations based on user preferences. 
  * **Shared video data through Federated Analytics** - Capitalize on our industry-first video sharing capabilities, to evaluate data holistically across all of your video distribution partners—operators, programmers, and distributors. 
  * **Partnerships with Certified Ratings Partners** - Adobe partners with audience ratings partner Nielsen to provide neutral census third party measurement to allow for trusted, certified video ratings. 
  * **Standardized solution across all platforms** - Enable consistent, standardized variables across all of your videos and platforms to allow for a more efficient cross-campaign, device and vendor comparison. 

<table cellpadding="4" cellspacing="0" summary="" frame="border" border="1" rules="all"><caption>Table 1. Comparison Chart</caption> 
    <thead align="left">	
        <tr> 
        <th valign="top" > </th>
        <th valign="top"><strong>Video Analytics- Milestone</strong> </th>
        <th valign="top" ><strong>Video Analytics- Heartbeats</strong> </th>
        </tr>
    </thead>

    <tbody> 
        <tr> 
            <td valign="top" ><strong>Video Events</strong> </td>
            <td valign="top" >High-level Standard Events </td>
            <td valign="top" >Detailed and Custom Events every 10s </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Metrics and Dimensions</strong> </td>
            <td valign="top" >Variances among Vendors, Non-Standardized Metrics and Dimensions </td>
            <td valign="top" >Clear, Standardized Metrics, Dimensions, and Benchmarks across Vendors </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Integrations w/ Adobe Products</strong> </td>
            <td valign="top" >Individual Sessions w/ some Mappings and Integrations </td>
            <td valign="top" >Stitched Marketing Cloud ID linked to full Adobe Experience Cloud for easier cross-analysis </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Pricing</strong> </td>
            <td valign="top" >Tracked and billed against each server call </td>
            <td valign="top" >Transparent tracking by video stream (single) </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Implementation and Support</strong> </td>
            <td valign="top" >Longer integrations with limited support on legacy versions &amp; no upgrades </td>
            <td valign="top" >Streamlined configuration with ongoing updates and improvements </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Partner Sharing</strong> </td>
            <td valign="top" >N/A </td>
            <td valign="top" >Federated Analytics and Certified Metrics </td>
        </tr>
        <tr> 
            <td valign="top" ><strong>Advanced Tracking</strong> </td>
            <td valign="top" >N/A </td>
            <td valign="top" >Error Recovery Tracking and Concurrent Viewers </td>
        </tr>
    </tbody>
</table>

## Devices Supported

Adobe Analytics for Video has evolved with the industry to provide strong data
collection tools to ensure each video stream is collected and reported across
all meaningful devices. Our SDK is developed for all of the most utilized
devices, including:

  * iOS and Android smartphones and tablets 
  * OTT devices for ROKU, AppleTV, FireTV, and Android TV 
  * JavaScript Browser for Desktop and Laptop 

The SDK’s are routinely updated when new versions of devices are released, and
you can use these SDKs to integrate with most of the largest video players
today, including Brightcove and Ooyala.

The table below provides a list of the devices that are currently supported
through our SDK implementation or Analytics API. To download the most recent
version of the SDK, visit [Download the Video Heartbeat Library SDKs
](c_vhl_download-sdks.html). If there is a device that is not listed which you
are seeking measurement against, please contact customer care or your solution
consultant for the status of that device.

<table cellpadding="4" cellspacing="0" summary=""> 
    <tbody> 
        <tr> 
            <td align="left" valign="top" > </td>
            <td align="center" valign="top" ><strong>Adobe Video SDK</strong> </td>
            <td align="center" valign="top" ><strong>Video Analytics Collection API</strong> </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>JavaScript Browser</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>iOS Devices</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Android Devices</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Windows </strong> </td>
            <td align="center" valign="top" > </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Blackberry</strong> </td>
            <td align="center" valign="top" > </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Apple TV (new/legacy)</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>ROKU</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>OSX</strong> </td>
            <td align="center" valign="top" > </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Fire TV</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Android TV</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Chromecast</strong> </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
            <td align="center" valign="top" > </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Xbox 1</strong> </td>
            <td align="center" valign="top" > </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
        </tr>
        <tr> 
            <td align="left" valign="top" ><strong>Sony PS3/PS4</strong> </td>
            <td align="center" valign="top" > </td>
            <td align="center" valign="top" ><strong>✔</strong> </td>
        </tr>
    </tbody>
</table>
