---
description: null
seo-description: null
seo-title: Prerequisites
title: Prerequisites
uuid: dc0c00e5-796b-4e64-8fc8-5641287e026a
index: y
internal: n
snippet: y
translate: y
---

# Prerequisites

Before you begin your video tracking implementation, you have some early decisions to make, regarding which implementation makes the most sense for your situation:
* **Video Analytics - **Using the latest VHL SDKs (the standard, recommended implementation) and/or the Media Collection (RESTful) API
* **Milestone - **The older Adobe tracking implementation
* **Data Insertion APIs - **Implementing video tracking without using VHL SDKs, ith .


For *Video Analytics*, here are the tasks you must complete prior to implementing: 


1. **Enable Experience Cloud. **As part of the requirements to implement the Video Heartbeat SDK, you need to implement the Experience Cloud ID Service (formerly known as Visitor ID Service). 

   The Experience Cloud ID service enables the common identification framework for the Experience Cloud Core Services, solutions, and customer attributes and audiences in the People core service. It works by assigning a unique, persistent ID to a site visitor. When your organization implements the ID service, this ID lets you identify the same site visitor and their data in different Experience Cloud solutions. 

   <a id="fig_E7648D1E230E4AA588C80C9092B662EA"></a> ![](assets/mc_id_service_graphic.png) 

   The ID service can also replace the different solution-specific IDs (for example, Analytics AID). Through the [ Customer IDs and Authentication States](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-authenticated-state.html) functionality, the ID service lets you pass in your own customer IDs to the Experience Cloud. Keep in mind, however, that the ID service only works with the solutions to which you have already subscribed. If you are not signed up for access to other products, the ID service does not provide the access. 

   Going forward, the ID service is an integral component of many current and future Experience Cloud features, enhancements, and services. Currently, the ID service supports [ Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [ Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), and [ Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). 

   >[!IMPORTANT]
   >
   >To participate in the Adobe Experience Cloud Device Co-op, the Experience Cloud ID service is required.
   If you have not implemented the ID service, now is the time to start considering a migration strategy. For more information about the importance and role of the ID service, see [ Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/). 

   >[!IMPORTANT]
   >
   >In the absence of any user ID information present on the video specific calls the default analytics[ Fallback ID Methods](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html) will apply. 
   For additional information about the Experience Cloud ID, see [ Experience Cloud ID Overview](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-overview.html), and [ Experience Cloud ID Service](https://marketing.adobe.com/resources/help/en_US/mcvid/). 

1. **Enable Adobe Analytics Reports. **To enable video reports in Analytics and see the video and video ad data you are collecting, see [](../video-reports/c_vhl_vid-rept_enable.md). 


