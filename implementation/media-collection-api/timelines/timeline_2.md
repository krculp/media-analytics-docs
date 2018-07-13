[](javascript:window.print();)

[Media Collection API Implementation](c_vhl_col-api_overview.html)[Video
Tracking Timelines](c_vhl_col-api-timelines.html)

[Parent topic: Video Tracking Timelines](c_vhl_col-api-timelines.html)

# Timeline 2 - User abandons session

![](graphics/va_api_content_2.png)

![](graphics/va_api_actions_2.png)

Table 1. VOD, Pre-roll ad, mid-roll ads, user abandons content early

Action # Action Action Timeline (Seconds) Playhead Position (Seconds) Client
Request Implementation Details

1

Auto-play or Play button pressed

0

0

/api/v1/sessions

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:sessionStart,
      params:{
        "media.playerName": "sample-html5-api-player",
        "analytics.trackingServer": "[_YOUR_TS_]",
        "analytics.reportSuite": "[_YOUR_RSID_]",
        "analytics.visitorId": "[_YOUR_VISITOR_ID_]",
        "media.contentType": "VOD",
        "media.length": 60.3333333333333,
        "media.id": "VA API Sample Player",
        "visitor.marketingCloudOrgId": "[YOUR_MCID]",
        "media.name": "ClickMe",
        "media.channel": "sample-channel",
        "media.sdkVersion": "va-api-0.0.0",
        "analytics.enableSSL": false
      }
    }

This call signals _the user's intention to play_ a video. It returns a Session
ID ({sid}) to the client that is used to identify all subsequent tracking
calls within the session. The player state is not yet "playing", but is
instead "starting". [Mandatory session parameters](c_vhl_col-
api_reference.html#concept_tqz_tqp_qbb__section_tps_bqm_kcb) must be included
in the params map in the request body.

On the backend, this call generates an Adobe Analytics initiate call.

2

App starts ping event timer

0

0

Start your app's 10-second ping timer. First ping event should then fire 10
seconds into the session.

3

Track pre-roll ad break start

0

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>},
      eventType:adBreakStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.podIndex": 0,
        "media.ad.podSecond": 0
      }
    }

Pre-roll ads must be tracked. Ads can only be tracked within an ad break.

4

Track pre-roll Ad #1 start

0

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adStart,
      params:{
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.name": "Ad 1",
        "media.ad.id": "002",
        "media.ad.length": 7, 
        "media.ad.podPosition": 1,
        "media.ad.playerName": "Sample Player",
        "media.ad.advertiser": "Ad Guys",
        "media.ad.campaignId": "1",
        "media.ad.creativeId": "42",
        "media.ad.siteId": "XYZ",
        "media.ad.creativeURL": "http://xyz_creative.com",
        "media.ad.placementId": "sample_placement2"
      },
    }

A 12 second ad starts.

5

App sends ping event

10

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

6

Track pre-roll Ad #1 complete

12

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adComplete
    }

The first pre-roll ad is over.

7

Track pre-roll ad break complete

12

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adBreakComplete
    }

The ad break is over. Throughout the ad break, the player has remained in the
"playing" state.

8

Track play event

12

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:play,
      qoeData: {
        bitrate: 10000
      }
    }

Move the player to the "playing" state; begin tracking the start of content
playback.

9

App sends ping event

20

8

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 8ß,
        ts: <timestamp>
      },
      eventType:ping
    } 

Ping the backend every 10 seconds.

10

App sends ping event

30

18

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 18,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

11

Error occurs, app sends error information.

32

20

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 20,
        ts: <timestamp>
      },
      eventType:error,
      qoeData:{
        "media.qoe.errorID": "<errorID>",
        "media.qoe.media.errorSource": "player"
      } 
    }

For error events, qoeData parameters errorID and errorSource are required.

12

App recovers from error, user presses Play

37

20

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 18,
        ts: <timestamp>
      },
      eventType:play,
      qoeData: {
        bitrate: 10000
      }
    }


13

App sends ping event

40

28

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 28,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

14

Track mid-roll ad break start

45

33

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 33,
        ts: <timestamp>
      },
      eventType:adBreakStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod2",
        "media.ad.podIndex": 1,
        "media.ad.podSecond": 33
      }
    }

Mid-roll ad of 8 seconds duration: send adBreakStart.

15

Track mid-roll Ad #1 start

45

33

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 33,
        ts: <timestamp>
      },
      eventType:adStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.name": "Ad 1",
        "media.ad.id": "002",
        "media.ad.length": 8, 
        "media.ad.podPosition": 1,
        "media.ad.playerName": "Sample Player",
        "media.ad.advertiser": "Ad Guys",
        "media.ad.campaignId": "7",
        "media.ad.creativeId": "40",
        "media.ad.siteId": "XYZ",
        "media.ad.creativeURL": "http://xyz_creative.com",
        "media.ad.placementId": "sample_placement2"
      },
    }

Track the mid-roll ad.

16

User closes the app. The app determines that the user has abandoned viewing
and isn't returning to this session.

48

33

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 33,
        ts: <timestamp>
      },
      eventType:sessionEnd
    }

Send sessionEnd to the VA backend to indicate that the session should be
closed immediately, with no further processing.

[Parent topic: Video Tracking Timelines](c_vhl_col-api-timelines.html)

WebHelp output generated by[ <oXygen/> XML Author ](http://www.oxygenxml.com)

