# Implementation Paths

## Client Side

This path requires only your player and one of these two Media Analytics solutions: the Video Analytics SDK or the Media Collection API. There are SDKs for several platforms, including iOS, Android, JS (browser), Chromecast, Roku, with more to come. The Media Collection API supports players with no VA SDK, instead making RESTful API calls directly to a VA back-end server. These solutions can be used across any video player, including customer and/or OVP players such as Brightcove, Ooyala, thePlatform, and so on. 

If Video Analytics is your intended path, see the [VA SDK Implementation]() and the [Media Collection API](). To use Video Analytics, customers must also use Adobe Analytics. 

## Adobe Launch

Adobe Launch, the follow-on product to Dynamic Tag Management, features a Video Analytics Launch Extension that facilitates implementing video tracking in your players. You can learn more about the VA Launch Extension here: [VA Launch Extension Docs](https://docs.adobelaunch.com/extension-reference/adobe-analytics-for-video-extension).

## Primetime

Adobe Primetime is an Adobe Experience Cloud solution that helps content programmers and distributors monetize video on every connected screen.

Primetime eliminates the complexity of reaching, monetizing, and activating global audiences across devices by providing a modular platform for video publishing, advertising, personalization, and analytics. Additionally, Primetime offers solutions and value around the following: 

* Support for accurately measuring Linear and VOD content types. 
* Support for measuring ad breaks with (or without) dynamic ad insertion. 
* TVSDK's seamless ad insertion model allows for analytics that directly measures the ad playback, which increases accuracy. 
* Robust set of events and metadata to ensure accuracy across QoS buffering or mobile connectivity interruptions issues and end-user interactions such as seeking, pausing, and backgrounding on mobile. 
* Integrated support for Nielsen DTVR (linear) with ID3 metadata and DCR with CMS metadata. 
