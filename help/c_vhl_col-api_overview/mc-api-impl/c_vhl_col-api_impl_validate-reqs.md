---
description: null
seo-description: null
seo-title: Validating Event Requests
title: Validating Event Requests
uuid: 5ad76e13-5658-446b-9acd-c7c9dc24f25f
index: y
internal: n
snippet: y
translate: y
---

# Validating Event Requests


<a id="section_cpy_3xc_mcb"></a>

The JSON request body for each event type is validated on the backend with JSON schemas. The HTTP response body is populated with an error message when validation fails for an API call. 

JSON validation schemas for each event type are publicly accessible here: ` {uri}/api/v1/schemas/{eventType}`, e.g., ` {uri}/api/v1/schemas/sessionEnd`. These JSON validation schemas are the absolute authority for determining the current and correct request body parameters and their data types for each type of event.

For example, the response to a request for the ` sessionStart` validation schema appears something like this sample (slightly formatted for readability here): 
```
HTTP/1.1 200 OK
Server: nginx/1.13.5
Date: Thu, 18 Jan 2018 15:44:50 GMT
Content-Type: application/json
Content-Length: 2716
Connection: keep-alive

{"$schema":"http://json-schema.org/draft-04/schema#",
"id":"http://alpha.hb-api.omtrdc.net/api/v1/schemas/sessionStart",
"definitions":{"playerTime":{"type":"object","properties":
{"playhead":{"type":"number"},"ts":{"type":"integer"}},
"required":["playhead","ts"],"additionalProperties":false},
"eventType":{"type":"string","enum":["sessionStart",
                                     "play",
                                     "ping",
                                     "bufferStart",
                                     "pauseStart",
                                     "sessionComplete",
                                     "bitrateChange",
                                     "error",
                                     "adBreakStart",
                                     "adBreakComplete",
                                     "adStart",
                                     "adComplete",
                                     "adSkip",
                                     "sessionEnd"]},
"qoeData":{"type":"object","properties":{"media.qoe.bitrate":{"type":"integer"},
                                         "media.qoe.droppedFrames":{"type":"integer"},
                                         "media.qoe.framesPerSecond":{"type":"integer"},
                                         "media.qoe.timeToStart":{"type":"integer"}},"required":[],
                                         "additionalProperties":false},
"customMetadata":{"type":"object","patternProperties":{"^[a-zA-Z0-9_\\.]+$":{"type":"string"}},
"additionalProperties":false},
"sessionStart":{"properties":{"eventType":{"type":"string","enum":["sessionStart"]},
                              "playerTime":{"$ref":"#/definitions/playerTime"},
                              "params":{"type":"object","properties":{"appInstallationId":{"type":"string"},
                                                                      "analytics.trackingServer":{"type":"string"},
                                                                      "analytics.reportSuite":{"type":"string"},
                                                                      <...>
                                                                      "visitor.marketingCloudOrgId"],
                              "additionalProperties":false},
"customMetadata":{"$ref":"#/definitions/customMetadata"},
"qoeData":{"$ref":"#/definitions/qoeData"}},
"required":["eventType","playerTime","params"],"additionalProperties":false}},
"type":"object","$ref":"#/definitions/sessionStart"}
```


>[!NOTE]
>
>Session level validation is not possible, as the session context is not available in the collection layer.

