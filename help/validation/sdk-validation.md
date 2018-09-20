---
description: null
seo-description: null
seo-title: SDK Validation
title: SDK Validation
uuid: 4a585726-09ce-45a0-88c8-4d85482e1a61
index: y
internal: n
snippet: y
translate: y
---

# SDK Validation

To validate your Media Heartbeat implementation you will need to use an HTTP Proxy tool to view the HTTP / HTTPS traffic between the Application and Heartbeats/Adobe Analytics. 

HTTP calls for video analytics tracking are sent to 2 different tracking servers: 


* **Adobe Analytics: **Adobe Analytics hits are used to mark the initiate of a Video/Ad/Chapter. Tracking server example: [!DNL  <visitornamespace>.sc.omtrdc.net].
* **Heartbeats platform: **Heartbeat platform hits (*heartbeats*) are sent throughout the video tracking session at 10 seconds intervals (out of band events might be sent outside of the 10 seconds cycle). Tracking server example: ` <visitornamespace>.hb.omtrdc.net`


All of the different parameters sent to the Adobe Analytics and Heartbeats tracking servers are presented here: [ Metrics and Metadata ](https://marketing-stage.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_metrics-and-metadata.html).

## Adobe Debug {#section_jwt_2l1_jbb}

Optionally, you can debug payloads (Heartbeat and Adobe Analytics) going out of Video Heartbeat Library using the Adobe Debug tool, which is a freely available tool from Adobe for Video Heartbeat customers. 

To use Adobe Debug, you need to contact your Adobe representative for the initial setup and registration. After you gain access to Adobe Debug, go to [ Adobe Debug help ](https://debug.adobe.com/login?next=/#/help/) to see the help information. 
