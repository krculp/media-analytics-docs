---
description: In this scenario, VOD content is played back with a pre-roll ad, the content, a mid-roll ad, the content, and a post-roll ad.
seo-description: In this scenario, VOD content is played back with a pre-roll ad, the content, a mid-roll ad, the content, and a post-roll ad.
seo-title: Playback with ad breaks
title: Playback with ad breaks
uuid: 8d9a289c-0b0d-451c-9e78-9b260c45601c
index: y
internal: n
snippet: y
translate: y
---

# Playback with ad breaks


><a id="fig_50DBB9988C2E42268B1ABFA2467E78FB"></a> ![](assets/ad-content-regular-playback.png) 

>
>* **Android - **To view this scenario in Android, set up the following code: 

>
>  ```
>  java>  // Set up mediaObject 
>  MediaObject mediaInfo = MediaHeartbeat.createMediaObject( 
>      Configuration.VIDEO_NAME,  
>      Configuration.VIDEO_ID,  
>      Configuration.VIDEO_LENGTH,  
>      MediaHeartbeat.StreamType.VOD 
>  ); 
>   
>  HashMap<String, String> videoMetadata = new HashMap<String, String>(); 
>  videoMetadata.put(CUSTOM_KEY_1, CUSTOM_VAL_1); 
>  videoMetadata.put(CUSTOM_KEY_2, CUSTOM_VAL_2); 
>   
>  // 1. Call trackSessionStart() when the user clicks Play or if autoplay is used,  
>  //   i.e., there's an intent to start playback. 
>  _mediaHeartbeat.trackSessionStart(mediaInfo, videoMetadata); 
>   
>  ...... 
>  ...... 
>   
>  // Pre-roll 
>  MediaObject adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(ADBREAK_NAME,  
>                                       ADBREAK_POSITION,  
>                                       ADBREAK_START_TIME); 
>  MediaObject adInfo = MediaHeartbeat.createAdObject(AD_NAME,  
>                                                     AD_ID,  
>                                                     AD_POSITION,  
>                                                     AD_LENGTH); 
>   
>  // Context ad data 
>  HashMap<String, String> adMetadata = new HashMap<String, String>(); 
>  adMetadata.put(CUSTOM_KEY_1, CUSTOM_VAL_1); 
>  adMetadata.put(CUSTOM_KEY_2, CUSTOM_VAL_2); 
>   
>  // 2. Track the MediaHeartbeat.Event.AdBreakStart event when the pre-roll pod  
>  //    starts to play. Note that since this is a pre-roll, you must track the  
>  //    "MediaHeartbeat.Event.AdBreakStart" event before you call trackPlay().  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo, null); 
>   
>  ....... 
>  ....... 
>   
>  // 3. Track the MediaHeartbeat.Event.AdStart event when the pre-roll pod's ad  
>  //    starts to play. Note that since this is a pre-roll, you must track the  
>  //    "MediaHeartbeat.Event.AdStart" event before you call trackPlay().  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 4. Call trackPlay() when the playback actually starts, i.e., when the first  
>  //    frame of the main content is rendered on the screen.  
>  _mediaHeartbeat.trackPlay(); 
>   
>  ....... 
>  ....... 
>   
>  // 5. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches the end,  
>  //    i.e., when the ad completes and finishes playing.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // 6. Track the MediaHeartbeat.Event.AdBreakComplete event when all of the ads in  
>  //;    the pod finish playing. 
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // Mid-roll 
>  MediaObject adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(mid-roll_BREAK_NAME,  
>                                       mid-roll_BREAK_POSITION,  
>                                       mid-roll_BREAK_START_TIME); 
>  MediaObject adInfo =  
>    MediaHeartbeat.createAdObject(mid-roll_AD_NAME,  
>                                  mid-roll_AD_ID,  
>                                  mid-roll_AD_POSITION,  
>                                  mid-roll_AD_LENGTH); 
>   
>  // Context ad data 
>  HashMap<String, String> adMetadata = new HashMap<String, String>(); 
>  adMetadata.put(CUSTOM_KEY_1, CUSTOM_VAL_1); 
>  adMetadata.put(CUSTOM_KEY_2, CUSTOM_VAL_2); 
>   
>  // 7. Track the MediaHeartbeat.Event.AdBreakStart event when the mid-roll pod  
>  //    starts to play.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo, null); 
>   
>  ....... 
>  ....... 
>   
>  // 8. Track the MediaHeartbeat.Event.AdStart event when the mid-roll pod's ad  
>  //    starts to play.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 9. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches the end,  
>  //    i.e., when the adcompletes and finishes playing.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // 10. Track the MediaHeartbeat.Event.AdBreakComplete event when all the ads in the  
>  //      mid-roll pod finish playing.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // Post-roll 
>  MediaObject adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(POSTROLL_BREAK_NAME,  
>                                       POSTROLL_BREAK_POSITION,  
>                                       POSTROLL_BREAK_START_TIME); 
>  MediaObject adInfo =  
>    MediaHeartbeat.createAdObject(POSTROLL_AD_NAME,  
>                                  POSTROLL_AD_ID,  
>                                  POSTROLL_AD_POSITION,  
>                                  POSTROLL_AD_LENGTH); 
>   
>  // Context ad data 
>  HashMap<String, String> adMetadata = new HashMap<String, String>(); 
>  adMetadata.put(CUSTOM_KEY_1, CUSTOM_VAL_1); 
>  adMetadata.put(CUSTOM_KEY_2, CUSTOM_VAL_2); 
>   
>  // 11. Track the MediaHeartbeat.Event.AdBreakStart event when the post-roll pod  
>  //     starts to play.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo, null); 
>   
>  ....... 
>  ....... 
>   
>  // 12. Track the MediaHeartbeat.Event.AdStart event when the post-roll pod's  
>  //     ad starts to play.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 13. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches the  
>  //     end, i.e., when the ad completes and finishes playing. 
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // 14. Track the MediaHeartbeat.Event.AdBreakComplete event when all the ads in  
>  //     the post-roll pod finish playing.  
>  _mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // 15. Call trackComplete() when the playback reaches the end, i.e., when the 
>  //     video completes and finishes playing. 
>  _mediaHeartbeat.trackComplete(); 
>   
>  ........ 
>  ........ 
>   
>  // 16. Call trackSessionEnd() when the playback session is over. This method  
>  //     must be called even if the user does not watch the video to completion.  
>  _mediaHeartbeat.trackSessionEnd(); 
>   
>  ........ 
>  ........ 
>  
>  ```


