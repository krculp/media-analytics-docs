---
description: null
seo-description: null
seo-title: Track App Actions (OTT apps)
title: Track App Actions (OTT apps)
uuid: 19baa913-5888-46b3-af37-147d42588c10
index: y
internal: n
snippet: y
translate: y
---

# Track App Actions (OTT apps)

Actions are the events that occur in your app that you want to measure. 

Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might send a ` trackAction` call for each new subscription, each time a content is rated, or each time a level is completed. Actions are not tracked automatically, so call ` trackAction` when an event that you want to track occurs, and map the action to a custom event. 


1. When an event you want to track occurs, call ` trackAction`. 
    * 
      ```
      ADBMobile().trackAction("myapp.ActionName", {})
      ```

    * 
      ```
      js      ADBMobile.analytics.trackAction("myapp.ActionName", {});
      ```


1. Map the action to a custom event. 
    * 
      ```
      dictionary = {} 
      dictionary["myapp.social.SocialSource"] = "Twitter"  
      ADBMobile().trackAction("myapp.SocialShare", dictionary)
      ```

    * 
      ```
      js      var dictionary = {}; 
      dictionary["myapp.social.SocialSource"] = "Twitter"; 
      ADBMobile.analytics.trackAction("myapp.SocialShare", dictionary);
      ```

   You can also send additional context data with each track action call. 


