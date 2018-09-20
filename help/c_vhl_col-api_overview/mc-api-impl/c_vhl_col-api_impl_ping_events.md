---
description: null
seo-description: null
seo-title: Sending Ping Events
title: Sending Ping Events
uuid: 3b6dc645-d3a2-4adc-abc6-120157dd4fd6
index: y
internal: n
snippet: y
translate: y
---

# Sending Ping Events


<a id="section_sml_4cy_lcb"></a>

***For main content, you must fire ping events every 10 seconds*, beginning after 10 seconds of playback, regardless of other API events that you have sent. For Ad tracking, you must fire ping events every 1 second - **This is literally the "heartbeat" of Video Analytics. The only required parameters for a ping call are ` eventType: ping` along with the ` playerTime` object (playhead position and timestamp). The following code snippet shows one way to implement a timed pinging mechanism for main content (10 second interval): 
```
js... 
Pinger.init(10000); 
... 
Pinger.kill(); 
 
 
var Pinger = { 
    init: function(interval) { 
        this._timer = window.setInterval(function() { 
                $.event.trigger({type: "onPing", _data: ""}); 
            }, interval); 
    }, 
     
    kill: function() { 
        window.clearInterval(this._timer); 
    } 
}
```

