# Video Analytics 2.x Cookbook

## Handling application interrupts during playback

Playback in a video application can be interrupted in a variety of ways: a
user explicitly presses pause, or when a user puts the application into the
background. Regardless of what causes an interruption in video playback, the
tracking instructions are the same:

1. Call **trackPause** when the application is interrupted (goes to background, video pauses, etc.). 
2. Call **trackPlay** when the application returns to the foreground and/or the video resumes playing.

**Note:** The Media Analytics team has seen instances where customers called 
`trackSessionStart` when their app returned from the background. Doing this 
results in the playback up to that point not counting towards the total playback 
time, along with losing earlier progress markers, segments, and so on. Instead, 
call `trackPlay` when the app returns and/or the video resumes playing.

## FAQ about handling application interrupts:

* _How long should an app be backgrounded before the session closes?_

  If the application allows background playback, it can continue tracking by calling 
  our APIs and we will send all our regular tracking pings. I have not seen any video 
  app allow background playback except youtube red, however, all audio apps allow this. 
  If the application does not allow background playback, then it is advisable to stay 
  in pause state for 1 minute and then end the tracking session. The application can 
  not continue sending pause pings as in most cases it cannot determine if the user 
  is going to return back to continue viewing the video or when it is going to be 
  killed. It is also a bad experience to keep sending pings when in the background.

* _What is the correct way to handle re-starting tracking after the app has been in
  the background for a long time?_

  The application should call `trackSessionEnd` to end the tracking session. From 
  Version 2.1, the SDK sends an "end" ping to notify the back-end that the tracking 
  session is closed. 

  For detailed instructions on restarting a tracking session, see this page: [Manually resume a previously closed session](../../va_sdks/js-sdk/manually-resume-session.md)
  The SDK sends a resume ping to notify the back-end that the user is manually 
  resuming the session.