>* **iOS - **To view this scenario in iOS, set up the following code: >
>  ```
>  //  Set up mediaObject 
>  ADBMediaObject *mediaObject =  
>    [ADBMediaHeartbeat createMediaObjectWithName:VIDEO_NAME  
>                       length:VIDEO_LENGTH  
>                       streamType:ADBMediaHeartbeatStreamTypeVOD]; 
>     
>  NSMutableDictionary *videoContextData =  
>    [[NSMutableDictionary alloc] init]; 
>  [videoContextData setObject:CUSTOM_VAL_1 forKey:CUSTOM_KEY_1]; 
>  [videoContextData setObject:CUSTOM_VAL_2 forKey:CUSTOM_KEY_2]; 
>    
>  // 1. Call trackSessionStart when the user clicks Play or if autoplay is used,  
>  //    i.e., there is an intent to start playback. 
>  [_mediaHeartbeat trackSessionStart:mediaObject data:videoContextData]; 
>  ....... 
>  ....... 
>    
>  // Pre-roll 
>  ADBMediaObject *adBreakInfo =  
>    [ADBMediaHeartbeat createAdBreakObjectWithName:AD_BREAK_NAME  
>                       position:AD_BREAK_POSITION  
>                       startTime:AD_BREAK_START_TIME]; 
>  ADBMediaObject *adInfo =  
>    [ADBMediaHeartbeat createAdObjectWithName:AD_NAME  
>                       adId:AD_ID  
>                       position:AD_POSITION  
>                       length:AD_LENGTH]; 
>    
>  // Context ad data 
>  NSMutableDictionary *adDictionary =  
>    [[NSMutableDictionary alloc] init]; 
>  [adDictionary setObject:@"custom-val1" forKey:@"custom-key1"]; 
>  [adDictionary setObject:@"custom-val2" forKey:@"custom-key2"]; 
>    
>  // 2. Track the ADBMediaHeartbeatEventAdBreakStart event when the  
>  //    pre-roll pod starts to play. Note that since this is a pre-roll,  
>  //    you must track the ADBMediaHeartbeatEventAdBreakStart event  
>  //    before you call trackPlay. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakStart  
>                   mediaObject:adBreakObject  
>                   data:adDictionary]; 
>  ....... 
>  ....... 
>    
>  // 3. Track the ADBMediaHeartbeatEventAdStart when the pre-roll  
>  //    pod's ad starts to play. Note that since this is a pre-roll,  
>  //    you must track the ADBMediaHeartbeatEventAdStart before you 
>  //    call trackPlay. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdStart  
>                    mediaObject:adObject  
>                    data:adDictionary]; 
>  ....... 
>  ....... 
>    
>  // 4. Call trackPlay when the playback actually starts, i.e., when 
>  //    the first frame of the main content is rendered on the screen. 
>  [_mediaHeartbeat trackPlay]; 
>  ....... 
>  ....... 
>    
>  // 5. Track the ADBMediaHeartbeatEventAdComplete event when the ad  
>  //    reaches the end, i.e., when it completes and finishes playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdComplete  
>                    mediaObject:nil  
>                    data:nil]; 
>  ....... 
>  ....... 
>    
>  // 6. Track the ADBMediaHeartbeatEventAdBreakComplete event when all  
>  //    of the ads in the pod finish playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakComplete  
>                    mediaObject:nil  
>                    data:nil]; 
>  ....... 
>  ....... 
>    
>  // Mid-roll 
>  ADBMediaObject *adBreakInfo =  
>    [ADBMediaHeartbeat createAdBreakObjectWithName:MIDROLL_BREAK_NAME  
>                       position:MIDROLL_BREAK_POSITION  
>                       startTime:MIDROLL_BREAK_START_TIME]; 
>  ADBMediaObject *adInfo =  
>    [ADBMediaHeartbeat createAdObjectWithName:MIDROLL_AD_NAME  
>                       adId:MIDROLL_AD_ID position:MIDROLL_AD_POSITION  
>                       length:MIDROLL_AD_LENGTH]; 
>    
>  // context ad data 
>  NSMutableDictionary *midrollAdDictionary = [[NSMutableDictionary alloc] init]; 
>  [midrollAdDictionary setObject:@"custom-val1" forKey:@"custom-key1"]; 
>  [midrollAdDictionary setObject:@"custom-val2" forKey:@"custom-key2"]; 
>    
>  // 7. Track the ADBMediaHeartbeatEventAdBreakStart event when the mid-roll pod  
>  //    starts to play. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakStart  
>                    mediaObject:adBreakObject  
>                    data:nil]; 
>  ....... 
>  ....... 
>    
>  // 8. Track the ADBMediaHeartbeatEventAdStart event when the mid-roll pod's  
>  //    ad starts to play. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdStart  
>                   mediaObject:adObject  
>                   data:midrollAdDictionary]; 
>  ....... 
>  ....... 
>    
>  // 9. Track the ADBMediaHeartbeatEventAdComplete event when the ad reaches  
>  //    the end, i.e., when it completes and finishes playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdComplete  
>                   mediaObject:nil  
>                   data:nil]; 
>  ....... 
>  ....... 
>    
>  // 10. Track the ADBMediaHeartbeatEventAdBreakComplete event when all the  
>  //     ads in the mid-roll pod finish playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakComplete  
>                   mediaObject:nil  
>                   data:nil]; 
>  ....... 
>  ....... 
>    
>  // Post-roll 
>  ADBMediaObject *postrollBreakInfo =  
>    [ADBMediaHeartbeat createAdBreakObjectWithName:POSTROLL_BREAK_NAME  
>                       position:POSTROLL_BREAK_POSITION  
>                       startTime:POSTROLL_BREAK_START_TIME]; 
>  ADBMediaObject *adInfo =  
>    [ADBMediaHeartbeat createAdObjectWithName:POSTROLL_AD_NAME  
>                       adId:POSTROLL_AD_ID  
>                       position:POSTROLL_AD_POSITION  
>                       length:POSTROLL_AD_LENGTH]; 
>    
>  // Context ad data 
>  NSMutableDictionary *postrollAdDictionary =  
>    [[NSMutableDictionary alloc] init]; 
>  [postrollAdDictionary setObject:@"custom-val1" forKey:@"custom-key1"]; 
>  [postrollAdDictionary setObject:@"custom-val2" forKey:@"custom-key2"]; 
>    
>  // 11. Track the ADBMediaHeartbeatEventAdBreakStart event when the  
>  //     post-roll pod starts to play. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakStart  
>                   mediaObject:adBreakObject  
>                   data:nil]; 
>  ....... 
>  ....... 
>    
>  // 12. Track the ADBMediaHeartbeatEventAdStart event when the  
>  //     post-roll pod's ad starts to play. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdStart  
>                   mediaObject:adObject  
>                   data:postrollAdDictionary]; 
>  ....... 
>  ....... 
>    
>  // 13. Track the ADBMediaHeartbeatEventAdComplete event when the  
>  //     post-roll pod's ad finishes playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdComplete  
>                   mediaObject:nil  
>                   data:nil]; 
>  ....... 
>  ....... 
>    
>  // 14. Track the ADBMediaHeartbeatEventAdBreakComplete event when  
>  //     all the ads in the post-roll pod finish playing. 
>  [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventAdBreakComplete  
>                   mediaObject:nil data:nil]; 
>  ....... 
>  ....... 
>    
>  // 15. Call trackComplete when the playback reaches the end,  
>  //     i.e., when the video completes and finishes playing. 
>  [_mediaHeartbeat trackComplete]; 
>  ....... 
>  ....... 
>    
>  // 16. Call trackSessionEnd when the playback session is over. This method  
>  //     must be called even if the user does not watch the video to completion. 
>  [_mediaHeartbeat trackSessionEnd]; 
>  ....... 
>  ....... 
>  
>  ```


