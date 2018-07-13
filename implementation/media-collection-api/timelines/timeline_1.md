[](javascript:window.print();)

[Media Collection API Implementation](c_vhl_col-api_overview.html)[Video
Tracking Timelines](c_vhl_col-api-timelines.html)

[Parent topic: Video Tracking Timelines](c_vhl_col-api-timelines.html)

# Timeline 1 - View to end of content

![](graphics/va_api_content.png)

![](graphics/va_api_actions.png)

Table 1. VOD, pre-roll ads, pausing, buffering, viewing content to the end

Action # Action Action Timeline (Seconds) Playhead position (Seconds) Client
Request Implementation Details

1

Auto-play or Play button pressed, video starts loading.

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
        ts: <timestamp>
      },
      eventType:adBreakStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.podIndex": 0,
        "media.ad.podSecond": 0
      }
    }

Ads can only be tracked within an ad break.

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
      params: {
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.name": "Ad 1",
        "media.ad.id": "001",
        "media.ad.length": 15, 
        "media.ad.podPosition": 1,
        "media.ad.playerName": "Sample Player",
        "media.ad.advertiser": "Ad Guys",
        "media.ad.campaignId": "1",
        "media.ad.creativeId": "42",
        "media.ad.siteId": "XYZ",
        "media.ad.creativeURL": "http://xyz_creative.com",
        "media.ad.placementId": "sample_placement"
      },
      customMetadata:{
        "myCustomData1": "CustomData1",
        "myCustomData2": "CustomData2"
      }
    }

Start tracking the first pre-roll ad, which is 15 seconds long. Including
custom metadata with this adStart.

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

15

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adComplete
    }

Track the end of the first pre-roll ad.

7

Track pre-roll Ad #2 start

15

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod1",
        "media.ad.name": "Ad 2",
        "media.ad.id": "002",
        "media.ad.length": 7, 
        "media.ad.podPosition": 1,
        "media.ad.playerName": "Sample Player",
        "media.ad.advertiser": "Ad Guys",
        "media.ad.campaignId": "2",
        "media.ad.creativeId": "44",
        "media.ad.siteId": "XYZ",
        "media.ad.creativeURL": "http://xyz_creative.com",
        "media.ad.placementId": "sample_placement2"
      },
    }

Track the start of the second pre-roll ad, which is 7 seconds long.

8

App sends ping event

20

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

9

Track pre-roll Ad #2 complete

22

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:adComplete
    }

Track the end of the second pre-roll ad.

10

Track pre-roll ad break complete

22

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0, 
        ts: <timestamp>
      },
      eventType:adBreakComplete
    }

The ad break is over. Throughout the ad break, the play state has remained
"playing".

11

Track play event

22

0

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 0,
        ts: <timestamp>
      },
      eventType:play
    }

After the adBreakComplete event, put the player is in the "playing" state
using the play event.

12

App sends ping event

30

8

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 8,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

13

Buffer start event occurred

33

11

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 11,
        ts: <timestamp>
      },
      eventType:bufferStart
    }

Track the player's move to the "buffering" state.

14

Buffering ended, the app tracks resumption of content

36

11

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 11,
        ts: <timestamp>
      },
      eventType:play
    }

Buffering ends after 3 seconds, so put the player back to the "playing" state.
You must send another track play event coming out of buffering.

**The play call after a bufferStart infers a "bufferEnd" call to the back end**, so there is no need for a bufferEnd event.

15

App sends ping event

40

15

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 15,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

16

Track mid-roll ad break start

46

21

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 21,
        ts: <timestamp>
      },
      eventType:adBreakStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod2",
        "media.ad.podIndex": 1,
        "media.ad.podSecond": 21
      }
    }

Mid-roll ad of 8 seconds duration: send adBreakStart.

17

Track mid-roll Ad #3 start

46

21

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{ 
        playhead: 21,
        ts: <timestamp>
      },
      eventType:adStart,
      params: {
        "media.ad.podFriendlyName": "ad_pod2",
        "media.ad.name": "Ad 3",
        "media.ad.id": "003",
        "media.ad.length": 8, 
        "media.ad.podPosition": 2,
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

18

App sends ping event

50

21

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 21,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

19

Track mid-roll Ad #1 complete

54

21

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 21,
        ts: <timestamp>
      },
      eventType:adComplete
    }

The mid-roll ad is complete.

20

Track mid-roll ad break complete

54

21

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 21,
        ts: <timestamp>
      },
      eventType:adBreakComplete
    }

The ad break is complete.

21

App sends ping event

60

27

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 27,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

22

User pressed Pause

64

31

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 31,
        ts: <timestamp>
      },
      eventType:pauseStart
    }

The user's action moves the play state to "paused".

23

App sends ping event

70

31

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 31,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds. Player is still in the "buffering" state;
the user is stuck at 20 seconds of content. Fuming...

24

User pressed Play to resume main content

74

31

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 31,
        ts: <timestamp>
      },
      eventType:play
    }

Move the play state to "playing".

**The play call after a pauseStart infers a "resume" call to the back end**, so there is no need for a resume event.

25

App sends ping event

80

37

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 37,
        ts: <timestamp>
      },
      eventType:ping
    }

Ping the backend every 10 seconds.

26

The user finishes watching the content to the end.

88

45

/api/v1/sessions/{sid}/events

    
    {
      playerTime:{
        playhead: 45,
        ts: <timestamp>
      },
      eventType:sessionComplete
    }

Send sessionComplete to the backend to indicate that the user finished
watching the entire content.

Note: **No Seek Events?** - There is no explicit support in the Media
Collection API for seekStart or seekComplete events. This is because certain
players generate a very large number of such events when the end-user is
scrubbing, and several hundred users could easily bottleneck the network
bandwidth of a backend service. Adobe works around explicit support for seek
events by computing heartbeat duration based on device timestamp, rather than
playhead position.

[Parent topic: Video Tracking Timelines](c_vhl_col-api-timelines.html)

WebHelp output generated by[ <oXygen/> XML Author ](http://www.oxygenxml.com)