>* **JavaScript - **To view this scenario in JavaScript, enter the following text: >
>  ```
>  js>  // Set up mediaObject 
>  MediaObject mediaInfo = MediaHeartbeat.createMediaObject( 
>      Configuration.VIDEO_NAME,  
>      Configuration.VIDEO_ID,  
>      Configuration.VIDEO_LENGTH,  
>      MediaHeartbeat.StreamType.VOD 
>  ); 
>   
>  var videoMetadata = { 
>      CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>      CUSTOM_KEY_2 : CUSTOM_VAL_2,  
>      CUSTOM_KEY_3 : CUSTOM_VAL_ 
>  }; 
>   
>  // 1. Call trackSessionStart() when Play is clicked or if autoplay is used,  
>  //    i.e., when there's an intent to start playback.  
>  this._mediaHeartbeat.trackSessionStart(mediaInfo, videoMetadata); 
>   
>  ...... 
>  ...... 
>   
>  // Preroll 
>  var adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(ADBREAK_NAME,  
>                                       ADBREAK_POSITION,  
>                                       ADBREAK_START_TIME); 
>  var adInfo =  
>    MediaHeartbeat.createAdObject(AD_NAME,  
>                                  AD_ID,  
>                                  AD_POSITION,  
>                                  AD_LENGTH); 
>   
>  // Custom ad metadata 
>  var adMetadata = { 
>      CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>      CUSTOM_KEY_2 : CUSTOM_VAL_2 
>   
>  }; 
>   
>  // 2. Track the MediaHeartbeat.Event.AdBreakStart event when the preroll pod  
>  //    starts to play. Note that since this is a preroll, you must track the  
>  //    MediaHeartbeat.Event.AdBreakStart event before you call trackPlay().  
>  this._trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo, null); 
>   
>  ....... 
>  ....... 
>   
>  // 3. Track the MediaHeartbeat.Event.AdStart event when the preroll pod's ad  
>  //    starts to play. Note that since this is a preroll, you must track the 
>  //    MediaHeartbeat.Event.AdStart event before you call trackPlay().  
>  this._heartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 4. Call trackPlay() when the main content actually starts, i.e., when the  
>  //    first frame of the video content is rendered on the screen.  
>  this._mediaHeartbeat.trackPlay(); 
>   
>  ....... 
>  ....... 
>   
>  // 5. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches the end,  
>  //    i.e., when the ad completes and finishes playing. 
>  this._heartbeat.trackEvent(MediaHeartbeat.Event.AdComplete, null, null); 
>   
>  ....... 
>  ....... 
>   
>  // 6. Track the MediaHeartbeat.Event.AdBreakComplete event when all of the ads in  
>  //    the pod finish playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete); 
>   
>  ....... 
>  ....... 
>   
>  // Midroll 
>  var adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(MIDROLL_BREAK_NAME,  
>                                       MIDROLL_BREAK_POSITION,  
>                                       MIDROLL_BREAK_START_TIME); 
>  var adInfo =  
>    MediaHeartbeat.createAdObject(MIDROLL_AD_NAME,  
>                                  MIDROLL_AD_ID, 
>                                  MIDROLL_AD_POSITION,  
>                                  MIDROLL_AD_LENGTH); 
>   
>  // Custom ad metadata 
>  var adMetadata = { 
>      CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>      CUSTOM_KEY_2 : CUSTOM_VAL_2 
>   
>  }; 
>   
>  // 7. Track the MediaHeartbeat.Event.AdBreakStart event when the  
>  //    midroll pod starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo); 
>   
>  ....... 
>  ....... 
>   
>  // 8. Track the MediaHeartbeat.Event.AdStart event when the midroll  
>  //    pod's ad starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart,  
>                                  adInfo,  
>                                  adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 9. Track the MediaHeartbeat.Event.AdComplete event when the ad  
>  //    reaches the end, i.e., when the ad completes and finishes playing.  
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete); 
>   
>  ....... 
>  ....... 
>   
>  // 10. Track the MediaHeartbeat.Event.AdBreakComplete event when all of  
>  //     the ads in the midroll pod finish playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete); 
>   
>  ....... 
>  ....... 
>   
>  // Set up mediaObject 
>  var mediaInfo = MediaHeartbeat.createMediaObject( 
>      Configuration.VIDEO_NAME,  
>      Configuration.VIDEO_ID,  
>      Configuration.VIDEO_LENGTH,  
>      MediaHeartbeat.StreamType.VOD 
>   
>  ); 
>   
>  var videoMetadata = { 
>      CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>      CUSTOM_KEY_2 : CUSTOM_VAL_2,  
>      CUSTOM_KEY_3 : CUSTOM_VAL_3 
>   
>  }; 
>   
>  // 1. Call trackSessionStart() when Play is clicked or if autoplay  
>  //    is used, i.e., when there's an intent to start playback. 
>  this._mediaHeartbeat.trackSessionStart(mediaInfo, videoMetadata); 
>   
>  ...... 
>  ...... 
>   
>  // Preroll 
>  var adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(ADBREAK_NAME,  
>                                       ADBREAK_POSITION,  
>                                       ADBREAK_START_TIME); 
>  var adInfo =  
>    MediaHeartbeat.createAdObject(AD_NAME,  
>                                  AD_ID,  
>                                  AD_POSITION,  
>                                  AD_LENGTH); 
>   
>  // Custom ad metadata 
>  var adMetadata = { 
>     CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>     CUSTOM_KEY_2 : CUSTOM_VAL_2 
>   
>  }; 
>   
>  // 2. Track the MediaHeartbeat.Event.AdBreakStart event when the preroll pod  
>  //    starts to play. Note that since this is a preroll, you must track the   
>  //    MediaHeartbeat.Event.AdBreakStart event before you call trackPlay(). 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo); 
>   
>  ....... 
>  ....... 
>   
>  // 3. Track the MediaHeartbeat.Event.AdStart event when the preroll pod's  
>  //    ad starts to play. Note that since this is a preroll, you must track   
>  //    the MediaHeartbeat.Event.AdStart event before you call trackPlay(). 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 4. Call trackPlay() when the playback actually starts, i.e., when the first  
>  //    frame of the main content is rendered on the screen.  
>  _mediaHeartbeat.trackPlay(); 
>   
>  ....... 
>  ....... 
>   
>  // 5. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches  
>  //    the end, i.e., when the ad completes and finishes playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete); 
>   
>  ....... 
>  ....... 
>   
>  // 6. Track the MediaHeartbeat.Event.AdBreakComplete event when all  
>  //    of the ads in the pod finish playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete); 
>   
>  ....... 
>  ....... 
>   
>  // Mid-roll 
>  var adBreakInfo =  
>    MediaHeartbeat.createAdBreakObject(MIDROLL_BREAK_NAME, 
>                                       MIDROLL_BREAK_POSITION,  
>                                       MIDROLL_BREAK_START_TIME); 
>  var adInfo =  
>    MediaHeartbeat.createAdObject(MIDROLL_AD_NAME,  
>                                  MIDROLL_AD_ID,  
>                                  MIDROLL_AD_POSITION,  
>                                  MIDROLL_AD_LENGTH); 
>   
>  // Custom ad metadata 
>  var adMetadata = { 
>     CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>     CUSTOM_KEY_2 : CUSTOM_VAL_2 
>   
>  }; 
>   
>  // 7. Track the MediaHeartbeat.Event.AdBreakStart event when the midroll  
>  //    pod starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo); 
>   
>  ....... 
>  ....... 
>   
>  // 8. Track the MediaHeartbeat.Event.AdStart event when the midroll pod's  
>  //    ad starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 9. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches  
>  //    the end, i.e., when the ad completes and finishes playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete); 
>   
>  ....... 
>  ....... 
>   
>  // 10. Track the MediaHeartbeat.Event.AdBreakComplete event when all  
>  //     of the ads in the midroll pod finish playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete); 
>   
>  ....... 
>  ....... 
>   
>  // Postroll 
>  var adBreakInfo = MediaHeartbeat.createAdBreakObject(POSTROLL_BREAK_NAME,  
>  POSTROLL_BREAK_POSITION, POSTROLL_BREAK_START_TIME); 
>  var adInfo = MediaHeartbeat.createAdObject(POSTROLL_AD_NAME, POSTROLL_AD_ID,  
>  POSTROLL_AD_POSITION, POSTROLL_AD_LENGTH); 
>   
>  // Custom ad metadata 
>  var adMetadata = { 
>     CUSTOM_KEY_1 : CUSTOM_VAL_1,  
>     CUSTOM_KEY_2 : CUSTOM_VAL_2 
>   
>  }; 
>   
>  // 11. Track the MediaHeartbeat.Event.AdBreakStart event when the postroll  
>  //     pod starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakInfo); 
>   
>  ....... 
>  ....... 
>   
>  // 12. Track the MediaHeartbeat.Event.AdStart event when the postroll pod's ad  
>  //     starts to play. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adInfo, adMetadata); 
>   
>  ....... 
>  ....... 
>   
>  // 13. Track the MediaHeartbeat.Event.AdComplete event when the ad reaches   
>  //     the end, i.e., when the ad completes and finishes playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete); 
>   
>  ....... 
>  ....... 
>   
>  // 14. Track the MediaHeartbeat.Event.AdBreakComplete event when all of  
>  //     the ads in the postroll pod finish playing. 
>  this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete); 
>   
>  ....... 
>  ....... 
>   
>  // 15. Call trackComplete() when the playback reaches the end, i.e., when playback 
>  //     completes and finishes playing. 
>  this._mediaHeartbeat.trackComplete(); 
>   
>  ........ 
>  ........ 
>   
>  // 16. Call trackSessionEnd() when the playback session is over. This method must be called  
>  //     even if the user does 
>  not watch the video to completion. 
>  this._mediaHeartbeat.trackSessionEnd(); 
>   
>  ........ 
>  ........ 
>  
>  ```



